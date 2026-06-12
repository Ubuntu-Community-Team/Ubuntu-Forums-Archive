---
title: "Setting up mysql and jdbc driver with java"
date: 2006-11-13
forum: Programming Talk
---

### Post by jinxen on 2006-11-13
I have been searching for a database solution, and i have decided to go with mysql and jdbc. So now im wondering if someone knows how to set-up these components with java (and installing them too).

Regards, Tommy

---

### Post by zhusheng on 2006-11-13
you can use apt-get to install the mysql and jdk,and also you can look for some infomation from FAQ,then you can install a tomcat or a jbossAS,then download a jdbc named mysql-connector-java-5.0.4.tar.gz from mysql.com,and take mysql-connector-java-5.0.4-bin.jar into $tomcat_home /commom/lib/.that's ok.

---

### Post by jinxen on 2006-11-13
ok, i will try to make sense of what you wrote when i get back home from the university :) But i have jdk installed already. I just want the option to be able to create databases and etc :)

---

### Post by mjreged on 2006-11-13
Generaly, you need to include the J/Connector jar which is available at mysql.org site and in the Ubuntu depository under a name
**libmysql-java** if you use the depo version, the jar will be located in
/usr/share/java/mysql-3.1.11.jar

You take the jar and place it in your Projects or Server's lib directory
so it's reachable in your project:

if you are using JDBC API direclty :  this is one way to get a connection to your database :

```

try {      
            Class.forName("com.mysql.jdbc.Driver").newInstance();
            prop = new Properties();
            prop.setProperty("useCompression","true");
            prop.setProperty("zeroDateTimeBehavior","convertToNull");
            
    } catch{ // exception here }
  

    public boolean authenticate(String usr, char[] pass, String server) throws Exception {
       
     try {
        url = "jdbc:mysql://"+server+"/phoenix?user="+usr+"&password="+new String(pass)+"";
        conn = DriverManager.getConnection(url, prop );        
        this.setServer( server );        
        return true;
     }catch ( Exception e ) { e.printStackTrace(); return false; }  
        
    }



```

How is that ??

---

### Post by jinxen on 2006-11-13
thanks, this will help! I will try this later :)

---

### Post by paulr on 2006-11-27
I wrote [https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL) ; this works on 5.10, 6.06 and 6.10 ; PM me if it doesn't work. It should :)

---

### Post by Darin722 on 2008-12-24
I'm trying to set up mysql and jdbc driver to work with java and I'm having a problem when I try to connect.  
MySQL server is 5.0.67
mysql-connector-java5.0.8

Code is as follows:
import java.sql.*;

public class Connect
{
	public static void main(String args[])
	{
		Connection con=null;
		try
		{
			//register the driver
			Class.forName("com.mysql.jdbc.Driver");
			String url = "jdbc:mysql://localhost/mysql";
			con=DriverManager.getConnection(url,"root","master");
		} // try
		catch(Exception e)
		{
			System.out.println(e.getMessage());
		} // end catch
		try
		{
			con.close();
		}
		catch (Exception e)
		{
			System.out.println(e.getMessage());
		}
		
	}// end main
} // end class 
The error I get is 

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '????????????????????????????????' at line 1
null



Any ideas what I'm doing wrong?
That is an error from the sql server, it looks like the driver is sending a bunch of question marks, but why?

---

### Post by slamMaster on 2010-01-27
Thanks, that worked great, and was a big help.

If you're working within eclipse you'll need to manually add the mysql.jar file.  Go to Project > Properties > Java Build Path > Add External JARs > and add the /usr/share/java/mysql.jar file.

Maybe that's obvious to some, but it took me more than a minute.

Thanks again!!

---

### Post by Ruhe on 2010-01-27
If you're developing a real world application (not an educational project), then I recommend you to use connection pooling. Apache Commons DBCP does that  well.

---

### Post by chessmonster on 2010-12-19
> **jinxen said:**
> ok, i will try to make sense of what you wrote when i get back home from the university :) But i have jdk installed already. I just want the option to be able to create databases and etc :)


haha

---

