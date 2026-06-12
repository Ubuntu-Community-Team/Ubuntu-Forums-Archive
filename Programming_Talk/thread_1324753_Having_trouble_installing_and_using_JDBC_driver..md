---
title: "Having trouble installing and using JDBC driver."
date: 2009-11-12
forum: Programming Talk
---

### Post by Jeremywilms on 2009-11-12
I've installed the JDBC driver, and have manually gone to the location I've set the classpath to, the driver exists. I've done this on windows and it works perfectly, for some reason, after switching to ubuntu I'm having some problems.

Essentially, I get an exception thrown every time I try to create a new instance of the class(com.mysql.jdbc.Driver).

If I don't create a new instance, I get past that part, attempt to open an new connection. I get

No suitable driver found for jdbc:mysql://127.0.0.1:3306/testdb

echo $CLASSPATH = ":/usr/share/java/mysql.jar"

I followed this tutorial word for word:
[https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)

---

### Post by froggyswamp on 2009-11-12
I'm not sure what "echo" is doing there..
Anyway, if you wanna solve this issue once and forever just put your .jar file into the "ext" folder so it will be visible to all your Java applications, on Karmic x64 the path is:
/usr/lib/jvm/java-6-sun/jre/lib/ext
Should work after you restart your app, if doesn't yet work, reboot or log out and log in.

---

### Post by Jeremywilms on 2009-11-12
> **froggyswamp said:**
> I'm not sure what "echo" is doing there..
Anyway, if you wanna solve this issue once and forever just put your .jar file into the "ext" folder so it will be visible to all your Java applications, on Karmic x64 the path is:
/usr/lib/jvm/java-6-sun/jre/lib/ext
Should work after you restart your app, if doesn't yet work, reboot or log out and log in.

I'm sorry I should have explained better. The _echo $CLASSPATH_ was a command put into the shell to show that the classpath was set correctly, after the = sign, was the output.

I'll give it a try.

Thanks.

---

