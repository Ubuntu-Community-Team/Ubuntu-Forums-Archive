---
title: "writing java app that connects to mysql db on another machine"
date: 2008-07-04
forum: Programming Talk
---

### Post by badperson on 2008-07-04
Hi,

posted this on another forum, but thought I'd put it here, too. 
I wrote some simple jdbc code, which I'm pretty sure is right, because it attemps to make the connection, but times out. 

I think it has something to do with which port is listening on the server



I'm trying to connect a java application to a mysql database on a machine running ubuntu server. The machine the java app is written and run on is ubuntu desktop.
Here is the relevant java code:
```
String url="jdbc:mysql://jasonServer/phototestdb";
			Connection con = DriverManager.getConnection(url, p);

```


('p' is a Properties object containing user and pw).

I get this error:
```


**** NOTE this is the wrong error, it should be a connection timed out error, but it looks the same

com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 
 
** BEGIN NESTED EXCEPTION ** 
 
java.net.SocketException
MESSAGE: java.net.ConnectException: Connection refused
 
STACKTRACE:
 
java.net.SocketException: java.net.ConnectException: Connection refused
 
// bunch of stack trace stuff...

```



I've tried a couple ways of connecting in the url,
```
String url="jdbc:mysql://jasonServer/phototestdb";
String url="jdbc:mysql://jasonServer:3306/phototestdb";
String url="jdbc:mysql://99.999.9.99/phototestdb"; (9's are my ip address, I have static ip's on wireless network)
String url="jdbc:mysql://99.999.9.99:3306/phototestdb";

```



when I have the ip in the url, it fails immediately and gives me a connection refused error:
```
establishing connection
com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 
 
** BEGIN NESTED EXCEPTION ** 
 
java.net.SocketException
MESSAGE: java.net.ConnectException: Connection refused
 
STACKTRACE:
 
java.net.SocketException: java.net.ConnectException: Connection refuse


```

But when I have the server name in the url, it hangs for a long time and then gives me the timeout error.

Couple other relevant notes;
I am able to ping the server from the desktop using the server name, i.e,
ping jasonServer
but not using the ip addres

I am not able to telnet in the terminal window, I type
telnet jasonServer 3306,
it says "Trying (ip address)

and it just hangs there.

This leads me to believe this isn't really a java issue 
but something to do with my network.


One more thing, I think the mysql config file on the server has it set to only listen to the local host...(I don't have the file in front of me, or I'd paste the line of code)

I tried changing that but no luck. 

Any ideas?
bp

---

### Post by henchman on 2008-07-04
can you connect to the mysql sever using the mysql command line tool?

```

mysql --user=username --password=password --host=host dbname

```

---

### Post by badperson on 2008-07-04
Hi,

I tried that code from the terminal, it gave me a lot of what looked like help menu output...several pages, not sure if I did the right thing. 

I tried that from the client machine, is that correct? 

Also, I was looking online and found some stuff for mysqld, but I'm not sure if that was only for windows? 
It was on the mysql tutorial site, it said to enter
mysqld-opt --console,
but that didn't work for me. 
bp

---

### Post by henchman on 2008-07-04
you can use the code to connect from your client to the server which you specify with the --host setting :) so you were right. 

When you connected without an error message, try typing

```
SHOW TABLES;
```

don't forget the ';'. if you get an overview of your tables, then your connection is alright :)

Iam very sorry, but if it's alright i can't help you, because your connection string is alright. I just know it with the port given after the server name... but it should work without... nite :)

---

### Post by badperson on 2008-07-04
Hi,

it isn't working.

The thing is, mysql is installed on both machines, so maybe that's messing it up, I don't know. 
bp

---

### Post by henchman on 2008-07-04
what is not working?

- connecting via the mysql terminal command
- connecting works, show tables not
- connecting works, show tables shows the tables ;), but java doesn't

---

### Post by badperson on 2008-07-04
solved,

I had to enter this in the server:
(found this on the mysql forum)
You simply need to do:

mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP
-> ON <dbname>.*
-> TO <username>@<host name>
-> IDENTIFIED BY '<password>';

where <dbname> is the name of the database you are tyring to connect to, <username> is the username of the user trying to connect to the database, <host name> the name of the host (in your case the XXX host) and <password> the password of the user.

---

### Post by balagosa on 2008-07-04
I did not know you had to grant access to users trying to access the database.

---

### Post by Geekkit on 2008-07-04
> **balagosa said:**
> I did not know you had to grant access to users trying to access the database.

You do if you're doing it from a different machine ... as apposed to SQLServer and Windows where there's a big neon sign saying 'Welcome', the door is open, and all data is unattended.

---

### Post by badperson on 2008-07-04
> **Geekkit said:**
> You do if you're doing it from a different machine ... as apposed to SQLServer and Windows where there's a big neon sign saying 'Welcome', the door is open, and all data is unattended.

:lolflag::lolflag:

---

