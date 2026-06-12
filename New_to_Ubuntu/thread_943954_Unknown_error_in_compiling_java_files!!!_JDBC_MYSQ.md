---
title: "Unknown error in compiling java files!!! JDBC MYSQL"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by disappearedng on 2008-10-10
Hi everyone
I wrote two files, and I have connected to my mysql database using jdbc using another program and it has proven to be successful. So I don't think it has anything to do with my Environment.

File 1:
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
	
	public DisplayQueryResults()	{
		
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

file 2
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

this is what I have done in the terminal
[code]
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ ls
DisplayQueryResults.java  ResultSetTableModel.java
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac 
DisplayQueryResults.java  ResultSetTableModel.java  
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac DisplayQueryResults.java 
DisplayQueryResults.java:42: unreported exception java.lang.ClassNotFoundException; must be caught or declared to be thrown
                        tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL, 
                                     ^
1 error
[code]

Even though ResultSetTableModel is under the same directory, the compiler complains that it can't find it.

I am using mysql-connector-java-5.16 and everything has worked well.

Why

---

### Post by jemate18 on 2008-10-10
> **disappearedng said:**
> Hi everyone
I wrote two files, and I have connected to my mysql database using jdbc using another program and it has proven to be successful. So I don't think it has anything to do with my Environment.

File 1:
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
	
	public DisplayQueryResults()	{
		
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

file 2
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

this is what I have done in the terminal
[code]
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ ls
DisplayQueryResults.java  ResultSetTableModel.java
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac 
DisplayQueryResults.java  ResultSetTableModel.java  
disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac DisplayQueryResults.java 
DisplayQueryResults.java:42: unreported exception java.lang.ClassNotFoundException; must be caught or declared to be thrown
                        tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL, 
                                     ^
1 error
[code]

Even though ResultSetTableModel is under the same directory, the compiler complains that it can't find it.

I am using mysql-connector-java-5.16 and everything has worked well.

Why

I think you must have the mysql-connector-j.jar on the same directory too

---

### Post by patrickballeux on 2008-10-10
Your TRY/Catch is not catching the ClassNotFoundException exception...  

The problem is not that your class is not found, it is because your are calling a method that can throw a "ClassNotFoundException". Simply add another catch(ClassNoFoundException cnfe) in your "Try...".

You will not be able to compile your code.

Good luck!

---

### Post by jemate18 on 2008-10-10
or you can just

```
catch(Exception ex){
   JOptionPane.showMessageDialog(this, ex);
}
```

In this way, 'you'll only have to do it once instead of

```
catch(ClassNotFoundException ex){
   JOptionPane.showMessageDialog(this, ex);
}
catch(SQLException ex){catch(Exception ex){
   JOptionPane.showMessageDialog(this, ex);
}

```

---

### Post by dhtseany on 2008-10-10
Not to be rude but in the future your questions might be bettered answered in the [Development and Programming Forums]("http://ubuntuforums.org/forumdisplay.php?f=310").

Peace
Sean

---

### Post by disappearedng on 2008-10-10
Where do I put the throwing? 

The compiler complains about this:
```

disappearedng@disappearedng-ubuntu-client:~/Desktop/Dev/testing$ javac DisplayQueryResults.java 
DisplayQueryResults.java:42: unreported exception java.lang.ClassNotFoundException; must be caught or declared to be thrown
			tableModel = new ResultSetTableModel( JDBC_DRIVER, DATABASE_URL, 
			             ^

```

I am not really familiar with java because I came from a C++ background. Why is the class not found at the first place? Is there anyway that I can "import" like #include "file.cpp" as in C++?
I read somewhere that the java compiler automatically looks at the compiler directory for all the classes not defined in the main file scope, so why is the compiler complaining about a class not found? 

Also, you mention that I need to include a ClassNotFoundException: my question is if I DO CATCH classnotfoundexception, that means the rest part of my try code is will not be executed? Why is there a classnotfoundexception at the first place? I don't believe catching it will solve the problem since that' s just avoiding the problem. 

If I should put in a catch exception part, where do I put it? 

Thx

---

### Post by disappearedng on 2008-10-10
Can anyone answer me? I am really stuck

---

### Post by dhtseany on 2008-10-11
Again, this is the Beginner Help forums for general help questions. Try the programming forums as people who are into programming hang around there.

Peace
Sean

---

### Post by The Cog on 2008-10-11
The problem is not that the class cannot be found. 

The problem is that a call to new ResultSetTableModel() **could possibly** throw a ClassNotFoundException. Now, ClassNotFoundException is a **checked exception** which means the compiler will not allow you to write code that ignores that possibility. As the compiler error says, you must re-write your code to deal witht that possibility. You can do this either by catching the exception (and presumably taking some appropriate action) or declaring that the method can throw that exception. Of course if you declare that your method can throw that exception, the compiler error then bubbles up to the next higher method. You must either catch the exception at some point, or keep on declaring that it can be thrown all the way back up to the outermost main() method.

This is a compiler error because you are trying to ignore a possible error that the language rules say you cannot ignore.  The error message  **must be caught or declared to be thrown** means exactly what it says.

This link should help:
[https://java.sun.com/docs/books/tutorial/essential/exceptions/catchOrDeclare.html](https://java.sun.com/docs/books/tutorial/essential/exceptions/catchOrDeclare.html)

---

