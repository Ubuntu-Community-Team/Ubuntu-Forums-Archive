---
title: "Dynamic Displays in Java"
date: 2012-12-09
forum: Programming Talk
---

### Post by kevinharper on 2012-12-09
```
import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;


public class LayoutManageUsers extends JPanel{
	String[][] activeSpecialists = {};
	
	private int userID;
	private JPanel pnlFullName;
	private JPanel pnlHandleUser;
	private JPanel pnlActiveUser;
	private JPanel pnlDContainer;
	private JTextField txtNewUserFullName;
	private JTextField txtNewUserName;
	private JTextField txtNewUserPassword;
	
	private MyDisableButton btnDisableUser;
	
	public LayoutManageUsers(){
		activeSpecialists = DBQueries.getInstance().getActiveSpecialists();
		
		JPanel pnlTitle = new JPanel();
		pnlTitle.setPreferredSize(new Dimension(500, 25));
		pnlTitle.setBackground(Color.WHITE);
		
		JLabel lblTitle = new JLabel("Active Console Users");
		
		pnlTitle.add(lblTitle);

		pnlDContainer = new JPanel();
		pnlDContainer.setBackground(Color.WHITE);
		
		//START: Dynamic list of active users
		this.setLayout(new BorderLayout());
		this.setPreferredSize(new Dimension(500, 500));
		this.setBackground(Color.WHITE);

		int evenOrOdd = 0;
		int userID;
		String userFullName;
		for(int row = 0; row < activeSpecialists.length; row++) {
			userID = Integer.parseInt(activeSpecialists[row][0]);
			userFullName = activeSpecialists[row][1];
			
			pnlActiveUser = new JPanel();
			pnlActiveUser.setLayout(new FlowLayout(FlowLayout.CENTER,0,0));
			pnlActiveUser.setPreferredSize(new Dimension(400, 37));
			
			//user full name layout
			pnlFullName = new JPanel();
			pnlFullName.setLayout(new FlowLayout(FlowLayout.LEFT,0,5));
			pnlFullName.setPreferredSize(new Dimension(190, 25));
			
			JLabel lblActiveUser = new JLabel();
			lblActiveUser.setText(userFullName);
			
			pnlFullName.add(lblActiveUser);
			
			//handle user button layout
			pnlHandleUser = new JPanel();
			pnlHandleUser.setLayout(new FlowLayout(FlowLayout.RIGHT,10,5));
			pnlHandleUser.setPreferredSize(new Dimension(190, 35));
			
			btnDisableUser = new MyDisableButton(userID);
			btnDisableUser.setText("Disable");
			
			pnlHandleUser.add(btnDisableUser);
			
			//alternate row border
			if(evenOrOdd%2 != 0)
				setBackground("WHITE");
			evenOrOdd++;
			
			pnlActiveUser.add(pnlFullName);
			pnlActiveUser.add(pnlHandleUser);
			
			pnlDContainer.add(pnlActiveUser);
        }
		// END: Dynamic list of active users
		
		this.add(pnlTitle, BorderLayout.NORTH);
		this.add(pnlDContainer, BorderLayout.CENTER);
		
		/***
		 * Admin panel @ bottom
		 **/
		JPanel pnlAddUser = new JPanel();
		pnlAddUser.setLayout(new FlowLayout(FlowLayout.RIGHT, 0,0));
		pnlAddUser.setPreferredSize(new Dimension(500,75));
		pnlAddUser.setBackground(Color.WHITE);
		
		JPanel pnlNewUserTitle = new JPanel();
		pnlNewUserTitle.setPreferredSize(new Dimension(500, 25));
		pnlNewUserTitle.setBackground(Color.WHITE);
	
		JLabel lblNewUserTitle = new JLabel();
		lblNewUserTitle.setText("Create a new User");
		
		pnlNewUserTitle.add(lblNewUserTitle);
		
		//User Full Name
		JPanel pnlNewUserFullName = new JPanel();
		pnlNewUserFullName.setPreferredSize(new Dimension(140, 25));
		pnlNewUserFullName.setBackground(Color.WHITE);
		
		JLabel lblNewUserFullName = new JLabel("Name");
		
		txtNewUserFullName = new JTextField();
		txtNewUserFullName.setPreferredSize(new Dimension(55,20));
		
		pnlNewUserFullName.add(lblNewUserFullName);
		pnlNewUserFullName.add(txtNewUserFullName);
		
		//Username
		JPanel pnlNewUserName = new JPanel();
		pnlNewUserName.setPreferredSize(new Dimension(140, 25));
		pnlNewUserName.setBackground(Color.WHITE);
		
		JLabel lblNewUserName = new JLabel("Username");
		
		txtNewUserName = new JTextField();
		txtNewUserName.setPreferredSize(new Dimension(55,20));
		
		pnlNewUserName.add(lblNewUserName);
		pnlNewUserName.add(txtNewUserName);
		
		//Password
		JPanel pnlNewUserPassword = new JPanel();
		pnlNewUserPassword.setPreferredSize(new Dimension(140, 25));
		pnlNewUserPassword.setBackground(Color.WHITE);
		
		JLabel lblNewUserPassword = new JLabel("Password");
		
		txtNewUserPassword = new JTextField();
		txtNewUserPassword.setPreferredSize(new Dimension(55,20));
		
		pnlNewUserPassword.add(lblNewUserPassword);
		pnlNewUserPassword.add(txtNewUserPassword);
		
		//Add user button
		JButton btnAddUser = new JButton();
		btnAddUser.setText("Add User");
		btnAddUser.addActionListener(new addUser());
		
		pnlAddUser.add(pnlNewUserTitle);
		pnlAddUser.add(pnlNewUserFullName);
		pnlAddUser.add(pnlNewUserName);
		pnlAddUser.add(pnlNewUserPassword);
		pnlAddUser.add(btnAddUser);
		
		this.add(pnlAddUser, BorderLayout.SOUTH);
	}
	
	/***
	 * addUser() adds a new user when "Add User" button is clicked.
	 * Function verifies that no field was left blank.
	 **/
	private class addUser implements ActionListener{
		private boolean isFullNameValid = true;
		private boolean isUserNameValid = true;
		private boolean isPasswordValid = true;
		
		String fullName;
		String userName;
		String password; 
		
		@Override
		public void actionPerformed(ActionEvent ae){
			isFullNameValid = chkFullName();
			isUserNameValid = chkUserName();
			isPasswordValid = chkPassword();
			
			//display red backgrounds where errors found, return (exit)
			if(isFullNameValid == false || isUserNameValid==false || isPasswordValid == false){
				bgError(isFullNameValid, isUserNameValid, isPasswordValid);
				return;
			}
			
			fullName = txtNewUserFullName.getText().trim();
			userName = txtNewUserName.getText().trim();
			password = txtNewUserPassword.getText().trim();
			
			DBQueries.getInstance().addNewSpecialist(fullName, userName, password);
		}
	}
	
	/***
	 * chkFullName() checks input from txtNewUserFullName.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkFullName(){
		boolean isValid = true;
		
		if(txtNewUserFullName.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * chkUserName() checks input from txtNewUserName.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkUserName(){
		boolean isValid = true;
		
		if(txtNewUserName.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * chkPassword() checks input from txtNewUserPassword.
	 * It returns true if input is valid and false if invalid is detected.
	 **/
	private boolean chkPassword(){
		boolean isValid = true;
		
		if(txtNewUserPassword.getText().trim().equals(""))
			isValid = false;
			
		return isValid;
	}
	
	/***
	 * bgError() changes the background color of all text fields previously
	 * 	found to contain invalid data.
	 * @param validFullNameValid, validUserNameValid, validPasswordValid
	 **/
	private void bgError(boolean validFullNameValid, boolean validUserNameValid, boolean validPasswordValid){
		if(validFullNameValid == false){
			txtNewUserFullName.setBackground(Color.RED);
		}
		
		if(validUserNameValid == false){
			txtNewUserName.setBackground(Color.RED);
		}
		
		if(validPasswordValid == false){
			txtNewUserPassword.setBackground(Color.RED);
		}
	}
	
	/***
	 * setBackground() alternates background color or "rows" that display active users'
	 * 	names. It sets all panels' backgrounds to GRAY or WHITE.
	 */
	private void setBackground(String color){
		if(color.trim().equals("WHITE")){
			pnlActiveUser.setBackground(Color.WHITE);
			pnlFullName.setBackground(Color.WHITE);
			pnlHandleUser.setBackground(Color.WHITE);
		}
	}	
}
```
This above class displays a list of active users. The rows alternate in color (white & gray). Each row has its own button for deactivation. When clicked, the corresponding user is disabled from the system.

Two questions...
How do I get the corresponding row to be removed from view when the user is removed? I want the white/gray color scheme to stay true. Instead of removing a row do I have to instead "refresh" the user panel?

I also want to add an "Edit" button but how do I let the userEdit panel know the user id of the user I want to edit? I was hoping to create one panel that would accept an id and then pull information for that one user from the DB but this has proven to be a little more difficult than I thought.

Any suggestions? Any links?

---

### Post by Unterseeboot_234 on 2012-12-10
This is the old MVC -- Model, View, Controller of JTable, which can be daunting to first-time coders. Basically, all edits pass through the Model which fires your implemented choice of Listeners to update the View using TableCellRenderer. Note that JTable is a cauldron mixture of awt.table and javax.swing.JTable.

The best how-to for JTable is a discontinued book by Manning Publications -- "Swing" (Robinson and Vorobiev). The website description page for that book used to have a free download of edition I of the book as a MSWord.doc. The Oracle tuts and API won't get you to your own project goals because JTable is a tiered outlook on GUI.

---

### Post by slickymaster on 2012-12-10
> **Unterseeboot_234 said:**
> The best how-to for JTable is a discontinued book by Manning Publications -- "Swing" (Robinson and Vorobiev). The website description page for that book used to have a free download of edition I of the book as a MSWord.doc. The Oracle tuts and API won't get you to your own project goals because JTable is a tiered outlook on GUI.


Unterseeboot_234 is right. I myself resorted repeatedly to that book. In any case if you're interested in taking a look at the book take note that the official site no longer exists, you have to link to a mirror of the official web-site for the book, [here]("http://www.grandt.com/sbe/").

---

### Post by kevinharper on 2012-12-10
So I need to display my users in JTable data cells instead of a panel?

There's no easier way to just add an id to a panel and hide that panel using the id?

Or maybe a way to refresh the panel after a new user has been added or a current user has been disabled?

What about my issue with the "Edit" button? An "edit" button appears to the right of each user's name. Clicking it changes display to a panel with that user's information (editable). Surely not everything that needs to be updated on-the-fly requires JTabels.

---

### Post by slickymaster on 2012-12-11
I think the JTable object will address all your needs because it provides an editable view of the data you get from your database.

As Unterseeboot_234 said in his post, JTable is a MVC component  divided into 3 parts. I usually approach JTables like this:

**_Model:_** This is the part that takes care of the data, who controls and distributes data in JTable. It is implemented by the TableModel interface (AbstractTableModel and DefaultTableModel).

```
import java.util.ArrayList;
import javax.swing.table.AbstractTableModel;

public class YourTabelModel extends AbstractTableModel
{
    private String[] columnNames = {"DATA1", "DATA2", "DATA3"};
    private ArrayList<YourData> dataResultSet = null;;
    
    public YourTabelModel(ArrayList<YourData> rSet)
    {
        this.dataResultSet = rSet;
    }

    @Override
    public int getRowCount() 
    {
        return dataResultSet.size();
    }

    @Override
    public int getColumnCount() 
    {
        return columnNames.length;
    }
    
    @Override
    public String getColumnName(int index)
    {
        return columnNames[index];
    }
    
    @Override
    public Object getValueAt(int rowIndex, int columnIndex)
    {
        YourData yd = (YourData) dataResultSet.get(rowIndex);

        switch (columnIndex)
        {
            case 0:
                return yd.getDATA1();
            case 1:
                return yd.getDATA2()();
            case 2:
                return yd.getDATA3();
        }
        return yd;
    }    
}
```

_**View:**_ This is the part that takes care of the presentation. It is implemented by CellRenderer interface and like the presentation is given in the table, cell to cell, the renderer should be provided for a specific cell.

```
import java.awt.Component;
import javax.swing.JTable;
import javax.swing.table.DefaultTableColumnModel;
import javax.swing.table.TableCellRenderer;
import javax.swing.table.TableColumn;

public class TableFormater 
{    
    private final int margin = 2;
    
    public void packColumns(JTable yourTabel)
    {
        for (int columnIndex = 0; columnIndex < yourTabel.getColumnCount(); columnIndex++)
        {
            packColumn(yourTabel, columnIndex, margin);
        }
    }

    /*
     * Sets the preferred width of the visible column specified by vColIndex. The column
     * will be just wide enough to show the column head and the widest cell in the column.
     * margin pixels are added to the left and right (resulting in an additional width of 2*margin pixels).
     */
    private void packColumn(JTable yourTabel, int columnIndex, int margin) 
    {
        DefaultTableColumnModel colModel = (DefaultTableColumnModel)yourTabel.getColumnModel();
        TableColumn column = colModel.getColumn(columnIndex);
        
        // Get width of column header
        TableCellRenderer renderer = column.getCellRenderer();
        if (renderer == null) {
            renderer = yourTabel.getTableHeader().getDefaultRenderer();
        }
        
        Component comp = renderer.getTableCellRendererComponent(
                yourTabel, column.getHeaderValue(), false, false, 0, 0);
        int width = comp.getPreferredSize().width;
        
        // Get maximum width of column data
        for (int i = 0; i < yourTabel.getRowCount(); i++) 
        {
            renderer = yourTabel.getCellRenderer(i, columnIndex);
            comp = renderer.getTableCellRendererComponent(
                yourTabel, yourTabel.getValueAt(i, columnIndex), false, false, i, columnIndex);
            width = Math.max(width, comp.getPreferredSize().width);
        }

        // Add margin
        width += 2*margin;

        // Set the width
        column.setPreferredWidth(width);        
    }
}

```

_**Controller:**_ It's the part that controls the presentation of the data in the view. It's the very JTable and as it has already been implemented to use the existing defaults types, to create a simple JTable is not that complicated. In the code bellow I use my JTable as pop-up window, thus the implementation in a JFrame, but normamlly it's implemented in a JPanel.

```
private void showTable(ArrayList<YourData> yd) 
    {
        // Create a new table instance
        modTab = new TabelModel(yd);
        yourTable = new JTable(modTab);
        yourTable.setAutoResizeMode(JTable.AUTO_RESIZE_OFF);
        yourTable.setShowGrid(true);
        // Handles the listener
        ListSelectionModel selectionModel = yourTable.getSelectionModel();
        selectionModel.setSelectionMode(ListSelectionModel.SINGLE_INTERVAL_SELECTION);
        selectionModel.addListSelectionListener(this);
        // Formats the width of the columns to the width of the data
        TableFormater tabFormater = new TableFormater();
        tabFormater.packColumns(yourTable);
        // Displays the table
        tablePanel = new TablePanel();
        tablePanel.scPane.getViewport().add(yourTable, null);
        tablePanel.setVisible(true);
    }
```

```
import java.awt.*;
import javax.swing.JFrame;
import javax.swing.JScrollPane;

@SuppressWarnings("serial")
public class TablePanel extends JFrame
{
    public JScrollPane scPane;

    public TablePanel()
    {
        setLayout(new BorderLayout());
        
        setTitle("Your Title");
        setResizable(false);
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);  
        scPane = new JScrollPane();
        scPane.setHorizontalScrollBarPolicy(JScrollPane.HORIZONTAL_SCROLLBAR_AS_NEEDED);
        scPane.setVerticalScrollBarPolicy(JScrollPane.VERTICAL_SCROLLBAR_AS_NEEDED);
        scPane.setPreferredSize(new Dimension (800, 400));
        add(scPane, BorderLayout.SOUTH);
        this.pack();
        centerWindow(this);
    }
    
    private void centerWindow(Window w)
    {
        Toolkit tk = Toolkit.getDefaultToolkit();
        Dimension d = tk.getScreenSize();
        setLocation((d.width-w.getWidth())/2, (d.height-w.getHeight())/2);
    }
}

```

One thing you have to keep in mind is that there are two problems with having a JButton in a JTable. Firstly, by default a JTable will display cell values as a String, so JButtons appear as "javax.swing.JButton". Secondly, a JTable does not pass clicks through to the cells.
To display the buttons correctly a custom cell renderer needs to be applied to any columns displaying JButtons. To get the table to pass clicks through to the button, add a mouse listener to the table with table.addMouseListener(new JTableButtonMouseListener(table)) method. This mouse listener will have to take the click, work out in which cell it occurred and if that cell contains a JButton, click it.

Hope this will help you.

---

### Post by Unterseeboot_234 on 2012-12-11
I sure like JTable over <html>, batik.java and I'm always ready to go pure Graphics2D. 

You can do <html table> on a JPanel. However, Sun promised .css and HTML5 and we are still not there.

batik is an opensource project that draws with .SVG. Count on linking a lot of .jars into the classpath to use batik. Too bad batik never caught on because it offers zoomable GUI graphics for big or small viewing.

Swing has its advantage in that the GUI is ready for events. JTable API has a choice of over 10 possibilities for a Listener(s) (before we speak of Drag-n-Drop). The choice of listener determines the design of JTable. That's why folks can not just copy and paste code for JTable.

Look at Oracle's [tut]("http://docs.oracle.com/javase/tutorial/uiswing/components/table.html") for JTable and they have an example with popup dialog.

---

### Post by slickymaster on 2012-12-11
I'm attaching a small Netbeans project where I use JTable. Hopefully it will help you to understand the way I've implemented it in the application.

Keep in mind that I'm using JTatto Look and Feel in the project, so you have to add that jar to your Libraries.
Another jar you have to add to the Libraries is sqljdbc4.jar because I'm using a SQL Server database, and don't forget to adapt the connectionURL

---

### Post by Unterseeboot_234 on 2012-12-11
Hey SlickyMaster, nice code. I would only suggest that JPanel is already default FlowLayout(). JFrame is default BorderLayout(). The LayoutManagers are the old AWT stuff that nobody seems to know any more.

For the constructor of JPanel
this.setAlignment( FlowLayout.RIGHT ); // no import needed

Turn on your Forums private message some time.

---

### Post by slickymaster on 2012-12-11
> **Unterseeboot_234 said:**
> Hey SlickyMaster, nice code. I would only suggest that JPanel is already default FlowLayout(). JFrame is default BorderLayout(). The LayoutManagers are the old AWT stuff that nobody seems to know any more.

For the constructor of JPanel
this.setAlignment( FlowLayout.RIGHT ); // no import needed

Turn on your Forums private message some time.

I see your point, but I'm really used to work with GridBagLayout. To me it's the more flexible, in terms of the design of UIs, of all the LayoutManagers.

Yes, I agree with you, these days it's all about web services. And in Java development, regarding desktop stand alone applications or client side interfaces, everybody is using JavaFX.
I must admite I've not tried JavaFx yet, but I'm planning on diving into it in the begging of next year.

I think now my forum private messages are on. Never even notice the default was off.

---

### Post by kevinharper on 2012-12-11
Thank you guys for your suggestions. I will take a look at how you write your code slickymaster.

I'll see if I can incorporate JTable into my project... Although tonight is really the last night I can work on it (It's due Thursday and I have to write up a lot of documentation for it).

---

