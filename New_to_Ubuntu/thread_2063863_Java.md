---
title: "Java"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by ericsonlouis on 2012-09-28
I have installed Jave in the ubuntu software center but when i try and play a java based browser based game it tells me that i need to installjave plugin but i know i already did that


Please help

---

### Post by GeForce 9500GT on 2012-09-28
Which Java envirnoment did you installed? OpenJDK? Icedtea? Or Sun Java?
 
For SUN Java take [a look here]("http://www.techlw.com/2012/07/install-sun-java-6-or-7-in-ubuntu-1204.html").

---

### Post by akoskm on 2012-09-28
> **ericsonlouis said:**
> I have installed Jave in the ubuntu software center but when i try and play a java based browser based game it tells me that i need to installjave plugin but i know i already did that


Please help

You probably just installed the JRE (Java Runtime Environment) but not the browser plugin.
Take a look at Ubuntu Community Documentation - [Browser Plugin]("https://help.ubuntu.com/community/Java#Browser_plugin").

In short: if you have installed Java through the software center then I guess you have OpenJRE installed.
Check your JRE version
```

java -version

```

If "java version" is 1.6.x install the icedtea6-plugin, if version is 1.7.x install the icedtea-7-plugin.

You can test the plugin here: [http://www.java.com/en/download/testjava.jsp]("http://www.java.com/en/download/testjava.jsp").

---

### Post by ericsonlouis on 2012-09-28
> **GeForce 9500GT said:**
> Which Java envirnoment did you installed? OpenJDK? Icedtea? Or Sun Java?
 
For SUN Java take [a look here]("http://www.techlw.com/2012/07/install-sun-java-6-or-7-in-ubuntu-1204.html").

i have the OpenJDK

---

### Post by ericsonlouis on 2012-09-28
> **akoskm said:**
> You probably just installed the JRE (Java Runtime Environment) but not the browser plugin.
Take a look at Ubuntu Community Documentation - [Browser Plugin]("https://help.ubuntu.com/community/Java#Browser_plugin").

In short: if you have installed Java through the software center then I guess you have OpenJRE installed.
Check your JRE version
```

java -version

```

If "java version" is 1.6.x install the icedtea6-plugin, if version is 1.7.x install the icedtea-7-plugin.

You can test the plugin here: [http://www.java.com/en/download/testjava.jsp]("http://www.java.com/en/download/testjava.jsp").

It Works thanks

---

