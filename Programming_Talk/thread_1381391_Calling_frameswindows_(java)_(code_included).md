---
title: "Calling frames/windows (java) (code included)"
date: 2010-01-14
forum: Programming Talk
---

### Post by JayKay3000 on 2010-01-14
Well guys and girls i'm stuck and I hope you can help.

I'm having some trouble trying to call a different window/frame/whatever technical term is.

I decided to use some sample code from a book.

The normal way I load windows i first create a static method (Menu being the place starter point/loging point to the prog (i've ommited most of the other code):


```
public class Menu extends JFrame implements ActionListener {
    private static CurrentVersion window1;
```Then at the bottom of the page I call to load each window and set them up on the screen.
```

     public static void main(String[] args) {
         Menu mymenu = new Menu();

         for creating the Current Network Version window    
         window1 = new CurrentVersion("Modify The Network Plan");
         Toolkit theKit1 = window1.getToolkit();
         window1.setVisible(false);
         Dimension wndSize1 = theKit1.getScreenSize();
         window1.setBounds(wndSize1.width/4, wndSize1.height/4,        // Position
         wndSize1.width/2, wndSize1.height/2);      // Size

            //for creating the Compare window    
         window2 = new Compare("Compare");
         Toolkit theKit2 = window2.getToolkit();
         window2.setVisible(false);
         Dimension wndSize2 = theKit2.getScreenSize();
         window2.setBounds(wndSize2.width/500, wndSize2.height/4,        // Position
         wndSize2.width/1, wndSize2.height/2);      // Size
         
         //for creating the Changes window    
         window3 = new Changes("Changes");
         Toolkit theKit3 = window3.getToolkit();
         window3.setVisible(false);
         Dimension wndSize3 = theKit3.getScreenSize();
         window3.setBounds(wndSize3.width/4, wndSize3.height/4,        // Position
         wndSize3.width/2, wndSize3.height/2);      // Size
         
         //for creating the Backup window    
         window4 = new Backup("Backup");
         Toolkit theKit4 = window4.getToolkit();
         window4.setVisible(false);
         Dimension wndSize4 = theKit4.getScreenSize();
         window4.setBounds(wndSize4.width/4, wndSize4.height/4,        // Position
         wndSize4.width/2, wndSize4.height/2);      // Size
                  
```Then when I want a menu item I call it from the menu by simply setting it to not visible:

```

    modify.addActionListener(new ActionListener() {
        public void actionPerformed(ActionEvent arg0) {
            window1.setVisible(true);
        }
    });

```So... 

Below is the "Current Version" code for letting you do sql queries, this code runs fine as standalone but I can't seem to integrate it into my main Menu class (java file). It simply says "cannot find symbol, window1 = new Current Version("Modify the newtork plan");. Bear in mind i've had this file run perfectly find using a bit of code that simply displays everything from a database.
```

import java.awt.BorderLayout;
import java.awt.event.WindowAdapter;          
import java.awt.event.WindowEvent;          
import java.awt.event.ActionEvent;          
import java.awt.event.ActionListener;          
import javax.swing.JFrame;               
import javax.swing.JTextField;               
import javax.swing.JTextArea;               
import javax.swing.JMenu;               
import javax.swing.JMenuBar;               
import javax.swing.JMenuItem;               
import javax.swing.JScrollPane;               
import javax.swing.JTable;       
import java.sql.DriverManager;                  
import java.sql.Connection;                  
import java.sql.Statement;                  
import java.sql.SQLException;                  

public class CurrentVersion extends JFrame implements ActionListener {
  public static void main(String[] args) {
   // Set default values for the command line args
   String user     = "guest";
   String password = "guest";
   String url      = "jdbc:odbc:technical_library";
   String driver   = "sun.jdbc.odbc.JdbcOdbcDriver";

   // Up to 4 arguments in the sequence database url,driver url, user ID, password
   switch(args.length) {
     case 4:                                 // Start here for four arguments
       password = args[3];
       // Fall through to the next case
     case 3:                                 // Start here for three arguments
       user = args[2];
       // Fall through to the next case
     case 2:                                 // Start here for two arguments
       driver = args[1];
       // Fall through to the next case
     case 1:                                 // Start here for one argument
       url = args[0];
   
  CurrentVersion theApp = new CurrentVersion(driver, url, user, password);
  }
  }

  public CurrentVersion(String driver, String url, 
                        String user , String password) {
      
      JFrame frame = new JFrame(); 
   // super("CurrentVersion");                     // Call base constructor
   // setBounds(0, 0, 400, 300);                   // Set window bounds
    frame.setDefaultCloseOperation(DISPOSE_ON_CLOSE);  // Close window operation
  //  addWindowListener(new WindowAdapter() {      // Listener for window close
            // Handler for window closing event
       //     public void windowClosing(WindowEvent e) {
       //       dispose();                         // Release the window resources
       //       System.exit(0);                    // End the application
      //      }
     //     } );

    // Add the input for SQL statements at the top
    command.setToolTipText("Key SQL commmand and press Enter");
    getContentPane().add(command, BorderLayout.NORTH);

    // Add the status reporting area at the bottom
    status.setLineWrap(true);
    status.setWrapStyleWord(true);
    getContentPane().add(status, BorderLayout.SOUTH);

    // Create the menubar from the menu items
    JMenu fileMenu = new JMenu("File");          // Create File menu
    fileMenu.setMnemonic('F');                   // Create shortcut
    fileMenu.add(clearQueryItem);                // Add clear query item
    fileMenu.add(exitItem);                      // Add exit item
    menuBar.add(fileMenu);                       // Add menu to the menubar
    setJMenuBar(menuBar);                        // Add menubar to the window

    // Add listeners for text field and menu items
    command.addActionListener(this);
    clearQueryItem.addActionListener(this);
    exitItem.addActionListener(this);

    // Establish a database connection and set up the table
    try {
      Class.forName(driver);                     // Load the driver
      connection = DriverManager.getConnection(url, user, password);
      statement = connection.createStatement();

      model = new ResultsModel1();                // Create a table model
      JTable table = new JTable(model);          // Create a table from the model
      table.setAutoResizeMode(JTable.AUTO_RESIZE_OFF);   // Use scrollbars
      resultsPane = new JScrollPane(table);      // Create scrollpane for table
      getContentPane().add(resultsPane, BorderLayout.CENTER);
    } catch(ClassNotFoundException cnfe) {
      System.err.println(cnfe);                    // Driver not found
    } catch(SQLException sqle) {
      System.err.println(sqle);                    // error connection to database
    }
    pack();
    frame.setVisible(true);
  }

  // Handles action events for menu items and the text field
  public void actionPerformed(ActionEvent e) {
    Object source = e.getSource();
    if(source == command) {                      // Enter key for text field input
      executeSQL();
    } else if(source == clearQueryItem) {        // Clear query menu item
      command.setText("");                       // Clear SQL entry
    } else if(source == exitItem) {              // Exit menu item
      dispose();                                 // Release the window resources
      System.exit(0);                            // End the application
    }    
  }

  // Executes an SQL command entered in the text field
  public void executeSQL() {
    String query = command.getText();            // Get the SQL statement
    if(query == null||query.length() == 0) {     // If there's nothing we are done
      return;
    }
    try {
      model.setResultSet(statement.executeQuery(query));
      status.setText("Resultset has " + model.getRowCount() + " rows.");
    } catch (SQLException sqle) {
      status.setText(sqle.getMessage());        // Display error message
    }
  }

  JTextField command = new JTextField();      // Input area for SQL
  JTextArea status = new JTextArea(3,1);      // Output area for status and errors
  JScrollPane resultsPane;

  private JMenuBar menuBar = new JMenuBar();                        // The menu bar
  JMenuItem clearQueryItem = new JMenuItem("Clear query");  // Clear SQL item
  JMenuItem exitItem = new JMenuItem("Exit");               // Exit item

  Connection connection;                       // Connection to the database
  Statement statement;                         // Statement object for queries
  ResultsModel1 model;                          // Table model for resultset
}


```So that's my prob. I did take out the case parts and then got told the method was not abstract. I'm at a loss as to how to show this window using my current system.

Have plans to build on this code once I get initial intergration done.

Suggestions are welcome. Preferable usefull ones. I don't know of any other way to call a window as this is the only way i've ever done it.

---

### Post by Axos on 2010-01-14
I admit I have not tried to fully understand what you are trying to do but one problem I can see is you are trying to call a constructor which doesn't exist:

window1 = new CurrentVersion("Modify The Network Plan");

Whereas the only constructor you have in the code you posted is:

public CurrentVersion(String driver, String url, 
                        String user , String password)

...unless I'm overlooking something.

---

### Post by JayKay3000 on 2010-01-15
Thanks for pointing me in the right direction. You saved me a load of time.

So after 15 min of fiddling with that constructor it now works just like all of the rest in the program


Cheers again

---

