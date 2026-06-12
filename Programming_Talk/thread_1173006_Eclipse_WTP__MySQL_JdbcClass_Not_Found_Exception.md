---
title: "Eclipse WTP | MySQL Jdbc:Class Not Found Exception"
date: 2009-05-29
forum: Programming Talk
---

### Post by bkarjala0001 on 2009-05-29
I use the Eclipse IDE. It first IDE I was introduced to when I started to learn programming (which wasn't that long ago) and I like it. Stick to what you know, right? Now, I've exhausted all my resources and spent countless hours searching similar form posts trying to extract meaningful information(nobody like reading nonsensical posts when they are troubleshooting). My only option start a new thread. I've carefully documented the steps that have gotten me this far. So, you can bet your backside that when I've everything working I'll post informative detailed descriptive how-to back to the community.

Anyway, I need help making my jsp page access a mySQL database. I'm pretty confident in creating jsp pages that's not the issue. I've been getting the following Class not found error:

```

org.apache.jasper.JasperException: javax.servlet.ServletException: java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:522)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:398)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)


```

I've set up the mySQL server. I've run apt-get install libmysql-java to install the database driver. I've followed the instructions in the following tutorial to configure the Jdbc driver: 

[https://help.ubuntu.com/community/JDBCAndMySQL]("https://help.ubuntu.com/community/JDBCAndMySQL"). 

Downloaded the drivers from the mySQL website and added the .jars to the build path:

[IMG]http://bkarjala0001.tripod.com/buildpathproof.png[/IMG]

So here's the lines that I added to bashrc:
```

# add the jdbc driver to the class path
export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.1.6.jar

```

Ok here's the Java class that loads the Jdbc driver:

```

package weightTrackerPackage;

//Import Statements
import java.sql.*;
import java.util.*;

public class WeightTrackerDAO {

//	Declare Variables
	private final String sourceName = "WeightTrackerDAO.java";
	private final String jdbcDriverName = "com.mysql.jdbc.Driver";
	private final String databaseURL = "jdbc:mysql://127.0.0.1:3306/weightTracker";

	private Connection dbConnection;
	private Statement statement;
	private ResultSet resultset;
	
/**
 * a) declares variables
 * b) loads database driver
 * c) opens a connection to the database
 * d) takes values from query result set and adds them to vector
 * @return
 * @throws Exception
 */
	public Vector<Weight> getWeightTable() throws Exception {
	// a)
		Vector <Weight> weightResults = new Vector <Weight>();
		Weight weightValues;
	 
		try {
	// b)
			loadJdbcDriver();
	// c)
			dbConnection = DriverManager.getConnection(databaseURL, "root", "password");
			statement = dbConnection.createStatement();
	// d)
			resultset = statement.executeQuery("SELECT * FROM weight");
			while (resultset.next()){
				weightValues = new Weight();
				weightValues.setWeight_entry_id(resultset.getInt("weight_entry_id"));
				weightValues.setEntry_ts(resultset.getString("entry_ts"));
				weightValues.setWeight_value(resultset.getDouble("weight_value"));
				weightResults.add(weightValues);
			}
			resultset.close();
			statement.close();
			dbConnection.close();
			return weightResults;
		}
		catch (SQLException sqle){
			throw sqle;
		}
		catch (Exception e){
			throw e;
		}
		
	}
	public void loadJdbcDriver() throws Exception {
		try {
			Class.forName(jdbcDriverName);
			System.out.println("!!!Success!!!");
			return;
		}
		catch (Exception e){
			System.out.println("*************** JDBC ERROR ************");
			System.out.println("Source: "+ sourceName);
			System.out.println("Message: Could not load the JDBC driver " + jdbcDriverName);
			throw e;
		}
	}

}

```

Well there you go. I think I covered just about every angle I could. It's the weirdest problem, I've defined the location of the driver so many places and still "no cigar!" Hopefully there's an intelligent individual out there that can divine a simple solution from the mess that I posted above. Thanks in advance.

PS. I'm using Jaunty, I'm using sun-java6-jdk, and I've installed Eclipse WTP manually.

:KS The age of enlightenment is here I've discovered Ubuntu!!! :KS

---

### Post by myrtle1908 on 2009-05-29
Just a guess ... have you tried adding the connector **binary** to your classpath ie. mysql-connector-java-5.1.7-bin.jar?

---

### Post by bkarjala0001 on 2009-05-30
Well I tried adding the bin to the class path and it didn't work. My Class path now consist of the lines of code I've pasted below.

I added the following line to /home/<username>/.bashrc

```

CLASSPATH=$CLASSPATH:/home/jokeri/opt/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.jar

```

Check the syntax of all the lines that I've added to /home/<username>/.bashrc
```

# add the jdbc driver to the class path
CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.1.6.jar
CLASSPATH=$CLASSPATH:/home/jokeri/opt/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.jar
export CLASSPATH

```

Also, check the syntax of the code that I've added to /etc/environment

```

CLASSPATH=".:/usr/share/java/mysql.jar"

```

When I execute "echo $CLASSPATH" I am prompted with the following result.

```

.:/usr/share/java/mysql.jar:/usr/share/java/mysql-connector-java-5.1.6.jar:/home/jokeri/opt/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.jar

```

Thanks anyway. It's all a very fun exercise for a beginner.

---

### Post by bkarjala0001 on 2009-06-01
I'll once again post the error message. In the example above I only posted the first part. In this post I'll post the message in it's entirety. I wouldn't mind getting a little help on this one it's giving me a headache. 

```

exception

org.apache.jasper.JasperException: javax.servlet.ServletException: java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:522)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:398)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)

root cause

javax.servlet.ServletException: java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
	org.apache.jasper.runtime.PageContextImpl.doHandlePageException(PageContextImpl.java:852)
	org.apache.jasper.runtime.PageContextImpl.handlePageException(PageContextImpl.java:781)
	org.apache.jsp.weightTrackerIndex_jsp._jspService(weightTrackerIndex_jsp.java:91)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:374)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)

root cause

java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1387)
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1233)
	java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	java.lang.Class.forName0(Native Method)
	java.lang.Class.forName(Class.java:169)
	weightTrackerPackage.WeightTrackerDAO.loadJdbcDriver(WeightTrackerDAO.java:61)
	weightTrackerPackage.WeightTrackerDAO.getWeightTable(WeightTrackerDAO.java:33)
	org.apache.jsp.weightTrackerIndex_jsp._jspService(weightTrackerIndex_jsp.java:71)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:374)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)


```

---

### Post by bkarjala0001 on 2009-06-06
No thoughts, comments, suggestions? I'm still struggling with the problem.

---

### Post by xpapad on 2009-07-29
You have probably solved it by now, but here you are: The problem is that you have to include your JDBC driver to your war file, and the right place to do that is in the WebContent/WEB-INF/lib directory. To do that:


[LIST]
[*]Right click on the WebContent/WEB-INF/lib directory, select Import...
[*]As a file type, use General -> Filesystem
[*]Select the directory of your JDBC jar file (/usr/share/java in ubuntu) and press OK
[*]Find the right file (mysql-connector-java-5.1.6.jar or so), check it. Make sure it will be copied to WebContent/WEB-INF/lib
[*]Restart Tomcat, and you're set.
[/LIST]

---

### Post by bkarjala0001 on 2009-08-04
:D Awesome thanks for the help! :D Alright, when I get around to it I'll give this solution a try. It's been so long that I've started a different project.

---

### Post by mathheadinclouds on 2010-02-23
That solution worked for me! 

The weirdest thing: I had the driver.forname thing in one .java file, that only had a main, and while I had the path to the driver only under project settings, and I would right click on that file with the main method, it would work, but when I tried it with the jsp file (right click, "run on server"), it would say "driver not found", although the jsp would just call the into the same class with that main file, that would work if invoked directly. Very very strange.

Thank you for the solution!!:D

---

