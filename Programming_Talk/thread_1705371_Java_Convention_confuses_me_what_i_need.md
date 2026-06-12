---
title: "Java Convention confuses me what i need"
date: 2011-03-12
forum: Programming Talk
---

### Post by 0000_soldier on 2011-03-12
Hey Ladies and gents,

I found out that for me to compile servlets i needed the servlet-api.jar in a sdk directory, to compile it in my windows VM for tomcat, to use:

```

import java.io.*;
import javax.servlet.*;
import.servlet.http.*;

```

So if i want to make an advanced web app what that can set session, access a postgre db, what installs am i gonna need?

 If i want to create a enterprise application i could use_ already existing_ "enterprise javabeans" eg where can i get these do they cost money?  Because of the java naming conventions ie javax, and  java 1.2-1.4 is called java2; i get a bit confused reading on the website a little enlightenment on the right direction, please!?

Thank you.

---

### Post by t1497f35 on 2011-03-12
The "Java 2" term was deprecated a long time ago and Java has evolved since then quite a bit.
Nowadays when one says i.e. "Java 5" he means JRE 1.5 and/or JDK 1.5, "Java 6" means JRE 1.6 and/or JDK 1.6 etc.

People don't typically compile themselves servlets nor Java beans. They usually use an IDE to do the job - it saves a lot of time.

Basically you should download [NetBeans]("http://netbeans.org/downloads/index.html") the "Java" bundle, install it, update it from the Help Menu - "check for updates" and then go on, anything's pretty obvious. Some folks choose Eclipse but I find it (a lot) less intuitive.

PS: for enterprise stuff use "GlassFish", for anything else (servlets, jsp, etc) - Tomcat - cause it's lighter and starts up faster.

---

### Post by 0000_soldier on 2011-03-12
Thank you for reply!

So this glass fish will provide me with an application server, which will have the EE api i would potentially need?

---

### Post by t1497f35 on 2011-03-12
Yes, it has a lot of stuff, not only EE apis.

---

### Post by Some Penguin on 2011-03-12
You'll also want the JDBC connector from the postgresql folks, and a connection pool (common free choices include DBCP, C3P0 and Proxool.  The jdbc-pool w/ Tomcat 7 looks like it was significantly less badly designed and written.)

---

### Post by 0000_soldier on 2011-03-14
Thank you for the hints in the right direction,

Appreciated. Im not a programmer just an enthusiast :P

---

