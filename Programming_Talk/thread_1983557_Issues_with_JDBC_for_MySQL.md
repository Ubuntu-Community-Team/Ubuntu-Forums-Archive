---
title: "Issues with JDBC for MySQL"
date: 2012-05-20
forum: Programming Talk
---

### Post by JCoster on 2012-05-20
Hi,
I'm running a MySQL instance on Ubuntu 11.10 and am using the MySQL JDBC connector within my Jar file.
I initialise the connection as follows:
```
conn = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/instancename?connectTimeout=3000", connectionProps);
```

20% of the time this works without issue. However, the remaining 80% of the time this just hangs. No exception is thrown, the thread just hangs. 

When it does hang, the jstack output for the thread is:
```
"Thread-1" prio=10 tid=0x000000004081e800 nid=0xfb1 runnable [0x00007f8c29c5e000]
   java.lang.Thread.State: RUNNABLE
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:631)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:615)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:631)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:615)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:631)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:615)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	- locked <0x00000000f5a23850> (a sun.misc.Launcher$AppClassLoader)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:154)
	at com.jamescoster.common.database.SQLConnection.<init>(SQLConnection.java:40)
	at com.jamescoster.common.update.UpdateSourceThread.run(UpdateSourceThread.java:42)
	at java.lang.Thread.run(Thread.java:662)

```

When it does hang, I can kill the process, try to launch it again 5 seconds later and without issue it may connect.

My question is, what is going on? Why does it sometimes work, then sometimes not? Why is no exception thrown when it hangs?

The only thing the Ubuntu server is used for is this, and it's a relatively new install (~1month).

Thanks for your help in advance.

```
~# java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

```

EDIT: Could it be due to low memory? It's only 512mb box and I have ~100mb free. I'd expect the whole process to crash if it was rather than just hang on the connection, but it's a thought?

---

### Post by PaulM1985 on 2012-05-20
There are a couple of things that appear odd in the code.
1 - Why are you casting to Connection on the function DriverManager.getConnection, doesn't this return a Connection anyway?
2 - What happens if you do not specify a time out?
3 - Do you load the class for the MySQL driver?  After looking at a tutorial it looks like you should have something like this before the getConnection call:
```

               Class.forName ("com.mysql.jdbc.Driver").newInstance ();

```
(taken from here: [http://www.kitebird.com/articles/jdbc.html](http://www.kitebird.com/articles/jdbc.html))
4 - After you have used a connection are you closing it again? It may be that you keep opening connections and the database doesn't allow any more since it has reached the maximum.  The times when you are successful could be because other connections that you haven't closed have eventually become timed out.

Paul

---

### Post by JCoster on 2012-05-20
Paul,
Thank you for your response. Please see answers to your questions below:

> **PaulM1985 said:**
> 1 - Why are you casting to Connection on the function DriverManager.getConnection, doesn't this return a Connection anyway?
My bad, was casting it to a JDBC connection rather than a SQL connection. Changed the import to SQL and removed the cast. Same problem occurring.[/QUOTE]

> **PaulM1985 said:**
> 
2 - What happens if you do not specify a time out?

Same thing, hangs seemingly forever...

> **PaulM1985 said:**
> 
3 - Do you load the class for the MySQL driver?  After looking at a tutorial it looks like you should have something like this before the getConnection call:

Yep, loading that class.

> **PaulM1985 said:**
> 
4 - After you have used a connection are you closing it again?


Yes. Also, I just restarted the mysql service and it failed first time (hanging again). Also, I'd expect some exception in the case of it being due to number of active connections.

I'm wondering if it's some strange setup on the server. I occasionally use various third-party java libraries (e.g. Twitter4j) and that sometimes fails to connect too without any good reason (fairly similar symptoms).

Any other thoughts? Thanks once again.

---

