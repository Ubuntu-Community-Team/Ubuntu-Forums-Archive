---
title: "Connecting to MySQL via a Java servlet"
date: 2005-06-10
forum: Programming Talk
---

### Post by judabuddhist on 2005-06-10
I'm having a problem when trying to run a servlet in Hoary with Tomcat. My mysqld process is running happily in the background, and the Java code is working well enought, but whenever the Servlet tries to access the database it fails and logs this exception:

java.sql.SQLException: Cannot connect to MySQL server on localhost:3306. Is there a MySQL server running on the machine/port you are trying to connect to? (java.net.ConnectException)
        at org.gjt.mm.mysql.Connection.connectionInit(Unknown Source)
        at org.gjt.mm.mysql.jdbc2.Connection.connectionInit(Unknown Source)
        at org.gjt.mm.mysql.Driver.connect(Unknown Source)
        at java.sql.DriverManager.getConnection(DriverManager.java:525)
        at java.sql.DriverManager.getConnection(DriverManager.java:171)
        at coreservlets.ConnectionPool.newConnection(ConnectionPool.java:237)
        at coreservlets.ConnectionPool.createConnections(ConnectionPool.java:207)
        at coreservlets.ConnectionPool.createPool(ConnectionPool.java:180)

So something's keeping the java from connect to the mysql

I tried the advice in this thread: [http://www.ubuntuforums.org/showthread.php?t=33601](http://www.ubuntuforums.org/showthread.php?t=33601)
 but my /etc/mysql/my.cnf file doesn't have any such option under skip-networking, only
```

skip-networking
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K

```

running
~$: netstat -an | grep 3306
brings up nothing.

Can anyone help me out? This is driving me insane, and keeping me from doing my job.

Thanks

---

### Post by LordHunter317 on 2005-06-10
[QUOTE=judabuddhist]
 but my /etc/mysql/my.cnf file doesn't have any such option under skip-networking, only
```

skip-networking
```[/quote]Yes it does.  That's what that line is.  'skip-networking' is the name of the option.   You need to remove that line and restart mysqld.

If you're only going to access the database server via Java on the machine it's running on, you should replace that line with:```
bind-address = 127.0.0.1
``` To only allow TCP on localhost.

---

### Post by judabuddhist on 2005-06-10
Thanks, I'm an idiot. I interpreted his psuedocode as another line of text I had to comment out.

Of course now I'm getting a whole new error in my logs, and the damn thing still isn't working

```

java.sql.SQLException: Server configuration denies access to data source
        at org.gjt.mm.mysql.MysqlIO.init(Unknown Source)
        at org.gjt.mm.mysql.Connection.connectionInit(Unknown Source)
        at org.gjt.mm.mysql.jdbc2.Connection.connectionInit(Unknown Source)
        at org.gjt.mm.mysql.Driver.connect(Unknown Source)
        at java.sql.DriverManager.getConnection(DriverManager.java:525)
        at java.sql.DriverManager.getConnection(DriverManager.java:171)
        at coreservlets.ConnectionPool.newConnection(ConnectionPool.java:237)
        at coreservlets.ConnectionPool.createConnections(ConnectionPool.java:207)
        at coreservlets.ConnectionPool.createPool(ConnectionPool.java:180)
        at courseware.module.ManagerServlet.init(ManagerServlet.java:78)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.java:1091)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:925)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContext.java:3857)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4118)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:759)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:739)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:524)
...

```


Looks like something's fucked up with permissions and all that, but I have no idea what it is

the Driver is being passed the following arguments
String driver = "org.gjt.mm.mysql.Driver";
String dbURL = "jdbc:mysql://localhost/courseware_v2";
String username = "root";
String password = "password";

I have a user programmed into mysql 'root'@'localhost' with the password password and priviledges set to Y for everything, and the database is in fact called courseware_v2. 

Anyone see anything obviously wrong?

---

### Post by LordHunter317 on 2005-06-10
One, that isn't the offical MySQL driver, I think.  I'd use that, or use one provided by your J2EE container if it has one (BEA I know provides a high-performance, pooling MySQL driver).

Second, don't connect as root.

Third, don't use a password of 'password'.

Forth, what was the GRANT command you ran to give the permissions? 

I haven't done much work using Tomcat correctly, so maybe it's a container permissions issue, though I find that doubtful.  Writing 30 lines of JDBC in a simple Test.java that runs as an application to verify wouldn't be that hard though.

---

### Post by judabuddhist on 2005-06-10
[QUOTE=LordHunter317]One, that isn't the offical MySQL driver, I think.  I'd use that, or use one provided by your J2EE container if it has one (BEA I know provides a high-performance, pooling MySQL driver).

Second, don't connect as root.

Third, don't use a password of 'password'.

Forth, what was the GRANT command you ran to give the permissions? 

I haven't done much work using Tomcat correctly, so maybe it's a container permissions issue, though I find that doubtful.  Writing 30 lines of JDBC in a simple Test.java that runs as an application to verify wouldn't be that hard though.[/QUOTE]

1. I'm kind of stuck with a lot of less than ideal stuff in this project, the fact that I'm even using java servlets is a testament to that.

2,3. Yeah, I know, but this just something I 'm running for testing, not the actual product. Would making a new user help things? Now that I think of it, I was originally told to make a user 'mysql', but then that was changed

4. I don't think I ever ran a grant command. It's the root account, and it seems to have all the privledges already

---

### Post by judabuddhist on 2005-06-10
Figured it out myself. It was just a matter of permissions. Thanks again, and sorry for the pointless thread

---

