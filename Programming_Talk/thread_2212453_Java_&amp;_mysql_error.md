---
title: "Java &amp; mysql error"
date: 2014-03-21
forum: Programming Talk
---

### Post by Drenriza on 2014-03-21
Hoping you guys can help me.

I have a mysql server, and installed phpmyadmin to administrate it.
I have created a user for my local lan with the name "cristian" and password of "kage" with the host of "%", with no global PRIVILEGES
I have then added all database specific privileges for the user.

But when i try and connect to the database i get an error as follows
> com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Access denied for user 'cristian'@'%' to database 'jsp_testDB;'

```

public class ClassOne {
    public static void main(String[] args) {
        
        Connection connection = null;
        
        try {
            Class.forName("com.mysql.jdbc.Driver");
            connection = DriverManager.getConnection("jdbc:mysql://192.168.0.251:3306/jsp_testDB;", "cristian", "kage");
            
            if(!connection.isClosed()){
                System.out.println("Connection ok");
            }
            
        } catch (ClassNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
}

```

I am using
> Eclipse Java EE IDE for Web Developers.

Version: Kepler Service Release 2
Build id: 20140224-0627

And got a JDBC file "mysql-connector-java-5.1.29-bin.jar" in my "Referenced Libraries".

I have checked that my mysql service is listening on the TCP/IP connection on the servers ip address and not 127.0.0.1
> netstat -lnp | grep mysql
tcp        0      0 192.168.0.251:3306      0.0.0.0:*               LISTEN      10582/mysqld
unix  2      [ ACC ]     STREAM     LISTENING     16533    10582/mysqld        /var/run/mysqld/mysqld.sock



But are running out of google searches to why i get this error.
Hope someone can help me out a bit.

---

### Post by spjackson on 2014-03-21
I'm not sure what the right syntax should be for passing the user and password to jdbc, but MySQL isn't seeing them. "[COLOR=#000000]*(using password: NO)" means that no password has been supplied. "*[/COLOR][COLOR=#000000]*for user ''@'192.168.0.11'" also means that no user has been supplied, because you should get "*[/COLOR][COLOR=#000000]*for user 'cristian'@'192.168.0.11'".*[/COLOR]

---

### Post by Drenriza on 2014-03-21
Edited it to
```
connection = DriverManager.getConnection("jdbc:mysql://192.168.0.251:3306/jsp_testDB;", "cristian", "kage");
```

And now i get this error.
> com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Access denied for user 'cristian'@'%' to database 'jsp_testDB;'

So now i guess it sees the username and password but wont allow access because... I dont know :)

---

### Post by spjackson on 2014-03-21
It could be that semicolon at the end of the database name. Sorry I didn't spot that before.

---

### Post by Drenriza on 2014-03-21
> **spjackson said:**
> It could be that semicolon at the end of the database name. Sorry I didn't spot that before.

hhhhaaaaalijula Halijula Hhhaaallliiiijjjjjuuullllaaaa

Thanks ,)

---

