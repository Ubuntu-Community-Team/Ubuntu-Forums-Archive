---
title: "[SOLVED] JTextFields not being displayed"
date: 2008-01-23
forum: Programming Talk
---

### Post by mike_g on 2008-01-23
I'm making a window. It has a variable size dependent on an amount of users. I'm using Netbeans, and its form designer generates some of the code. After the generated code runs my own code adds text fields and resizes the window. The problem is that none of my text fields are being displayed in the window. Am I missing something in my constructor to display them? Or could it be the generated code causing a problem?

```
package loginunit;
import java.awt.Dimension;
import javax.swing.JTextField;
import javax.swing.JPanel;

public class AccountManagementWindow extends javax.swing.JFrame 
{
    Users users;
    JTextField[] unames;
    JTextField[] pwords;
    
    /** Creates new form AccountManagementWindow */
    public AccountManagementWindow(Users u) 
    {
        users = u;
        unames = new JTextField[users.getList().size()];
        pwords = new JTextField[users.getList().size()];        
        
        initComponents();
        
        JPanel userPanel = new JPanel();
        
        for(int i=0; i<users.getList().size(); i++)
        {    
            unames[i] = new JTextField(users.getList().get(i).getName());
            getContentPane().add(unames[i]);
             
        }
        
        System.out.println("***"+users.getList().size()+ "***"); //Shows I have 3 users
        pack();
       
        setBounds(10, 10, 100, users.getList().size() * 60);    
        setVisible(true);
    }
    
    /** GENERATED CODE ***/
    // <editor-fold defaultstate="collapsed" desc=" Generated Code ">                          
    private void initComponents() {

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 394, Short.MAX_VALUE)
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 282, Short.MAX_VALUE)
        );
        pack();
    }// </editor-fold>                        

    
    // Variables declaration - do not modify                     
    // End of variables declaration                   
    
}
```
Cheers.

---

### Post by mike_g on 2008-01-23
Ok, I sorted it out. The generated code was getting in the way so I removed it, then there were a few things to fix with my code but thats all done now.

---

