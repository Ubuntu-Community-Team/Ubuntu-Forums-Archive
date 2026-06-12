---
title: "Mysql jdbc error!"
date: 2008-10-10
forum: Packaging and Compiling Programs
---

### Post by disappearedng on 2008-10-10
Hi everyone
I wrote two files, and I have connected to my mysql database using jdbc using another program and it has proven to be successful. So I don't think it has anything to do with my Environment.

```

import java.awt.BorderLayout;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Driver;

import javax.swing.JFrame;
import javax.swing.JTextArea;
import javax.swing.JScrollPane;
import javax.swing.ScrollPaneConstants;
import javax.swing.JTable;
import javax.swing.JOptionPane;
import javax.swing.JButton;
import javax.swing.Box;


public class DisplayQueryResults extends JFrame	{
	//variable
	static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
	static final String DATABASE_URL = "jdbc:mysql//localhost/books";
	static final String USERNAME = "disappearedng";
	static final String PASSWORD = "secret";
	
	//default query
	static final String DEFAULT_QUERY = "SELECT * FROM authors";
	
	private ResultSetTableModel tableModel; //declared from other file in package;
	private JTextArea queryArea;
	
	public DisplayQueryResults() throws ClassNotFoundException {
		
		super ( "Displaying Query Results"	);
		
		try		{
			tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL, 
					USERNAME, PASSWORD, DEFAULT_QUERY);
			
			queryArea = new JTextArea( DEFAULT_QUERY, 3, 100);
			queryArea.setWrapStyleWord( true) ;
			queryArea.setLineWrap( true);
			
			JScrollPane scrollPane	 = new JScrollPane(queryArea, 
				ScrollPaneConstants.VERTICAL_SCROLLBAR_AS_NEEDED, ScrollPaneConstants.HORIZONTAL_SCROLLBAR_NEVER);
			
			JButton submitButton = new JButton("Submit Query");
			
			Box box = Box.createHorizontalBox();
			box.add( scrollPane);
			box.add( submitButton);
			
			JTable resultTable = new JTable( tableModel);
			
			add(box , BorderLayout.NORTH);
			add( new JScrollPane( resultTable), BorderLayout.CENTER);
			
			submitButton.addActionListener(	
					new ActionListener()	{
						public void actionPerformed( ActionEvent event)	{
							try	{
								tableModel.setQuery(queryArea.getText() );
							}
							catch (SQLException sqlException)	{
								JOptionPane.showMessageDialog( null,
										sqlException.getMessage(), "Databse error",
										JOptionPane.ERROR_MESSAGE);
								
								try	{
									tableModel.setQuery(DEFAULT_QUERY);
									queryArea.setText(DEFAULT_QUERY);
								} 
								catch (SQLException sqlException2)	{
									JOptionPane.showMessageDialog(null, sqlException2.getMessage(),
											"Database error", JOptionPane.ERROR_MESSAGE);
								
								tableModel.disconnectFromDatabase();
								
								System.exit(1);
								}//end innercatch
							}//end outercatch
						}//end actionPerformed
					}//end ActionListener
		);//end submitButton.addActionListener
	
		setSize( 500, 250);
		setVisible( true);
		}//end try
		
		catch (SQLException sqlException)	{
			JOptionPane.showMessageDialog(null, sqlException.getMessage(), 
					"Database Error", JOptionPane.ERROR_MESSAGE);
					
					tableModel.disconnectFromDatabase();
			
					System.exit(1);
		}
		
		catch (
		setDefaultCloseOperation(DISPOSE_ON_CLOSE);
		
		addWindowListener(	
				new WindowAdapter()	{
					public void windowClosed( WindowEvent event)	{
						tableModel.disconnectFromDatabase();
						System.exit(0);
					}
				}
				);
	}
	
	public static void main(String args[])	{
	
		new DisplayQueryResults();
		
	}

}

```

```

import java.sql.*;
import javax.swing.table.AbstractTableModel;

public class ResultSetTableModel extends AbstractTableModel 	{
	
	private Connection connection;
	private Statement statement;
	private ResultSet resultSet;
	private ResultSetMetaData metaData;
	private int numberOfRows;
	
	private boolean connectedToDatabase = false;
	
	public ResultSetTableModel(String driver, String url, String username, String password, String query) 
			throws ClassNotFoundException, SQLException		{
		Class.forName( driver );
		
		connection = DriverManager.getConnection(url, username, password);
		
		statement = connection.createStatement( ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_READ_ONLY);
		
		connectedToDatabase	= true;
		
		setQuery(query);
	}
	
	public Class getColumnClass(int column) throws 	IllegalStateException	{
		
		if (!connectedToDatabase)
			throw new IllegalStateException("Not Connected to Database");
		
		try {
			String className = metaData.getColumnClassName( column + 1);
			return Class.forName( className);
		}
		catch (Exception exception)	{
			exception.printStackTrace();
		}
		
		return Object.class;
	}
	
	public int getColumnCount()	throws IllegalStateException	{
		if (!connectedToDatabase)	
			throw new IllegalStateException("Not Connected to Database");
		
		try {	
			return metaData.getColumnCount();
		}
		catch (SQLException sqlException)	{
			sqlException.printStackTrace();
		}
		
		return 0;
	}
	
	public String getColumnName(int column)	throws IllegalStateException	{
		if (!connectedToDatabase)	{
			throw new IllegalStateException("Not connected to Db");
		}
		
		try	{
			return metaData.getColumnName( column + 1);
		}
		
		catch (SQLException sqlException)	{
			sqlException.printStackTrace();
		}
		
		return "";
	}
	
	public int getRowCount()	throws IllegalStateException	{
		if (!connectedToDatabase)
			throw new IllegalStateException( "Not Connected to Database");
		
		return numberOfRows;	
	}
	
	public Object getValueAt(int row, int column)	throws IllegalStateException	{
		if (!connectedToDatabase)	
			throw new IllegalStateException( "Not Connected to Database");
		
		try 	{
			resultSet.absolute( row + 1);
			return resultSet.getObject(column + 1);
		}
		catch (SQLException	sqlException)	{
			sqlException.printStackTrace();
		}
		
		return "";
	}
	
	public void setQuery( String query)	throws IllegalStateException, SQLException	{
		if(!connectedToDatabase)	
			throw new IllegalStateException( "Not Connected to Database");	
		
		resultSet = statement.executeQuery(query);
			
		metaData = resultSet.getMetaData();
		
		resultSet.last();
		numberOfRows = resultSet.getRow();
		
		fireTableStructureChanged();           
	}
	
	public void disconnectFromDatabase()	{
		if(!connectedToDatabase)
			throw new IllegalStateException( "Not Connected to Database");
		
		try {
			statement.close();
			connection.close();
		}
		
		catch (SQLException sqlException)	{
			sqlException.printStackTrace();
		}
		
		finally {
			connectedToDatabase = false;
		}
	}
}

```
This is what happens when I try to compile it.

```

disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac DisplayQueryResults.java 
DisplayQueryResults.java:42: unreported exception java.lang.ClassNotFoundException; must be caught or declared to be thrown
			tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL, 

```		             ^

I am not really familiar with java because I came from a C++ background. Why is the class not found at the first place? Is there anyway that I can "import" like #include "file.cpp" as in C++?
I read somewhere that the java compiler automatically looks at the compiler directory for all the classes not defined in the main file scope, so why is the compiler complaining about a class not found?

Also, someone mentioned that I need to include a ClassNotFoundException: my question is if I DO CATCH classnotfoundexception, that means the rest part of my try code is will not be executed? Why is there a classnotfoundexception at the first place? I don't believe catching it will solve the problem since that' s just avoiding the problem.

If I should put in a catch exception part, where do I put it?

Thx

---

### Post by disappearedng on 2008-10-10
Anyone here?

---

### Post by apetresc on 2008-10-10
After the catch(SQLException) block, try adding another catch block for generic exceptions, like
```

catch (Exception e) {
     System.err.println(e.getMessage());
     System.exit(-1);
}
```

---

### Post by disappearedng on 2008-10-10
Which file,
I have a few SQLExceptions.

BTW, Why will adding a catch solve my problem? Doesn't the problem lie within the compiler not being able to resolve the Undefined class issue?

---

### Post by apetresc on 2008-10-11
> **disappearedng said:**
> Which file,
I have a few SQLExceptions.


Obviously the file containging the line "tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL," :P That's DisplayQueryResults.java .

> BTW, Why will adding a catch solve my problem? Doesn't the problem lie within the compiler not being able to resolve the Undefined class issue?

Nope. The compiler is not actually reporting a ClassNotFoundException... it's merely reporting that one of your lines (line 42 of DisplayQueryResults.java to be exact) COULD throw that exception and you have to deal with it (either by catching it or by adding "throws ClassNotFoundException" to the signature of the calling method).

Hope that clarifies things for you!

---

