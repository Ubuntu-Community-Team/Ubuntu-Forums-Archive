---
title: "[SOLVED] Java (JDBC). Connecting to a local PostgreSQL database"
date: 2008-11-27
forum: Programming Talk
---

### Post by fredscripts on 2008-11-27
Hi!

I have PostgreSQL 7.4 (note that's an old version, so maybe the error is related with this).

Ok then I have a database called "test" with some tables.

Then , I want to connect to that database from a java program to execute queries from the database "test".

The java code is (just put the important part, not class definition and inheritance):

```
public static void main(String[] args) throws ClassNotFoundException, SQLException {
            
    String driver ="org.postgresql.Driver";
    String url = "jdbc:postgresql://localhost/postgres"; 
    String user = "postgres"; 
    String pwd = ""; 
                         
    try {
         Class.forName(driver); //trying to load driver
    }
    catch (ClassNotFoundException e) {
                         
        System.err.println("Can't load driver "+ e.getMessage());
    }
    try { 
        Connection con = DriverManager.getConnection(url, user, pwd);
        System.err.println("Conection OK");
                           
        con.close(); 
    }
    catch(Exception e) {
                         
        System.err.println("Connection Attempt failed");
        System.err.println(e.getMessage());
    }
}
```

(Sorry for possible indentation mess from copying code)

OK Then,

First of all, I start the database:

On a terminal (as being an old version of pgsql isn't on the path so I must do the following commands to enter to the "test" database):

```
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
/usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data >logfile 2>&1 &
/usr/local/pgsql/bin/psql test
```

Note that I didn't type any password to enter to the database.


All right, then I try to run the java code linking with the proper driver library:


```

javac Client.java
java -classpath /home/postgres/Desktop/postgresql-7.4.jdbc3.jar:./ Client

```

So I've logged in Ubuntu with the user postgres, and the .jar is the correct one as I've got to access to a database of my university (by writting to the String url = ...161.112.*.*/user) with any problems.

The error I get is:

Connection Attempt failed
Connection refused. Check that the hostname and port are correct and that the
postmaster is accepting TCP/IP connections. 

To sum up,

With that java code, I can get access to a database of my university (just changing the url, user and password). That is to say, no problem with the jdbc driver, nor the postgresql. The problem seems to be that I cannot access my local database because some sort of TCP/IP connection (to my own machine!) error.

I attach my pg_hba.conf file.

Thanks so much in advance!

---

### Post by Timdejager on 2008-11-27
Have you tried using a jdbc 3 driver I suspect that jdbc 4 doesn't work with the postgres version you are using.

---

### Post by CptPicard on 2008-11-27
IIRC TCP/IP connections are disabled by default on PostgreSQL, you need to enable them in the configuration.

---

### Post by fredscripts on 2008-11-28
> **Timdejager said:**
> Have you tried using a jdbc 3 driver I suspect that jdbc 4 doesn't work with the postgres version you are using.

Yep I'm using jdbc 3 I misspelled on my post, editing it! Thanks!

---

### Post by fredscripts on 2008-11-28
> **CptPicard said:**
> IIRC TCP/IP connections are disabled by default on PostgreSQL, you need to enable them in the configuration.

I imagine is something like this, would you mind telling me how could I do it? (I've posted the pg_hba.conf , if you need more information please tell me)

---

### Post by fredscripts on 2008-11-28
I had to edit the file postgresql.conf and set the tcpip_socket = true :)

---

