    
The following code verifys the user log in credentials and verifies that it matches the database record before allowing the user to move move forward.
The test is to compare the data for the Admin in the ADMIN table in the database, input those values,and ensure successful log in. 

	private void LoginBtnMouseClicked(java.awt.event.MouseEvent evt) {                                      
        if (UserIDTF.getText().isEmpty() || PasswordTF.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "Missing Information");
        } else {
            String Query = "select * from ADMINTBL where ADMINNAME='" + UserIDTF.getText() + "' and ADMINPASSWORD= '" + PasswordTF.getText() + "'";
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
                St = Con.createStatement();
                Rs = St.executeQuery(Query);
                if (Rs.next()) {
                    new HomeForm().setVisible(true);
                    this.dispose();
                } else {
                    JOptionPane.showMessageDialog(this, "Incorrect Login Credentials");
                }

            } catch (Exception e) {

                //e.printStackTrace();
            }

        }
    }

The following code is used when a new CATEGORY is being added to the CATEGORY table in the database. To verify this is successful one can 
input the values in the CATEGORY form and click Add, then compare the data in the CATEGORY table. 

    private void AddBtnMouseClicked(java.awt.event.MouseEvent evt) {                                    
        try {
            Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
            PreparedStatement add = Con.prepareStatement("insert into CATEGORYTBL values(?,?)");
            add.setInt(1, Integer.valueOf(CategoryID.getText()));
            add.setString(2, CategoryName.getText());
            int row = add.executeUpdate();
            JOptionPane.showMessageDialog(this, "Category Successfully Added");
            Con.close();
            SelectCategory();

        } catch (java.sql.SQLException ex) {
            Logger.getLogger(Category.class.getName()).log(Level.SEVERE, null, ex);
            ex.printStackTrace();
        }
    }        

The following code is used when a existing CATEGORY is being edited to the CATEGORY table in the database. To verify this is successful one can 
input the values in the CATEGORY form and click Add, then compare the data in the CATEGORY table.

    private void EditBtnMouseClicked(java.awt.event.MouseEvent evt) {                                     
        if (CategoryID.getText().isEmpty() || CategoryName.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "No Editable Information");
        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");

                String UpdateQuery = "update CATEGORYTBL set CATEGORYNAME = '" + CategoryName.getText() + "'" + "where CATEGORYID=" + CategoryID.getText();

                Statement Add = Con.createStatement();
                Add.executeUpdate(UpdateQuery);
                JOptionPane.showMessageDialog(this, "Category Edit Successful");
                SelectCategory();

            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }    

The following code is used when a new CATEGORY is being deleted from the CATEGORY table in the database. To verify this is successful one can 
input the values in the CATEGORY form and click Add, then compare the data in the CATEGORY table.

    private void DeleteBtnMouseClicked(java.awt.event.MouseEvent evt) {                                       
        if (CategoryID.getText().isEmpty()) {

            JOptionPane.showMessageDialog(this, "Enter the Category to be Deleted");

        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
                String ID = CategoryID.getText();
                String Query = "Delete from CATEGORYTBL where CATEGORYID=" + ID;
                Statement Add = Con.createStatement();
                Add.executeUpdate(Query);
                SelectCategory();
                JOptionPane.showMessageDialog(this, "Category Deleted Successfully");
            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }      

The following code is used when a new CUSTOMER is being added to the CUSTOMER table in the database. To verify this is successful one can 
input the values in the CUSTOMER form and click Add, then compare the data in the CUSTOMER table. 

    private void AddBtnMouseClicked(java.awt.event.MouseEvent evt) {                                    
        try {
            Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
            PreparedStatement add = Con.prepareStatement("insert into CUSTOMERTBL values(?,?,?)");
            add.setInt(1, Integer.valueOf(CustomerID.getText()));
            add.setString(2, CustomerName.getText());
            add.setString(3, CustomerPhone.getText());
            int row = add.executeUpdate();
            JOptionPane.showMessageDialog(this, "Customer Successfully Added");
            Con.close();
            SelectCustomer();

        } catch (java.sql.SQLException ex) {
            Logger.getLogger(Customer.class.getName()).log(Level.SEVERE, null, ex);
            ex.printStackTrace();
        }
    }       

The following code is used when a existing CUSTOMER is being edited to the CUSTOMER table in the database. To verify this is successful one can 
input the values in the CUSTOMER form and click Add, then compare the data in the CUSTOMER table.

    private void EditBtnMouseClicked(java.awt.event.MouseEvent evt) {                                     
        if (CustomerID.getText().isEmpty() || CustomerName.getText().isEmpty() || CustomerPhone.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "No Editable Information");
        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");

                String UpdateQuery = "update CUSTOMERTBL set CUSTOMERNAME = '" + CustomerName.getText() + "'" + ",CUSTOMERPHONE='"
                        + CustomerPhone.getText() + "'" + "where CUSTOMERID=" + CustomerID.getText();

                Statement Add = Con.createStatement();
                Add.executeUpdate(UpdateQuery);
                JOptionPane.showMessageDialog(this, "Customer Edit Successful");
                SelectCustomer();

            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }     


The following code is used when a existing CUSTOMER is being deleted from the CUSTOMER table in the database. To verify this is successful one can 
input the values in the CUSTOMER form and click Add, then compare the data in the CUSTOMER table.

    private void DeleteBtnMouseClicked(java.awt.event.MouseEvent evt) {                                       
        if (CustomerID.getText().isEmpty()) {

            JOptionPane.showMessageDialog(this, "Enter the Customer to be Deleted");

        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
                String ID = CustomerID.getText();
                String Query = "Delete from CUSTOMERTBL where CUSTOMERID=" + ID;
                Statement Add = Con.createStatement();
                Add.executeUpdate(Query);
                SelectCustomer();
                JOptionPane.showMessageDialog(this, "Customer Deleted Successfully");
            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }         

The following code is used when a new PRODUCT is being added to the PRODUCT table in the database. To verify this is successful one can 
input the values in the PRODUCT form and click Add, then compare the data in the PRODUCT table. 

    private void AddbtnMouseClicked(java.awt.event.MouseEvent evt) {                                    
        // TODO add your handling code here:
        try {
            Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
            PreparedStatement add = Con.prepareStatement("insert into PRODUCTTBL values(?,?,?,?,?)");
            add.setInt(1, Integer.valueOf(ProductID.getText()));
            add.setString(2, ProdName.getText());
            add.setInt(3, Integer.valueOf(ProdQty.getText()));
            add.setString(4, ProdDescription.getText());
            add.setString(5, CatCb.getSelectedItem().toString());
            int row = add.executeUpdate();
            JOptionPane.showMessageDialog(this, "Product Successfully Added");
            Con.close();
            SelectProd();

        } catch (java.sql.SQLException ex) {
            Logger.getLogger(Products.class.getName()).log(Level.SEVERE, null, ex);
            ex.printStackTrace();
        }
    }  

The following code is used when a existing PRODUCT is being edited to the PRODUCT table in the database. To verify this is successful one can 
input the values in the PRODUCT form and click Add, then compare the data in the PRODUCT table.

    private void EditBtnMouseClicked(java.awt.event.MouseEvent evt) {                                     
        if (ProductID.getText().isEmpty() || ProdName.getText().isEmpty() || ProdQty.getText().isEmpty() || ProdDescription.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "No Editable Information");
        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");

                String UpdateQuery = "update PRODUCTTBL set PRODNAME = '" + ProdName.getText() + "'" + ",PRODQTY= " + ProdQty.getText() + "" + ",PRODDESCRIPTION='"
                        + ProdDescription.getText() + "'" + ",PRODCATEGORY='" + CatCb.getSelectedItem().toString() + "'" + "where PRODUCTID=" + ProductID.getText();

                Statement Add = Con.createStatement();
                Add.executeUpdate(UpdateQuery);
                JOptionPane.showMessageDialog(this, "Product Edit Successful");
                SelectProd();

            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }      

The following code is used when a existing PRODUCT is being deleted from the PRODUCT table in the database. To verify this is successful one can 
input the values in the PRODUCT form and click Add, then compare the data in the PRODUCT table.

    private void DeleteBtnMouseClicked(java.awt.event.MouseEvent evt) {                                       
        if (ProductID.getText().isEmpty()) {

            JOptionPane.showMessageDialog(this, "Enter the Product to be Deleted");

        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
                String ID = ProductID.getText();
                String Query = "Delete from PRODUCTTBL where PRODUCTID=" + ID;
                Statement Add = Con.createStatement();
                Add.executeUpdate(Query);
                SelectProd();
                JOptionPane.showMessageDialog(this, "Product Deleted Successfully");
            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }    

The following code is used when a new ORDER is being added to the ORDER table in the database. To verify this is successful one can 
input the values in the ORDER form and click Add, then compare the data in the ORDER table.

    private void AddOrderbtnMouseClicked(java.awt.event.MouseEvent evt) {                                         
        if(OrderIdTB.getText().isEmpty())  {
            
            JOptionPane.showMessageDialog(this, "Enter the Order ID.");
            
        } else {
        try {
            Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
            PreparedStatement add = Con.prepareStatement("insert into ORDERTBL values(?,?,?,?)");
            add.setInt(1, Integer.valueOf(OrderIdTB.getText()));
            add.setString(2, CustNameLbl.getText());
            add.setString(3, DateLbl.getText());
            add.setInt(4, Integer.valueOf(TotalAmountLbl.getText()));
         
            int row = add.executeUpdate();
            JOptionPane.showMessageDialog(this, "Order Successfully Added");
            Con.close();
            

        } catch (java.sql.SQLException ex) {
            Logger.getLogger(Products.class.getName()).log(Level.SEVERE, null, ex);
            ex.printStackTrace();
        }
        }
    }    

The following code is used when a new PRODUCT is being added to the ORDER. To verify this is successful one can 
input the values in the ORDER form and click Add To, then compare the data in the ORDER table.

    private void AddtoBtnMouseClicked(java.awt.event.MouseEvent evt) {                                      
        if(flag == 0 || QtyTB.getText().isEmpty() || PriceTB.getText().isEmpty()) {
            
            JOptionPane.showMessageDialog(this, "Select a Product, and Enter the Price and Qty.");
            
        } else {
        Uprice = Integer.valueOf(PriceTB.getText());
        total = Uprice * Integer.valueOf(QtyTB.getText());
        Vector v = new Vector();
        v.add(i);
        v.add(ProdName);
        v.add(QtyTB.getText());
        v.add(Uprice);
        v.add(total);
        DefaultTableModel dt = (DefaultTableModel) BillTbl.getModel();
        dt.addRow(v);
        tot = tot + total;
        TotalAmountLbl.setText(""+tot);
        update();
        i++;
        }
    }            



The following code is used when a new USER is being added to the USER table in the database. To verify this is successful one can 
input the values in the USER form and click Add, then compare the data in the USER table.

    private void AddBtnMouseClicked(java.awt.event.MouseEvent evt) {                                    
        try {
            Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
            PreparedStatement add = Con.prepareStatement("insert into USERTBL values(?,?,?)");
            add.setString(1, UserName.getText());
            add.setString(2, UserPassword.getText());
            add.setString(3, UserPhone.getText());
            int row = add.executeUpdate();
            JOptionPane.showMessageDialog(this, "User Successfully Added");
            Con.close();
            SelectUser();

        } catch (java.sql.SQLException ex) {
            Logger.getLogger(User.class.getName()).log(Level.SEVERE, null, ex);
            ex.printStackTrace();
        }
    }    

The following code is used when a existing USER is being edited to the USER table in the database. To verify this is successful one can 
input the values in the USER form and click Add, then compare the data in the USER table.

    private void EditBtnMouseClicked(java.awt.event.MouseEvent evt) {                                     
        if (UserName.getText().isEmpty() || UserPassword.getText().isEmpty() || UserPhone.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "No Editable Information");
        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");

                String UpdateQuery = "update USERTBL set USERNAME ='" + UserName.getText() + "'" + ",USERPASSWORD='" + UserPassword.getText() + "'" + "where USERPHONE =" + "'" + UserPhone.getText() + "'";

                Statement Add = Con.createStatement();
                Add.executeUpdate(UpdateQuery);
                JOptionPane.showMessageDialog(this, "User Edit Successful");
                SelectUser();

            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }     

The following code is used when a existing USER is being deleted from the USER table in the database. To verify this is successful one can 
input the values in the USER form and click Add, then compare the data in the USER table.

    private void DeleteBtnMouseClicked(java.awt.event.MouseEvent evt) {                                       
        if (UserPhone.getText().isEmpty()) {

            JOptionPane.showMessageDialog(this, "Select the User to be Deleted");

        } else {
            try {
                Con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mysql?zeroDateTimeBehavior=CONVERT_TO_NULL", "root", "admin");
                String ID = UserPhone.getText();
                String Query = "Delete from USERTBL where USERPHONE=" + "'" + ID + "'";
                Statement Add = Con.createStatement();
                Add.executeUpdate(Query);
                SelectUser();
                JOptionPane.showMessageDialog(this, "User Deleted Successfully");
            } catch (java.sql.SQLException e) {

                e.printStackTrace();

            }
        }
    }     

