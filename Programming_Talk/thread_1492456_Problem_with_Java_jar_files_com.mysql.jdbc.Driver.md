---
title: "Problem with Java jar files com.mysql.jdbc.Driver"
date: 2010-05-24
forum: Programming Talk
---

### Post by peterv6 on 2010-05-24
I'm running Kubuntu 10.04, and have java 1.6 installed.  I can compile and run "hello world" types of programs, but when I attempt to compile a program using jdbc, I keep getting this error:
```
Mon May 24 18:28:55 EDT 2010                                                                                                        
~/java ->                                                                                                                           
peterv@MBP17K10<2200>$: javac db_select_test.java                                                                                   
[COLOR="Red"][B]db_select_test.java:19: cannot find symbol                                                                                          
symbol  : class Statement                                                                                                           
location: class db_select_test                                                                                                      
               Statement s = conn.createStatement ();                                                                               
               ^                                                                                                                    
db_select_test.java:21: cannot find symbol                                                                                          
symbol  : class ResultSet [/B][/COLOR]                                                                                                          
location: class db_select_test                                                                                                      
               ResultSet rs = s.getResultSet ();                                                                                    
               ^                                                                                                                    
2 errors                                       
```

The source code is (problem is hilighted):
```

import java.sql.*;
   public class jdbc11
   {
       public static void main (String[] args)
       {
           Connection conn = null;

           try
           {
               String userName = "peterv";
               String password = "jclark";
               String url = "jdbc:mysql://localhost/test";
               **[COLOR="Red"]Class.forName ("com.mysql.jdbc.Driver").newInstance ();[/COLOR]**
               conn = DriverManager.getConnection (url, userName, password);
               System.out.println ("Database connection established");
           }
           catch (Exception e)
           {
        	   e.printStackTrace();
               System.err.println ("Cannot connect to database server");
           }
           finally
           {
               if (conn != null)
               {
                   try
                   {
                       conn.close ();
                       System.out.println ("Database connection terminated");
                   }
                   catch (Exception e) { /* ignore close errors */ }
               }
           }
       }
   }




```

I know there's a problem with the classpath.  I set it to where the .jar file (hilighted) is but it doesn't seem to work:
```

peterv@MBP17K10<2193>$: **[COLOR="Red"]echo $CLASSPATH[/COLOR]**                                                                                             
**[COLOR="Red"][COLOR="Red"]/usr/bin/java/jdk1.6.0_20/lib:.   [/COLOR][/COLOR]**                                                                                                                                
Mon May 24 19:01:40 EDT 2010                                                                                                        
~/java ->                                                                                                                           
peterv@MBP17K10<2194>$: cd /usr/bin/java/jdk1.6.0_20/lib                                                                            
                                                                                                                                    
Mon May 24 19:01:40 EDT 2010                                                                                                        
/usr/bin/java/jdk1.6.0_20/lib ->                                                                                                    
peterv@MBP17K10<2195>$: lsx                                                                                                         
total 31M                                                                                                                           
drwxr-xr-x  3 root 4.0K 2010-05-24 18:42 .                                                                                          
drwxr-xr-x 10 root 4.0K 2010-05-24 18:42 ..                                                                                         
-rw-r--r--  1 root  15M 2010-04-12 17:23 ct.sym                                                                                     
-rw-r--r--  1 root 143K 2010-04-12 17:24 dt.jar                                                                                     
-rw-r--r--  1 root 202K 2010-04-12 17:30 htmlconverter.jar                                                                          
-r--r--r--  1 root  18K 2010-04-12 17:23 ir.idl                                                                                     
-rw-r--r--  1 root 385K 2010-04-12 17:23 jconsole.jar                                                                               
-rwxr-xr-x  1 root  17K 2010-04-12 17:23 jexec                                                                                      
-rw-r--r--  1 root 737K 2010-05-23 20:18 [COLOR="Red"]**mysql-connector-java-5.1.10.jar **[/COLOR]                                                           
-r--r--r--  1 root  429 2010-04-12 17:23 orb.idl                                                                                    
-rw-r--r--  1 root 2.3M 2010-04-12 17:23 sa-jdi.jar                                                                                 
-rw-r--r--  1 root  13M 2010-05-07 02:22 tools.jar                                                                                  
drwxr-xr-x  6 root 4.0K 2010-04-12 19:13 visualvm         

```

This is driving me nuts!  Any help would be greatly appreciated!

---

### Post by Some Penguin on 2010-05-24
Add the entire .jar name to the CLASSPATH variable.
Or unpack the jar.

---

### Post by r-senior on 2010-05-24
The errors you are getting are concerned with the java.sql.Statement and java.sql.ResultSet interfaces. These are part of the JDBC API itself, which doesn't come with the JDBC driver. The JDBC driver is just the database specific parts.

You'll find Statement and ResultSet in rt.jar, which you'll probably find in /usr/bin/java/jdk1.6.0_20/jre/lib, along with a load of others that you may need in the future.

Try adding /usr/bin/java/jdk1.6.0_20/jre/lib/rt.jar, or even ...jre/lib/* into your $CLASSPATH?

---

### Post by GregBrannon on 2010-05-24
In Java, the java source file name has to be the same as the main class of the source file.  I believe the errors are telling you that a class named "db_select_test" cannot be found in your java source file.

---

### Post by peterv6 on 2010-05-24
Greg,
You are correct, however that's not the error.  I mistakenly copied in the wrong source code.  The actual source code causing the problem is this:
```

import java.sql.Connection;
import java.sql.DriverManager;

   public class db_select_test
   {
       public static void main (String[] args)
       {
           Connection conn = null;

           try
           {
               String userName = "";
               String password = "";
               String url = "jdbc:mysql://localhost/test";
               Class.forName ("com.mysql.jdbc.Driver").newInstance ();
               conn = DriverManager.getConnection (url, userName, password);
               System.out.println ("Database connection established");
//
               Statement s = conn.createStatement ();
               s.executeQuery ("SELECT id, name, category FROM animal");
               ResultSet rs = s.getResultSet ();
               int count = 0;
               while (rs.next ())
               {
                   int idVal = rs.getInt ("id");
                   String nameVal = rs.getString ("name");
                   String catVal = rs.getString ("category");
                   System.out.println (
                           "id = " + idVal
                           + ", name = " + nameVal
                           + ", category = " + catVal);
                   ++count;
               }
               System.out.println (count + " rows were retrieved");
               rs.close ();
               s.close ();               
//
           }
           catch (Exception e)
           {
        	   e.printStackTrace();
               System.err.println ("Cannot connect to database server");
           }
           finally
           {
               if (conn != null)
               {
                   try
                   {
                       conn.close ();
                       System.out.println ("Database connection terminated");
                   }
                   catch (Exception e) { /* ignore close errors */ }
               }
           }
       }
   }


```

---

### Post by peterv6 on 2010-05-24
R-Senior,
I tried your solution, but still get the same errors.  I set the class path as follows:
```

Mon May 24 22:12:56 EDT 2010                                                                                                        
~/java ->                                                                                                                           
peterv@MBP17K10<2320>$: echo $CLASSPATH                                                                                             
/usr/bin/java/jdk1.6.0_20/jre/lib  

```
This directory contains the following files:
```

Mon May 24 22:12:56 EDT 2010                                                                                                        
/usr/bin/java/jdk1.6.0_20/jre/lib ->                                                                                                
peterv@MBP17K10<2314>$: lsx *.jar                                                                                                   
-rw-r--r-- 1 root  67K 2010-04-12 17:20 alt-rt.jar                                                                                  
-rw-r--r-- 1 root 6.6M 2010-05-07 02:22 charsets.jar                                                                                
-rw-r--r-- 1 root 3.2M 2010-05-07 02:22 deploy.jar                                                                                  
-rw-r--r-- 1 root 884K 2010-05-07 02:22 javaws.jar                                                                                  
-r--r--r-- 1 root  87K 2010-04-12 16:58 jce.jar                                                                                     
-rw-r--r-- 1 root 608K 2010-05-07 02:22 jsse.jar                                                                                    
-rw-r--r-- 1 root  382 2010-04-12 17:04 management-agent.jar                                                                        
-rw-r--r-- 1 root 737K 2010-05-23 20:25 [COLOR="Red"]**mysql-connector-java-5.1.10.jar **[/COLOR]                                                            
-rw-r--r-- 1 root 1.8M 2010-05-07 02:22 plugin.jar                                                                                  
-rw-r--r-- 1 root 1.1M 2010-04-12 17:23 resources.jar                                                                               
-rw-r--r-- 1 root  50M 2010-05-07 02:22 [COLOR="Red"]**rt.jar **[/COLOR]            



```
And I still get these errors.  Any ideas?
```

Mon May 24 22:12:56 EDT 2010                                                                                                        
~/java ->                                                                                                                           
peterv@MBP17K10<2322>$: [COLOR="Red"]**javac db_select_test.java **[/COLOR]                                                                                  
db_select_test.java:19: cannot find symbol                                                                                          
symbol  : class Statement                                                                                                           
location: class db_select_test                                                                                                      
               Statement s = conn.createStatement ();                                                                               
               ^                                                                                                                    
db_select_test.java:21: cannot find symbol                                                                                          
symbol  : class ResultSet                                                                                                           
location: class db_select_test                                                                                                      
               ResultSet rs = s.getResultSet ();                                                                                    
               ^                                                                                                                    
2 errors                                                                                                                            
                                                                                                                                    
Mon May 24 22:12:56 EDT 2010                                                                                                        
~/java ->                                                                                                                           
peterv@MBP17K10<2323>$: [COLOR="Red"]**javac -cp /usr/bin/java/jdk1.6.0_20/jre/lib db_select_test.java**[/COLOR]                                       
db_select_test.java:19: cannot find symbol                                                                                          
symbol  : class Statement                                                                                                           
location: class db_select_test                                                                                                      
               Statement s = conn.createStatement ();                                                                               
               ^                                                                                                                    
db_select_test.java:21: cannot find symbol                                                                                          
symbol  : class ResultSet                                                                                                           
location: class db_select_test                                                                                                      
               ResultSet rs = s.getResultSet ();                                                                                    
               ^                                                                                                                    
2 errors                                                                                                                            
                                                                                                                                    
Mon May 24 22:12:56 EDT 2010

```

---

### Post by nmccrina on 2010-05-24
Don't use Class.forName.

I've been experimenting with jdbc myself recently, and came up with this working example:

```

package org.mccrina.recipe.prototypes;

import java.sql.*;

public class Driver
{
	public static void main(String[] args)
	{
		Connection conn = null;
		Statement stmt = null;
		ResultSet rslt = null;
		
		try
		{
			conn = DriverManager.getConnection("jdbc:mysql://127.0.0.1", "testuser", "test");
			stmt = conn.createStatement();
			rslt = stmt.executeQuery("SELECT * FROM testdb.stock;");
			
			while (rslt.next())
			{
				System.out.println("Name: " + rslt.getString("name"));
				System.out.println("Price: " + rslt.getDouble("price"));
				System.out.println("Quantity: " + rslt.getInt("quantity") + "\n");
			}
		}
		catch (SQLException sqlEx)
		{
			System.out.println(sqlEx.getMessage());
			return;
		}
		finally
		{
			try
			{
				if (rslt != null)
				{
					rslt.close();
				}
			}
			catch (Exception ex)
			{
				System.out.println("Error closing result set");
			}
			try
			{
				if (stmt != null)
				{
					stmt.close();
				}
			}
			catch (Exception ex)
			{
				System.out.println("Error closing statement");
			}
			try
			{
				if (conn != null)
				{
					conn.close();
				}
			}
			catch (Exception ex)
			{
				System.out.println("Error closing connection");
			}
		}
	}
}

```

Apparently Class.forName is deprecated, the JRE will automagically find the correct driver when you initialize the connection with DriverManager.getConnection().

Incidentally, I highly recommend using Eclipse and adding /usr/share/java/mysql.jar to the project as an external library, it eliminates all messing with CLASSPATH and is just all-around easier :)

Oh, and /usr/share/java/mysql.jar IS the .jar you need to have in your CLASSPATH, if you still want to do it manually.

---

### Post by Some Penguin on 2010-05-24
I don't see your imports in the second Java file.

---

### Post by peterv6 on 2010-05-25
SP,

Not sure what you're referring to.  If you look at the db_test_select file, you'll see these import statements as the first two lines:

import java.sql.Connection;
import java.sql.DriverManager;

If that's not what you're referring to, please clarify.

---

### Post by peterv6 on 2010-05-25
nmccrina,
Thanks for the information!  I used your code as a model, and I got mine working.  I'm a java newbie, so I'll have to look up a lot of the things in the code to make sure I understand it correctly, but you've given me a great head start!
Peter V.

---

### Post by Some Penguin on 2010-05-25
> **peterv6 said:**
> SP,

Not sure what you're referring to.  If you look at the db_test_select file, you'll see these import statements as the first two lines:

import java.sql.Connection;
import java.sql.DriverManager;

If that's not what you're referring to, please clarify.

Isn't it obvious, considering that the error messages you were getting refer to Statement and ResultSet?

---

### Post by peterv6 on 2010-05-25
SP,
No, obviously it isn't obvious!  Shouldn't it be obvious to *you* that I don't know much about the import statements?  I'm a complete newbie to java, and I'm attempting to learn it on my own.  If you want to help, great.  Maybe you have always known everything about java, and have never had simple questions.  If so, I'm impressed, but if you feel you are too important to help out, don't bother replying with obnoxious comments, they're not appreciated.

---

