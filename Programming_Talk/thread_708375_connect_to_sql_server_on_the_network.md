---
title: "connect to sql server on the network"
date: 2008-02-26
forum: Programming Talk
---

### Post by soumy on 2008-02-26
I am developing jsp applications on ubuntu (tomcat5) and I would like to connect  my application to an sql server database on the network. Could you please tell me how to do that (what I should download....).

Thanks

---

### Post by pedro_orange on 2008-02-26
Have you heard of the JavascriptDB project?

It's pretty nifty. Check it out.

[http://sourceforge.net/project/showfiles.php?group_id=131101&package_id=143753](http://sourceforge.net/project/showfiles.php?group_id=131101&package_id=143753)

---

### Post by aks44 on 2008-02-26
> **pedro_orange said:**
> Have you heard of the JavascriptDB project?
Javascript has nothing to do with Java...



@OP: I guess you should use **JDBC**. Sorry I can't help more, I'm not very knowledgeable at Java.

---

### Post by thaus on 2008-05-21
Hi, you can connect to SQL Using JDBC 

1) download the JAR of jTDS add to your CLASSPATH
2) Microsoft SQL Server 2000 Driver for JDBC is a Type 4 JDBC driver. You need to place the jar files in your CLASSPATH variable.

when u have all the jars on your CLASSPATH try this code 

import java.sql.*;

public class testConnection
{
    public static void main(String[] args) 
    {
        DB db = new DB();
        db.dbConnect(
     "jdbc:jtds:sqlserver://localhost:1433/tempdb","sa","");
    }
}

class DB
{
    public DB() {}

    public voidn dbConnect(String db_connect_string, 
  String db_userid, String db_password)
    {
        try
        {
            Class.forName("net.sourceforge.jtds.jdbc.Driver");
            Connection conn = DriverManager.getConnection(
    db_connect_string, db_userid, db_password);
            System.out.println("connected");
            
        }
        catch (Exception e)
        {
            e.printStackTrace();
        }
    }
};


Best Regards
Thaus Nebel.

---

