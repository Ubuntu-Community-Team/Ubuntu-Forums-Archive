---
title: "Java Applet and Mysql Woes"
date: 2009-04-13
forum: Programming Talk
---

### Post by Das Oracle on 2009-04-13
I have built an applet that communicates to a MySQL database via MySQL Connector/J. Using netbeans I just added it as a library however I am getting an error message that I have no idea how to resolve.

```
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
```

I only get the error when I upload the Jar file to the webserver and run it from my PC or any other pc on the network. If I run this from netbeans it works just fine. I have checked and I do have sql access at each of the stations I tested this on, so it should not be a permissions issue. Any ideas?

---

### Post by cph05a on 2009-04-13
"Make sure that the [mysql] server has not been configured to ignore network connections or (if you are attempting to connect remotely) that it has not been configured to listen only locally on its network interfaces. If the server was started with --skip-networking, it will not accept TCP/IP connections at all. If the server was started with --bind-address=127.0.0.1, it will listen for TCP/IP connections only locally on the loopback interface and will not accept remote connections. "

[http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html)


I'm not sure if this is the problem, but you might try restarting your mysql server without --skip-networking

---

### Post by Das Oracle on 2009-04-13
> **cph05a said:**
> "Make sure that the [mysql] server has not been configured to ignore network connections or (if you are attempting to connect remotely) that it has not been configured to listen only locally on its network interfaces. If the server was started with --skip-networking, it will not accept TCP/IP connections at all. If the server was started with --bind-address=127.0.0.1, it will listen for TCP/IP connections only locally on the loopback interface and will not accept remote connections. "

[http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html)


I'm not sure if this is the problem, but you might try restarting your mysql server without --skip-networking

I just tried connecting from another IP using mysqladmin and specifying TCP/IP as the connection type and I was able to connect just fine and run queries so I don't think this is the issue.

---

### Post by cl333r on 2009-04-13
Find out which line in your source code is triggering that exception, from there on you could make further progress/clues.

---

### Post by Das Oracle on 2009-04-13
> **cl333r said:**
> Find out which line in your source code is triggering that exception, from there on you could make further progress/clues.

Breaks on the second line of these two statements:

[CODEClass.forName("com.mysql.jdbc.Driver");
Connection con = DriverManager.getConnection("jdbc:mysql://" + server + "/db", "uname", "passwd");
[/CODE]

---

### Post by Das Oracle on 2009-04-14
I've been playing around with this a bit. I self signed my applet so there is no applet security issue there.

---

### Post by Das Oracle on 2009-04-15
Anyone have any suggestions? I'm open to try anything at this point

---

### Post by quaternion on 2009-04-15
"I only get the error when I upload the Jar file to the webserver and run it from my PC or any other pc on the network. If I run this from netbeans it works just fine."

I find this a bit confusing... You put a jar on the server, then you are running it from a terminal?  

Anyways netbeans has all the files on your local computer... well normally anyways and it works fine.  So if you packaged the jar correctly it should run on another PC in the network that also has access to the DB and I am assuming that the DB is not on the same machine you are developing on.

I would then suspect routing.  If you are running the program on the same machine as the DB and having it accessed by clients though some terminal program/VNC then try to avoid any routing issues by not specifing an IP address which goes out onto the network (only to come back again), instead stick with the loopback address where this traffic will be avoided.

---

### Post by Das Oracle on 2009-04-20
well I upload the jar to an apache server and the jar has to also connect to a mysql server on the network. apache server xxx.xxx.x.23 and mysql server xxx.xxx.x.22. from 23 i can use mysql-client to login to 22 so there is no issue concerning that.

---

### Post by Undaunted on 2009-06-18
Ever figure anything out for this problem? 

Seems I am in the exact same spot.

---

