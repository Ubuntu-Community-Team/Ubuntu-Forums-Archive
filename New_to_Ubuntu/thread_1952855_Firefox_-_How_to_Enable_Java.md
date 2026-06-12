---
title: "Firefox - How to Enable Java"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by expatCM on 2012-04-05
I was trying to log on to personal banking using the following url

[https://www.shacombank.com.hk/ibanking/servlet/com.ibm.dse.cs.servlet.CSEstablishSessionServlet/customer/en_US](https://www.shacombank.com.hk/ibanking/servlet/com.ibm.dse.cs.servlet.CSEstablishSessionServlet/customer/en_US)

I get a message that says 

Enable Java
You need to use a browser that support Java and have it enabled in order to access i-banking.

It then talks about IE


What do I need to do to make this work with Ubuntu / Firefox?

---

### Post by santosh83 on 2012-04-05
> **expatCM said:**
> I was trying to log on to personal banking using the following url

[https://www.shacombank.com.hk/ibanking/servlet/com.ibm.dse.cs.servlet.CSEstablishSessionServlet/customer/en_US](https://www.shacombank.com.hk/ibanking/servlet/com.ibm.dse.cs.servlet.CSEstablishSessionServlet/customer/en_US)

I get a message that says 

Enable Java
You need to use a browser that support Java and have it enabled in order to access i-banking.

It then talks about IE


What do I need to do to make this work with Ubuntu / Firefox?

Installing the completely free, community developed version of Java, OpenJDK, is quite easy in Ubuntu. See: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java).

But some Java apps don't work properly with OpenJDK and must have Sun's (now Oracle's) version of JDK. If thats the case, then the procedure to install it is more involved. See directions here:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by expatCM on 2012-04-05
thanks for the comment.  I already have openjdk 6 installed. Thought I might upgrade to version 7 but that does not appear to be so friendly.

But it looks like I need to enable the ppa and use the Sun / Oracle version which I will do tomorrow ....

---

### Post by expatCM on 2012-04-05
ok ...  so I skipped a coffee and did this instead.  

The Sun / Oracle solution works perfectly.

Thank you for your help.

---

### Post by bear12hug on 2012-04-05
Thanks for the wonderful information SAntosh,

 it works on my PART!!! :popcorn:

____________________________
[Funny Photos]("http://www.funnywallphotos.com")

---

### Post by lovinglinux on 2012-04-05
reason why your openjdk suddenly stopped working is because Mozilla is blocklisting old versions that are insecure.

---

