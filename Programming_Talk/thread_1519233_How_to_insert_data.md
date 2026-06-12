---
title: "How to insert data"
date: 2010-06-27
forum: Programming Talk
---

### Post by MughalShahzad on 2010-06-27
I am new in ubuntu 9.10, I had installed NetbeansIDE 6.7.1 from software centre and had installed mysql 5 using sudo apt-get install mysql-server.
I can create table, insert data into it and view data from Netbeans IDE using sql commands.

but when I code to insert data and debug pointer jumps to catch statement

CODE]
package insertingvalues;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class Main {

    public static void main(String[] args) {        
        try{
        String driver = "com.mysql.jdbc.Driver";
        Class.forName(driver);
        Connection con = DriverManager.getConnection("jdbc:mysql://", "root", "root");
        Statement st = con.createStatement();
        int val = st.executeUpdate("INSERT into mysql.Profile VALUES(" + 101 + "," + "Shahzad" + ")");
        System.out.println("1 row affected");
        }catch (Exception ex){
            System.out.println(ex.getMessage());
        }
    }

}
[/CODE]

what is wrong with it?
kindly suggest me
Thanks & Regards

---

### Post by Can+~ on 2010-06-27
> **MughalShahzad said:**
> ```
int val = st.executeUpdate("INSERT into mysql.Profile VALUES(" + 101 + "," + "**Shahzad**" + ")");
```

what is wrong with it?
kindly suggest me
Thanks & Regards

That SQL string should be marked as such, aka:

```
int val = st.executeUpdate("INSERT into mysql.Profile VALUES(" + 101 + "," + "'Shahzad'" + ")");
```

Btw, if all values are constant, then you can avoid doing that string addition. In fact, you should avoid concatenating strings and variables for this, there are other methods.

Unfortunately, I don't know much about java, but there should probably be some function for inserting which makes it cleaner, and possibly sanitize the input.

---

### Post by Some Penguin on 2010-06-28
Yes, avoiding the string concatenation by using prepared statements would be a good idea.

---

### Post by MughalShahzad on 2010-06-28
> **Some Penguin said:**
> Yes, avoiding the string concatenation by using prepared statements would be a good idea.

ok!

is there any problem with following?

String driver = "com.mysql.jdbc.Driver";
Connection con = DriverManager.getConnection("jdbc:mysql://", "root",  "root");


Regards
Shahzad

---

### Post by Javich on 2010-06-28
Yes, there is a problem with that, you're not loading the driver.

Think this may resolve your questions:

```

public class MySQLTest {

	
	public static void main(String[] args) throws Exception{
		
		Class.forName("com.mysql.jdbc.Driver");
		Connection con = DriverManager.getConnection( "jdbc:mysql://localhost/mydb", "root", "");
		
		String sql = "INSERT INTO users SET name=?";
		PreparedStatement ps = con.prepareStatement(sql);
		ps.setString(1, "username");
		if (ps.execute()){
			//Success, do something
		}else{
			//Insert failed, do something else
		}		
	}
	
}

```

---

### Post by MughalShahzad on 2010-06-28
I saw some examples on net and this code is also taken from there, no one mentioned this kind of requirement, please guide me how to do so.

Thanks & Regards
Shahzad

> **Javich said:**
> Yes, there is a problem with that, you're not loading the driver.

Think this may resolve your questions:

```

public class MySQLTest {

    
    public static void main(String[] args) throws Exception{
        
        Class.forName("com.mysql.jdbc.Driver");
        Connection con = DriverManager.getConnection( "jdbc:mysql://localhost/mydb", "root", "");
        
        String sql = "INSERT INTO users SET name=?";
        PreparedStatement ps = con.prepareStatement(sql);
        ps.setString(1, "username");
        if (ps.execute()){
            //Success, do something
        }else{
            //Insert failed, do something else
        }        
    }
    
}

```

---

### Post by MughalShahzad on 2010-06-29
I have done this in windows xp with following steps
mysql-connector.jar downloaded from internet
then copied into two locations
Java\jre1.6.0_06\lib
Java\jre1.6.0_06\lib\ext
restarted NetbeansIDE and that's all 




> **MughalShahzad said:**
> I saw some examples on net and this code is also taken from there, no one mentioned this kind of requirement, please guide me how to do so.

Thanks & Regards
Shahzad

---

### Post by Javich on 2010-06-29
Hey Mughal, 

Here is the explained code

```

public class MySQLTest {

    //You know what this is - Program entry point
    public static void main(String[] args) throws Exception{

        //The Following line searches for that Driver class in the whole classpath, if it doesn't find it, it will throw an exception
        Class.forName("com.mysql.jdbc.Driver");
        

        // Get's a connection, the URL format reference is at: http://dev.mysql.com/doc/refman/5.0/en/connector-j-reference-configuration-properties.html
Connection con = DriverManager.getConnection( "jdbc:mysql://localhost/mydb", "root", "");
        

        //This declares a SQL "Template" where the ? signs will be replaced by a type(int, String, double, etc)
        String sql = "INSERT INTO users SET name=?";


        //This prepares the connection to execute a query (or SQL Template) 
        PreparedStatement ps = con.prepareStatement(sql);
        
        //This substitutes the "?" sign in position one (the first one)  for "username"
        ps.setString(1, "username");

        //This one executes the actual query, returning true if succeeds or false if fails.
        if (ps.execute()){
            //Success, do something
        }else{
            //Insert failed, do something else
        }        
    }
    
}

```

That's the code explained, in order to make sure you have the MySQL JAR in the classpath, here is a nice tutorial that explains it on steps 1 to 5:

[http://www.linglom.com/2007/12/05/accessing-mysql-on-netbeans-using-jdbc-part-i-create-a-connection/]("http://www.linglom.com/2007/12/05/accessing-mysql-on-netbeans-using-jdbc-part-i-create-a-connection/")

Cheers
Javier

---

### Post by MughalShahzad on 2010-06-30
Thanks Javier

Actually I don't have any idea where to place the "mysql-connector-java-3.1.14-bin.jar" file in ubuntu 9.10.
yesterday I did this in xp successfully by placing this jar file at following locations

Java\jre1.6.0_06\lib
Java\jre1.6.0_06\lib\ext

If you have any idea that where would it be in ubuntu 9.10 please teach me.
Moreover, the jar file which I am using for xp; cab be used for ubuntu 9.10 or not if not kindly help me to get this too?

I am using NetbeansIDE 6.7.1 (installed from Software Center), MySQL 5 Server (sudo apt-get install mysql-server) is this enough?

Thanks & Regards
Shahzad

---

