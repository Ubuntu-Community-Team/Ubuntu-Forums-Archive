---
title: "MVC in Java"
date: 2009-06-02
forum: Programming Talk
---

### Post by Coldhearth on 2009-06-02
I would like to create an application that uses a MySQL database, I already have installed MySQL and de MySQL connectorJ for connecting through Java and I already have a database class that implements methodes for querying and updating databases.
And I would like to implement this with the MVC because I've heard it's a very good design pattern to create database driver applications.

Problem is I don't really now how to start out, besides my views I haven't the slightest idea how to create this structure...

If anyone here can point me in the right direction I would be very grateful. :)

---

### Post by dwhitney67 on 2009-06-02
MVC = Model-Viewer-Controller

The database interface best sits in the Model area.  The Viewer is the GUI, and the Controller is the interface between the Viewer and the Model.

---

### Post by Coldhearth on 2009-06-02
So I would have to put my DatabaseConnection class in the model package?
Not in a seperate package...?

---

### Post by dwhitney67 on 2009-06-02
> **Coldhearth said:**
> So I would have to put my DatabaseConnection class in the model package?
Not in a seperate package...?

The DatabaseConnection should be/remain a separate package, however it should be used by the Model for storing/retrieving data from the database.

---

### Post by Coldhearth on 2009-06-02
Hmmm I don't seem to understand the pattern like I should...
Can anyone maybe post a small sample application that explains the pattern better? :)

---

### Post by CptPicard on 2009-06-02
[http://www.enode.com/x/markup/tutorial/mvc.html](http://www.enode.com/x/markup/tutorial/mvc.html)

First google result for "model-view-controller example" :)

---

### Post by Coldhearth on 2009-06-02
Thx :) but it's not that I can't find any examples though it's that there are a lot of examples who are to big or who are somewhat different from other examples...
Thanks to this people like me who don't know the pattern are confused on what the exact usage of MVC should really be I think:)

---

### Post by Coldhearth on 2009-06-02
After doing some research on google this afternoon I'm still wondering what the best implementation is of MVC... I must have encountered more than 3 implementations of the MVC for applications.

If anyone can tell me what the right implementation is to use and give me an example in code I would be very grateful because I'm struggling to get this right.

---

### Post by CptPicard on 2009-06-02
There is no "right implementation". It's a design pattern (way to structure your application) you use when you, the developer, feel like it is the correct design strategy to use.

It really is not that difficult a concept... you divide your application into a model (that contains the data), the views (code that contains ways of displaying the data) and controllers that encapsulate application logic. This is a very clear separation that, when wired together, is not only architecturally pretty but also gives quite a bit of flexibility for extension.

---

### Post by dwhitney67 on 2009-06-02
I should have stated this earlier, but at the time I did not think it was relevant.  MVC is not a design pattern, but instead a design paradigm.

The MVC paradigm is used in laying out the responsibilities of each facet of the application(s).  THe first diagram shown in the link provided by CaptPicard pretty much summarizes this.

Since you are working with Java, think of the Controller as the object that instantiates an object to display the GUI (the Viewer) and another object (the Model) to serve as the front-end to the data repository.  Meanwhile, the Controller will tender its services to handle Viewer updates by listening for "actions".  Types of actions can range from any number of sources:  operator input, the expiration of a timer, data updates to the Model, etc.

In certain applications, the Controller, the Viewer and the Model are setup as 3 separate applications that communicate over some type of communication channel, shared memory, or other nifty interface.  But the MVC paradigm still holds true.

The whole point of the MVC is to separate each area such that at any point in time, an area can be replaced (with hopefully a superior product), and yet require minimal upgrades to the rest of the system.

If you have already started your project and would like feedback on whether it follows the MVC paradigm, please give us a hint of what the design looks like.

---

### Post by Coldhearth on 2009-06-02
Hmmm well can you help me to change this application into a working MVC application? Now it's just a skeleton ofcourse... Here's the code:
(This is just a test application for myself to learn MVC ofcourse)

MAIN:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package mvctest;

import view.CalculatorFrame;

/**
 *
 * @author coldhearth
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        CalculatorFrame app = new CalculatorFrame();
    }

}

```

MODEL:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

/**
 *
 * @author coldhearth
 */
public class Sum {
    private int number1, number2;

    public Sum(int number1, int number2){
        setNumber1(number1);
        setNumber2(number2);
        }

    public void setNumber1(int number1){
        this.number1 = number1;
    }

    public void setNumber2(int number2){
        this.number2 = number2;
    }

    public int getNumber1(){
        return number1;
    }

    public int getNumber2(){
        return number2;
    }
}

```

VIEW:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;


/**
 *
 * @author coldhearth
 */
public class CalculatorFrame {

    JFrame calcFrame;
    JTextField number1TextField, number2TextField;
    JLabel totalLabel;
    JButton calculateButton;

    public CalculatorFrame(){
        initGUI();
    }

    public void initGUI(){
        calcFrame = new JFrame("Calculator");
        number1TextField = new JTextField(20);
        number2TextField = new JTextField(20);
        totalLabel = new JLabel("Total comes here");
        calculateButton = new JButton("Calculate");
        calculateButton.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e){
                //Insert code to add integers to eachother through the 
                //Sum class 
                int num1 = 
                Integer.parseInt(number1TextField.getText());
                int num2 = 
                Integer.parseInt(number2TextField.getText());
                
            }
        });

        calcFrame.setSize(400, 200);
        calcFrame.setVisible(true);
        calcFrame.setLocationRelativeTo(null);
        calcFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        calcFrame.setLayout(new FlowLayout());

        Container container = calcFrame.getContentPane();
        container.add(number1TextField);
        container.add(number2TextField);
        container.add(calculateButton);
        container.add(totalLabel);
    }

}

```

CONTROLLER:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package controller;

/**
 *
 * @author coldhearth
 */
public class CalculatorController {

}

```

---

### Post by Reiger on 2009-06-02
Nevermind.

---

### Post by Coldhearth on 2009-06-02
Hmm well I was planning on creating a application where you can add edit and delete records to a database. Also show an overview of what's in tha database and search in the database... 
But without first nowing how to implement MVC I don't really know how to begin...

[Edit]:
I think I would learn best if I get a good example ... is there no one who can show me some sourcecode? :)

---

### Post by dwhitney67 on 2009-06-02
In your case, I would have the Controller instantiate the CalculatorFrame, not the main() function.  The main() function in turn would instantiate the Controller object.

Alternatively, you could have a Calculator object that contains the Controller, the CalculatorFrame, and the Sum, which, by the way, I would rename as Register.

Think of the CalculatorFrame as the area where the user will enter a value, an operator (e.g. a '+', '-', etc.) and then another value, and possibly other operator/value combos, etc.  Only when the user selects the '=' button should the string, for example "N1+N2-N3", be obtained by the Controller, where the operation is performed, the result stored in the Register and also displayed on the CalculatorFrame.

If the user selects the "M" button on the calculator, then the value currently in the Register will be saved for posterity.  If the user selects the "CLR" button, the value in the Register is cleared, but the value previously save in memory will still be available.

It should be the Controller that receives the "=", "M", "M+", "M-", "MR" actions.  The others can be handled by the CalculatorFrame.  Thus, for those aforementioned buttons, you would want to use the Controller object as the listener, not an anonymous ActionListener object.  The anonymous ActionListener can handle the mundane stuff of number buttons, operator buttons, etc, rejecting of course any illegal entries (e.g. do not allow 3++4).

Does this make sense?

---

### Post by Coldhearth on 2009-06-02
Look, that's exactly what I don't understand...
What does the controller what does the main... how hangs everything together etc...  :s It's just realy confusing to me for some reason :(

---

### Post by Reiger on 2009-06-02
Think about it as the following problem:

You walk into a store and you ask one of the staff for something. The staff doesn't know the answer to your question: it asks its manager.
The manager doesn't know either, but at least the manager does know about the other staff in other locations that are bound to know. So he/she asks the other staff. That staff *does* know, gives the manager their answer who in turn informs his/her staff of the answer who then get back to you.

---

### Post by Coldhearth on 2009-06-02
Okay, I have build my application from the ground up just now.
Let me begin with just de view for the login window and the classes that I have now:

MAIN:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package routeplanner;

/**
 *
 * @author coldhearth
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

    }

}

```

DATALAYER (package for database class)
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package datalayer;

import java.sql.*;
import javax.swing.*;

/**
 *
 * @author coldhearth
 */
public class MysqlConnector {

    private Connection con;
    private static MysqlConnector connection;

    public static MysqlConnector getInstance(){
        if(connection == null){
            connection = new MysqlConnector();
        }
        return connection;
    }

    private MysqlConnector(){
        try{
            Class.forName("com.mysql.jdbc.Driver");
            con = DriverManager.getConnection("jdbc:mysql://localhost/testdb", "root", "root");
        }catch(ClassNotFoundException classNotFoundException){
            JOptionPane.showMessageDialog(null, "Error: " + classNotFoundException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }catch(SQLException sqlException){
            JOptionPane.showMessageDialog(null, "Error: " + sqlException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public ResultSet voerQueryUit(String sqlString){
            ResultSet result=null;
            Statement statement;
        try{
            statement = con.createStatement();
            result = statement.executeQuery(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
        return result;
    }

    public void voerUpdateUit(String sqlString){
        Statement statement;
        try{
            statement = con.createStatement();
            statement.executeUpdate(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
    }
}

```

VIEW:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

/**
 *
 * @author coldhearth
 */
public class LoginJFrame {
    /*public static void main(String [] args){
        new LoginJFrame();
    }*/
    JFrame loginFrame;
        JPanel loginPanel;
            JLabel usernameLabel;
            JTextField usernameTextField;
            JLabel passwordLabel;
            JTextField passwordTextField;
        JButton reset, login;

    public LoginJFrame(){
         initGUI();
    }

    public void initGUI(){
        loginFrame = new JFrame("Login");

        loginPanel = new JPanel();
        loginPanel.setBorder(BorderFactory.createTitledBorder("Login"));
        loginPanel.setLayout(new BoxLayout(loginPanel, BoxLayout.Y_AXIS));

        usernameLabel = new JLabel("Username");
        usernameTextField = new JTextField(10);
        passwordLabel = new JLabel("Password");
        passwordTextField = new JTextField(10);
        reset = new JButton("Reset");
        reset.addActionListener(new ActionListener(){
                public void actionPerformed(ActionEvent e){
                    usernameTextField.setText("");
                    passwordTextField.setText("");
                }
            }
        );
        login = new JButton("Login");
        login.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e){
                //Login control method call to controller

            }
        }
        );

        loginFrame.setLocationRelativeTo(null);
        loginFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        loginFrame.setVisible(true);
        loginFrame.setSize(300, 250);
        loginFrame.setLayout(new BorderLayout());

        Container container = loginFrame.getContentPane();
        container.add(loginPanel, BorderLayout.NORTH);
        loginPanel.add(usernameLabel);
        loginPanel.add(usernameTextField);
        loginPanel.add(passwordLabel);
        loginPanel.add(passwordTextField);
        container.add(reset, BorderLayout.CENTER);
        container.add(login, BorderLayout.SOUTH);


    }

}

```

CONTROLLER:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package controller;



/**
 *
 * @author coldhearth
 */
public class LoginController {
    
}

```

MODEL:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

/**
 *
 * @author coldhearth
 */
public class User {
    private String username;
    private String password;
    
    public User(String username, String password){
        setUsername(username);
        setPassword(password);
    }
    
    public void setUsername(String username){
        this.username = username;
    }
    
    public void setPassword(String password){
        this.password = password;
    }
    
    public String getUsername(){
        return username;
    }
    
    public String getPassword(){
        return password;
    }
}

```

It's now the meaning that the actionlistener goes to the database and finds out if the username and password exist for the user through the User class...

Can anyone tell me how to implement this design into MVC?

---

### Post by CptPicard on 2009-06-02
It should also be noted that quite often, if the controller is really lightweight, it is combined into the View (look at typical Java Swing code with Listeners as anonymous inner classes)...

Anyways, I think your view of this is a bit too rigid. It's just a way to design stuff, and for all I can see, you're well on your way to an architecture like that.

---

### Post by Coldhearth on 2009-06-02
Yes I know I can combine the controller with the view but I would like to keep de controller package.

So to make this login control system work... any suggestions.
With this I mean ... how do I make an MVC application of these packages and classes I already have? What's still missing to make it a good working MVC system? :)

---

### Post by Coldhearth on 2009-06-02
Okay I have the following code and I can check if my login and password are correct :) But it keeps giving me following error:
[B]Exception in thread "main" java.lang.ClassCastException: view.LoginJFrame cannot be cast to view.UserObserver
        at view.LoginJFrame.<init>(LoginJFrame.java:37)
        at routeplanner.Main.main(Main.java:25)[/B]

My code is:

MAIN:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package routeplanner;

import view.LoginJFrame;
import controller.LoginController;
import model.User;

/**
 *
 * @author coldhearth
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        User model = new User();
        LoginController controller = new LoginController(model);
        LoginJFrame app = new LoginJFrame(controller, model);
    }

}

```

DATALAYER (for database purposes)
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package datalayer;

import java.sql.*;
import javax.swing.*;

/**
 *
 * @author coldhearth
 */
public class MysqlConnector {

    private Connection con;
    private static MysqlConnector connection;

    public static MysqlConnector getInstance(){
        if(connection == null){
            connection = new MysqlConnector();
        }
        return connection;
    }

    private MysqlConnector(){
        try{
            Class.forName("com.mysql.jdbc.Driver");
            con = DriverManager.getConnection("jdbc:mysql://localhost/testdb", "root", "root");
        }catch(ClassNotFoundException classNotFoundException){
            JOptionPane.showMessageDialog(null, "Error: " + classNotFoundException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }catch(SQLException sqlException){
            JOptionPane.showMessageDialog(null, "Error: " + sqlException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public ResultSet voerQueryUit(String sqlString){
            ResultSet result=null;
            Statement statement;
        try{
            statement = con.createStatement();
            result = statement.executeQuery(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
        return result;
    }

    public void voerUpdateUit(String sqlString){
        Statement statement;
        try{
            statement = con.createStatement();
            statement.executeUpdate(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
    }
}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package datalayer;

import java.sql.*;

/**
 *
 * @author coldhearth
 */
public class LoginMapper {

    MysqlConnector connection;

    public LoginMapper(){
        connection = MysqlConnector.getInstance();
    }

    public boolean controleLogin(String username, String password){
        boolean result = false;
        String sqlString = "SELECT username, password FROM users WHERE username='" + username + "' && password='" + password + "'";
        ResultSet aantal = connection.voerQueryUit(sqlString);
        
        try{
        while(aantal.next()){
            result = true;
        }
        }catch(SQLException sqlException){

        }
        return result;
    }

}

```

MODEL:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

import view.UserObserver;

/**
 *
 * @author coldhearth
 */
public interface UserInterface {
    public void addObserver(UserObserver o);
    public void removeObserver(UserObserver o);
}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

import datalayer.LoginMapper;
import view.UserObserver;

import javax.swing.*;

import java.util.*;

/**
 *
 * @author coldhearth
 */
public class User implements UserInterface{
    private String username;
    private String password;

    private LoginMapper loginMapper;
    private ArrayList userObservers = new ArrayList();

    public User(){
        loginMapper = new LoginMapper();
    }

    public User(String username, String password){
        setUsername(username);
        setPassword(password);
    }

    public void setUsername(String username){
        this.username = username;
    }

    public void setPassword(String password){
        this.password = password;
    }

    public String getUsername(){
        return username;
    }

    public String getPassword(){
        return password;
    }

    public void addObserver(UserObserver o){
        userObservers.add(o);
    }

    public void removeObserver(UserObserver o){
        int i = userObservers.indexOf(o);
        userObservers.remove(i);
    }

    public void notifyObservers(){
        for(int i=0; i<userObservers.size(); i++){
            UserObserver observer = (UserObserver)userObservers.get(i);
            observer.updateUser();
        }
    }

    public void controleLogin(){
        boolean result = false;
        result = loginMapper.controleLogin(getUsername(), getPassword());
        if(result){
            //Voer methodde uit om in te loggen in view
            //JOptionPane.showMessageDialog(null, "Yaaaaaay");
            notifyObservers();
        }else{
            JOptionPane.showMessageDialog(null, "Wrong login");
        }

    }
}

```

CONTROLLER:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package controller;

import model.User;


/**
 *
 * @author coldhearth
 */
public class LoginController {

    private User model;

    public LoginController(User model){
        this.model = model;
    }

    public void controleLogin(String username, String password){
        model.setUsername(username);
        model.setPassword(password);
        model.controleLogin();
    }

}

```

VIEW:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

/**
 *
 * @author coldhearth
 */
public interface UserObserver {
    public void updateUser();
}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

import controller.LoginController;
import model.User;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

/**
 *
 * @author coldhearth
 */
public class LoginJFrame {
    /*public static void main(String [] args){
        new LoginJFrame();
    }*/
    LoginController loginController;
    User model;

    JFrame loginFrame;
        JPanel loginPanel;
            JLabel usernameLabel;
            JTextField usernameTextField;
            JLabel passwordLabel;
            JTextField passwordTextField;
        JButton reset, login;

    public LoginJFrame(LoginController loginController, User model){
         this.loginController = loginController;
         this.model = model;
         model.addObserver((UserObserver)this);
         initGUI();
    }

    public void initGUI(){
        loginFrame = new JFrame("Login");

        loginPanel = new JPanel();
        loginPanel.setBorder(BorderFactory.createTitledBorder("Login"));
        loginPanel.setLayout(new BoxLayout(loginPanel, BoxLayout.Y_AXIS));

        usernameLabel = new JLabel("Username");
        usernameTextField = new JTextField(10);
        passwordLabel = new JLabel("Password");
        passwordTextField = new JTextField(10);
        reset = new JButton("Reset");
        reset.addActionListener(new ActionListener(){
                public void actionPerformed(ActionEvent e){
                    usernameTextField.setText("");
                    passwordTextField.setText("");
                }
            }
        );
        login = new JButton("Login");
        login.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e){
                //Login control method call to controller
                String username = usernameTextField.getText();
                String pass = passwordTextField.getText();
                loginController.controleLogin(username, pass);
            }
        }
        );

        loginFrame.setLocationRelativeTo(null);
        loginFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        loginFrame.setVisible(true);
        loginFrame.setSize(300, 250);
        loginFrame.setLayout(new BorderLayout());

        Container container = loginFrame.getContentPane();
        container.add(loginPanel, BorderLayout.NORTH);
        loginPanel.add(usernameLabel);
        loginPanel.add(usernameTextField);
        loginPanel.add(passwordLabel);
        loginPanel.add(passwordTextField);
        container.add(reset, BorderLayout.CENTER);
        container.add(login, BorderLayout.SOUTH);


    }

}

```

Am I well on my way of using MVC? Or not? I can check the login but now I want to make a change in my GUI if the login was wrong instead of using a popup dialog box. So I'm working with the observer pattern to do this but it gives me thus an error... :(

Any help and comments would be appreciated :)

---

### Post by slavik on 2009-06-03
I like that one article that basically says that there is no such thing as MVC for the web.

---

### Post by Ruhe on 2009-06-03
[http://martinfowler.com/eaaDev/uiArchs.html]("http://martinfowler.com/eaaDev/uiArchs.html")

For advanced readers.

---

### Post by Coldhearth on 2009-06-03
Okay I think I'm getting it now... there's just one problem when I try to combine this with a DB, I keep getting an nullpointer exception and I don't understand where it's coming from...

The error message is:
```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at model.Task.insertTaskToDB(Task.java:37)
        at model.Task.setTitle(Task.java:32)
        at controller.TaskFrameController.insertTask(TaskFrameController.java:32)
        at view.TaskMainFrame$1.actionPerformed(TaskMainFrame.java:42)
```

My code is:
MAIN:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package simpletaskmanagement;

import model.TaskInterface;
import controller.TaskFrameController;
import model.Task;

/**
 *
 * @author coldhearth
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        //Create controller object
        //Create frame object wish contains controller

        TaskInterface model = new Task();
        TaskFrameController controller = new TaskFrameController(model);
    }

}

```

DATALAYER:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package datalayer;

import java.sql.*;
import javax.swing.*;

/**
 *
 * @author coldhearth
 */
public class MysqlConnector {

    Connection con;
    private static MysqlConnector connection;

    public static MysqlConnector getInstance(){
        if(connection == null){
            connection = new MysqlConnector();
        }
        return connection;
    }

    private MysqlConnector(){
        try{
            Class.forName("com.mysql.jdbc.Driver");
            con = DriverManager.getConnection("jdbc:mysql://localhost/testdb", "root, "root");
        }catch(ClassNotFoundException classNotFoundException){
            JOptionPane.showMessageDialog(null, "Error :" + classNotFoundException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }catch(SQLException sqlException){
            JOptionPane.showMessageDialog(null, "Error: " + sqlException.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public ResultSet queryString(String sqlString){
        ResultSet result = null;
        Statement statement;

        try{
            statement = con.createStatement();
            result = statement.executeQuery(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
        return result;
    }

    public void updateQuery(String sqlString){
        Statement statement;

        try{
            statement = con.createStatement();
            statement.executeUpdate(sqlString);
        }catch(SQLException sqlException){
            sqlException.printStackTrace();
        }
    }

}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package datalayer;

/**
 *
 * @author coldhearth
 */
public class TaskMapper {
    private MysqlConnector connection;

    public TaskMapper(){
        connection = MysqlConnector.getInstance();
    }

    public void insertTask(String title){
        String sqlString = "INSERT INTO tasks (title) VALUES ('" + title + "')";
        connection.updateQuery(sqlString);
    }
}

```

MODEL:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

import view.TaskObserver;

/**
 *
 * @author coldhearth
 */
public interface TaskInterface {
    public void registerObserver(TaskObserver o);
    public void removeObserver(TaskObserver o);
    public void setTitle(String title);
    public String getTitle();
    public void insertTaskToDB();
}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package model;

import view.TaskObserver;
import datalayer.TaskMapper;

import java.util.*;

/**
 *
 * @author coldhearth
 */
public class Task implements TaskInterface{

    private String title;
    private ArrayList taskObservers = new ArrayList();
    private TaskMapper taskMapper;

    public Task(){}

    public Task(String title, TaskMapper taskMapper){
        this.taskMapper = taskMapper;
        setTitle(title);
    }

    public void setTitle(String title){
        this.title = title;
        insertTaskToDB();
        notifyObservers();
    }

    public void insertTaskToDB(){
        taskMapper.insertTask(getTitle());
    }

    public String getTitle(){
        return title;
    }

    public void registerObserver(TaskObserver o){
        taskObservers.add(o);
    }

    public void removeObserver(TaskObserver o){
        int i = taskObservers.indexOf(o);
        if(i >= 0){
            taskObservers.remove(i);
        }
    }

    public void notifyObservers(){
        for(int i=0; i<taskObservers.size(); i++){
            TaskObserver observer = (TaskObserver)taskObservers.get(i);
            observer.updateTask();
        }
    }

}

```

CONTROLLER:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package controller;

import model.TaskInterface;
import model.Task;
import view.SecondTaskMainFrame;
import view.TaskMainFrame;

/**
 *
 * @author coldhearth
 */
public class TaskFrameController {

    private TaskInterface model;

    public TaskFrameController(TaskInterface model){
        this.model = model;
        TaskMainFrame app = new TaskMainFrame(model, this);
        SecondTaskMainFrame app2 = new SecondTaskMainFrame(model, this);
    }

    public void setTaskTitle(String title){
        model.setTitle(title);
    }

    public void insertTask(String title){
        model.setTitle(title);
    }

}

```

VIEW:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

/**
 *
 * @author coldhearth
 */
public interface TaskObserver {
    public void updateTask();
}

```

```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package view;

import model.TaskInterface;
import controller.TaskFrameController;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

/**
 *
 * @author coldhearth
 */
public class TaskMainFrame implements TaskObserver{

    TaskInterface model;
    TaskFrameController controller;

    JFrame taskMainFrame;
    JTextField inputTextField;
    JButton searchButton;
    JTextField outputTextField;

    public TaskMainFrame(TaskInterface model, TaskFrameController controller){
        this.model = model;
        this.controller = controller;
        model.registerObserver((TaskObserver)this);
        initGUI();
    }

    public void initGUI(){
        taskMainFrame = new JFrame("Task frame");
        inputTextField = new JTextField(10);
        searchButton = new JButton("Search");
        searchButton.addActionListener(new ActionListener(){
           public void actionPerformed(ActionEvent e){
                controller.insertTask(inputTextField.getText());
           }
        });
        outputTextField = new JTextField(10);
        outputTextField.setEditable(false);

        taskMainFrame.setLocationRelativeTo(null);
        taskMainFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        taskMainFrame.setSize(400, 200);
        taskMainFrame.setVisible(true);
        taskMainFrame.setLayout(new FlowLayout());

        Container container = taskMainFrame.getContentPane();
        container.add(inputTextField);
        container.add(searchButton);
        container.add(outputTextField);

    }

    public void updateTask(){
        outputTextField.setText(model.getTitle());
    }

}

```

If anyone can tell me where my fault sits I would be grateful :)
Also is this a bit of a good MVC implementation I've used in here?
Or am I still doing something wrong?

---

### Post by Coldhearth on 2009-06-03
Okay I think I found the answer but I'm not sure if I'm using the correct implementation here...

I adjusted my Main.java class:
Created a TaskMapper in here and linked it to the model Task:
```
 TaskMapper datalayer = new TaskMapper();
        TaskInterface model = new Task(datalayer);
```

After that I changed the no body-constructor of Task into:
```
 public Task(TaskMapper taskMapper){
        this.taskMapper = taskMapper;
    }
```

So now there is a TaskMapper object in memory and I don't have a nullpointer exception anymore.

Can someone look at al of my code with these changes and tell me if I'm doing a good job?
I really hope my MVC structure is good this time. :)

---

