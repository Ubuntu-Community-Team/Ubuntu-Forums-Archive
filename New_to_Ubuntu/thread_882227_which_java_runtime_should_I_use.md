---
title: "which java runtime should I use?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by santiagorf on 2008-08-06
Hi all, I was wondering if I need to keep installed all these java distributions from the following list or just keeping alternative 4 will be enought to run all java apps.

cheers 
santiagorf

sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by Diabolis on 2008-08-06
If you don't write your own Java applications, you only need the option number 3.

JRE java runtime environment
JDK java development kit

---

### Post by santiagorf on 2008-08-07
thanks!!

---

