---
title: "java - oracle connection"
date: 2010-11-21
forum: Programming Talk
---

### Post by kartabosh on 2010-11-21
hi guys
i'm trying to get java to connect to my oracle xe database but i'm having difficulties in doing so 
here's my code 
```
	static void Connect(){
		Connection connection = null;
		try {
		    // Load the JDBC driver
		    String driverName = "oracle.jdbc.driver.OracleDriver";
		    Class.forName(driverName);

		    // Create a connection to the database
		    String serverName = "127.0.0.1";
		    String portNumber = "1521";
		    String sid = "orcl";
		   // String url = "jdbc:oracle:thin:@" + serverName + ":" + portNumber + ":" + sid;
		    String url = "jdbc:oracle:thin:@127.0.0.1:1521:orcl";
		    String username = "ali";
		    String password = "bacbac";
		    connection = DriverManager.getConnection(url, username, password);
		} catch (ClassNotFoundException e) {
		    System.out.println("1");
			// Could not find the database driver
		} catch (SQLException e) {
			System.out.println("2");
			// Could not connect to the database
		}
	}

```
when i debug i noticed it fails this line
 String driverName = "oracle.jdbc.driver.OracleDriver";
and it returns 1 the ClassNotFoundException 
anyone have any idea on how to fix this?

---

### Post by Some Penguin on 2010-11-22
Ensure that 

(1) you've actually downloaded the Oracle JDBC drivers, and
(2) you've installed the jar(s) and set the CLASSPATH to include the location, and
(3) you've installed any dependencies those drivers may have.

ClassNotFoundException is an extremely informative name -- it can't find the class file that you're asking it for, either because you didn't get the driver or you haven't told Java where to find it.

---

### Post by kartabosh on 2010-11-22
strange that i can't find any website describing what the problem is for a noob such as myself
anyway after messing around for like 16 hours trying to find out what the problem was i finally got a good error from java informing me that there is no driver located at "/usr/lib/jvm/java-6-openjdk/jre/lib/ext" 
so with that in mind i went to oracle.com and downloaded the driver namely [http://www.oracle.com/technetwork/database/enterprise-edition/jdbc101040-094982.html](http://www.oracle.com/technetwork/database/enterprise-edition/jdbc101040-094982.html)
and placed it in that folder and voilla! it works

thanks penguin guy

---

