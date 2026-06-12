---
title: "Form does not appear even after this.setVisible(true) [JAVA]"
date: 2012-11-29
forum: Programming Talk
---

### Post by vikkyhacks on 2012-11-29
Hello, I recently started GUI programming in Java with Swing. I am using NetBeans IDE and have attached my complete project with this thread. 

I have two classes.
Login -> Is the GUI part with all labels, buttons ... (Without main method)
Main  -> Having main method.

```

/*   Main.java   */
package main;

public class Main {

    public static void main(String[] args) throws Exception {
        Login win = new Login();
        win.setVisible(true);
    }
}


```

```

package main;

import javax.swing.UIManager;

public class Login extends javax.swing.JPanel {

    public Login() throws Exception
    {
        UIManager.setLookAndFeel("com.seaglasslookandfeel.SeaGlassLookAndFeel");
        initComponents();
    }   
    
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        jLabel1 = new javax.swing.JLabel();
        jLabel2 = new javax.swing.JLabel();
        jLabel3 = new javax.swing.JLabel();
        cUser = new javax.swing.JTextField();
        cPass = new javax.swing.JTextField();
        cLogin = new javax.swing.JButton();
        cOut = new javax.swing.JLabel();

        jLabel1.setFont(new java.awt.Font("Ubuntu", 1, 16)); // NOI18N
        jLabel1.setText("Login Window");

        jLabel2.setText("Username");

        jLabel3.setText("Password");

        cUser.setName("");

        cLogin.setLabel("Login");
        cLogin.addMouseListener(new java.awt.event.MouseAdapter() {
            public void mouseClicked(java.awt.event.MouseEvent evt) {
                cLoginMouseClicked(evt);
            }
        });

        cOut.setForeground(new java.awt.Color(255, 0, 0));

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(this);
        this.setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                .addContainerGap(27, Short.MAX_VALUE)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                        .addGap(83, 83, 83)
                        .addComponent(cLogin, javax.swing.GroupLayout.PREFERRED_SIZE, 64, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addGap(81, 81, 81))
                    .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                        .addGap(59, 59, 59)
                        .addComponent(jLabel1)
                        .addGap(66, 66, 66))
                    .addGroup(layout.createSequentialGroup()
                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addComponent(jLabel2)
                            .addComponent(jLabel3))
                        .addGap(52, 52, 52)
                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addComponent(cOut)
                            .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING, false)
                                .addComponent(cUser)
                                .addComponent(cPass, javax.swing.GroupLayout.PREFERRED_SIZE, 115, javax.swing.GroupLayout.PREFERRED_SIZE)))))
                .addGap(20, 20, 20))
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addComponent(jLabel1)
                .addGap(18, 18, 18)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(jLabel2)
                    .addComponent(cUser, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(18, 18, 18)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(jLabel3)
                    .addComponent(cPass, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addComponent(cOut)
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addComponent(cLogin, javax.swing.GroupLayout.PREFERRED_SIZE, 34, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(0, 28, Short.MAX_VALUE))
        );
    }// </editor-fold>                        

    private void cLoginMouseClicked(java.awt.event.MouseEvent evt) {                                    
        String password = cPass.getText();
        String username = cUser.getText();
        if("pass".equals(password) && "admin".equals(username))
            cOut.setText("Logged In");
        else
            cOut.setText("Invalid Login");
    }                                   

    // Variables declaration - do not modify                     
    private javax.swing.JButton cLogin;
    private javax.swing.JLabel cOut;
    private javax.swing.JTextField cPass;
    private javax.swing.JTextField cUser;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    // End of variables declaration                   
}

```

---

### Post by PaulM1985 on 2012-11-29
Your Login class is a JPanel, which is not a window.  You want a window to be displayed.  So you either need to change your Login class to inherit from JFrame, so that it is a window that can be displayed, or create a JFrame and put the Login JPanel in it.

From looking at your post it looks like you are using a designer to set up your Login class, so I would suggest creating a JFrame and adding your panel to it.

```

Login login = new ........

JFrame frame = new JFrame();
frame.setSize(300, 300); // Set the size of the window
frame.add(login);
frame.setVisible(true);

```

Paul

---

### Post by spjackson on 2012-11-29
The problem is that the way you have written Main.main, Swing doesn't start to run. You need to do it like [this]("http://docs.oracle.com/javase/tutorial/uiswing/examples/start/HelloWorldSwingProject/src/start/HelloWorldSwing.java").

---

### Post by slickymaster on 2012-11-29
Another problem you have with your code is that you setting the look and feel of your form with the SeaGlassLookAndFeel but you are not importing it to your project. You have to add the SeaGlassLookAndFeel jar's to your project libraries.

---

### Post by vikkyhacks on 2012-11-29
how noob i am ... Thanks a LOT !!!!

---

### Post by vikkyhacks on 2012-11-29
> **slickymaster said:**
> not importing it to your project

I added it !!!

---

