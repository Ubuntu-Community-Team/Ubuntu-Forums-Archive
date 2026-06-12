---
title: "problem connecting to mySQL driver using java."
date: 2009-04-30
forum: Programming Talk
---

### Post by ggankhuy on 2009-04-30
I got the following code below: 
Can someone help me?

import java.sql.*;

public class Connect 
{
	public static void main(String[] args)
	{
		Connection conn = null;
		String url = "jdbc:mysql://localhost/cookbook";
		String userName = "cbuser";
		String password = "cbpass";
		
		try
		{
			Class.forName("com.mysql.jdbc.Driver").newInstance();
			conn = DriverManager.getConnection(url, userName, password);
			System.out.println("Connected");
		}
		catch (Exception e)
		{
			
			System.err.println("Cannot connect to server: " + e.getLocalizedMessage());
			System.err.println(e.getMessage());
			System.err.println(e.toString());
			System.err.println(e.getCause());
		}
		finally
		{
			if (conn != null)
			{
				try
				{
					conn.close();
					System.out.println("Disconnected");
				}
				catch (Exception e)
				{
					System.out.println("Warning: Failure closing");
				}
			}
		}
	}

}


PROGRAM OUTPUT:::

root@tester-laptop:~/workspace/Connect# java Connect
Cannot connect to server: com.mysql.jdbc.Driver
com.mysql.jdbc.Driver
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
null

---

### Post by sujoy on 2009-04-30
set the classpath to point to the mysql-connector-java jar file

---

### Post by ggankhuy on 2009-04-30
thanks for letting me know.
now the problem is that file is not present anywhere in my file system.
wonder what package i had to install to get the damn file. I tried bunch of packages with no avail.

---

### Post by MeLight on 2009-04-30
[http://dev.mysql.com/downloads/connector/j/3.0.html]("http://dev.mysql.com/downloads/connector/j/3.0.html")

Inside the .zip you'll find a jar file

---

### Post by The Cog on 2009-04-30
The easiest thing to do is to drop the jar file in JRE lib/ext folder. Then it's always available and you don't have to fanny around with classpaths.

---

