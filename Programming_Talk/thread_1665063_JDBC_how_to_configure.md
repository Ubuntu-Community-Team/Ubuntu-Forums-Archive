---
title: "JDBC how to configure?"
date: 2011-01-11
forum: Programming Talk
---

### Post by zxkelxz on 2011-01-11
I'm on Ubuntu 11.04, I've got SUN-Java-JDK up and running. I need to connect through java to my MYSQL database. I installed the package libmysql-java. I followed this tutorial [https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)

However when I get to:

```
**Setting up the user to use JDBC**

 Add  these two lines to /home/[user]/.bashrc. I am running Java 5 which  doesn't require the current directory to be on the Classpath ; I *think*  Java 2 does, but I'm not going back to check it In that case you may  need to have $CLASSPATH:.:/user/share/java/mysql.jar 
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATHAlternatively, you can set it for all users, by editing /etc/environment (use sudo - sudo vi /etc/environment) 

CLASSPATH=".:/usr/share/java/mysql.jar"Log  out and Log in again. (If you only edited /home/[user]/.bashrc you  don't need to log out/in, only execute in a terminal "$source .bashrc"  in your home dir). Start up a terminal and type: 

echo $CLASSPATHIt should print out something like ":/usr/share/java/mysql.jar" 
```

I find I can't/don't understand how to do this on 11.04 of Ubuntu, I've searched the Internet a good bit but can't find anything more useful than the link I posted. I get this error when just running java DBDemo:

```
java DBDemo
com.mysql.jdbc.Driver
Exception in thread "main" java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:169)
    at DBDemo.main(DBDemo.java:22)

```

When I run the same code with java -cp usr/share/java.mysql.jar DBDemo I get:
```

~/java$ java -cp usr/share/java.mysql.jar DBDemo 
Exception in thread "main" java.lang.NoClassDefFoundError: DBDemo
Caused by: java.lang.ClassNotFoundException: DBDemo
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: DBDemo.  Program will exit.


```

Anyone on here know what I can do?

---

### Post by zxkelxz on 2011-01-11
Well, works now all it took was a restart.

---

