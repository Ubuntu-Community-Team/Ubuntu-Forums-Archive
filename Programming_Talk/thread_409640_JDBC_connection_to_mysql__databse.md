---
title: "JDBC connection to mysql  databse"
date: 2007-04-14
forum: Programming Talk
---

### Post by jimmyjean on 2007-04-14
Hi,

I am having trouble connecting to a mysql database from a current java project. The driver loads correctly but an sql exception is thrown when the driver tries to connect to the database. I get the following message:
  
  Exception in thread "main" java.sql.SQLException: Access denied for user ''@'localhost'   (using password: NO) 

I have tried using my username and password in the url but i am still denied access to the database. To run mysql in ubuntu you have to sudo first. Is this going to be an issue with accessing a database from a Java class? 

Here is a snippet of code below,

// Load driver
Class.forName(driver);
System.out.println("Driver loaded.");
			
// Connect to database
Connection connection = DriverManager.getConnection(url);
System.out.println("Connection established.");

Thanks

Jim

---

### Post by phossal on 2007-04-15
Maybe try something like this:

```
	//DATABASE VARIABLES
	String database = "<YOUR DATABASE>";
	String user 	   = "root";
	String password = "<YOUR PASSWORD>";
	String host	   = "localhost"; //By default
	
	public Connection 	con;

	public boolean connect() {	
		try {
			
			Class.forName("com.mysql.jdbc.Driver").newInstance();
			con = DriverManager.getConnection("jdbc:mysql://"+host+"/"+database+"?user="+user+"&password="+password);
			//Set connectionStatus
			
			return true;
		} catch (Exception E) {
			return false;
		}
	}
```

You can get the required .jar file from mysql.com.

---

### Post by jimmyjean on 2007-04-15
Thanks for the advice. I tried using root and the system password but still couldn't get anywhere. I have tried changing the permissions on the mysql executable and the databse but I can't because root is the owner. I have tried $sudo chmod u+wrx mysql but it seems to have no effect.

---

### Post by phossal on 2007-04-15
This demonstrates a working connection. It requires no user administration, no personal database. It only requires that you've installed mysql-client and mysql-server as Ubuntu Packages, and that you've downloaded the .jar file from MySQL.com and put it in your /path_to_java/jre/lib/ext folder.

Example: You just installed Ubuntu. You just ran: sudo apt-get install mysql-client mysql-server. You downloaded Java. You downloaded eclipse. You downloaded [mysql-connector-java-5.0.3-bin.jar]("http://dev.mysql.com/downloads/connector/j/5.1.html"), and put it in your classpath. Then you can run this class and connect. It's a working example. You don't need to change any variables to test a connection.

```

import java.sql.*;



public class JMySQL {
	
	//DATABASE VARIABLES
	String database = "mysql";
	String user = "root";
	String password = "";
	String host = "localhost"; //By default

	public Connection 	con;
	
	public boolean connect() {	
		try {
			
			Class.forName("com.mysql.jdbc.Driver").newInstance();
			con = DriverManager.getConnection("jdbc:mysql://"+host+"/"+database+"?user="+user+"&password="+password);
			//Set connectionStatus
			
			return true;
		} catch (Exception E) {
			return false;
		}
	}
	
	
	public static void main(String args[]) {
		JMySQL db = new JMySQL();
		System.out.println("Connected: "+db.connect());
	}
	
	/* Running this class will connect to a MySQL database on Ubuntu Edgy. 
	 * INSTALLING MYSQL
	 * ------------------
	 * MySQL is installed at the command line like this:
	 * sudo apt-get install mysql-client mysql-server
	 * 
	 * Before you create a database, the only user is root, and the default database is MySQL
	 * 
	 * INSTALLING MySQL-CONNECTOR
	 * -------------------
	 * MySQL.com makes a .jar file available to use to connect to MySQL from Java. The name of 
	 * the .jar file is something like: mysql-connector-java-5.0.3-bin.jar
	 * 
	 * Put mysql-connector-java-5.0.3-bin.jar in your <PATH_TO_JAVA>/jre/lib/ext/ folder.
	 * 
	 * Restart eclipse, and run this class. 
	 */
	
	
}

```

---

### Post by phossal on 2007-04-15
> **jimmyjean said:**
> Thanks for the advice. **[COLOR="Red"]I tried using root and the system password[/COLOR]** but still couldn't get anywhere. I have tried changing the permissions on the mysql executable and the databse but I can't because root is the owner. I have tried $sudo chmod u+wrx mysql but it seems to have no effect.

I don't know what you've done with your DB. I suggest using the class in my previous post to see if you can get connected at all. Unless you've set a password for root on MySQL (or you're connecting as another user which you have previously set up within MySQL), there *isn't* a password. I pass it as a null value when connecting as root. 

The beauty of the class I've included for you is that MySQL installs on Edgy with the MySQL database (and root user) already configured. That means, if you just *install correctly*, which is pretty straightforward, it will connect to the MySQL database called *mysql* as the *root* user.

---

### Post by jimmyjean on 2007-04-15
Thanks, that's done it!! :D ! I was using root as user but also using a password. If I leave it as null it connects fine.

	public static void main(String[] args) throws SQLException {
		
		String driver = "com.mysql.jdbc.Driver";
		String url    = "jdbc:mysql://localhost/<my_database>?user=root";
		
		try {
			// Load driver
			Class.forName(driver);
			System.out.println("Driver loaded.");
			
			// Conect to database
			Connection connection = DriverManager.getConnection(url);
			System.out.println("Connection established.");
            
			// Close connection
			connection.close();
			System.out.println("Connection closed.");

		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		

	}

}

Thanks for your help!

---

### Post by phossal on 2007-04-15
> **jimmyjean said:**
> Thanks, that's done it!! :D ! I was using root as user but also using a password. If I leave it as null it connects fine. ... Thanks for your help!

You're welcome, of course. ;)

---

### Post by jimmyjean on 2007-04-15
On a slighty seperate issue. I have added mysql-connector-java-5.0.3-bin.jar to my classpath from within my eclipse project. I'm not quite sure how to permenantly change my classpath though. I originally used  $export CLASSPATH=$CLASSPATH:/<path_to_jar_file> but this doesn't seem to be a permanent change.

Thanks

---

### Post by phossal on 2007-04-15
I always put that file in the /ext folder of my JRE. There are other ways, but none I like more.

---

