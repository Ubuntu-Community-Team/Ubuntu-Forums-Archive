---
title: "import com.google.gwt.gadgets.client.Gadget;"
date: 2009-01-07
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-07
When you have something like this in your java program, does that mean that your computer has to be online and have to connect to the google server in order to run the java program?

[INDENT]package com.google.gwt.gadgets.sample.hellogadgets.client;
import com.google.gwt.gadgets.client.Gadget;[/INDENT]


Thanks a lot.

Paul

---

### Post by hundredwatt on 2009-01-07
> **zpzpzp said:**
> When you have something like this in your java program, does that mean that your computer has to be online andN have to connect to the google server in order to run the java program?

[INDENT]package com.google.gwt.gadgets.sample.hellogadgets.client;
import com.google.gwt.gadgets.client.Gadget;[/INDENT]


Thanks a lot.

Paul

No, you should have all the files necessary to run GWT locally. com.google. etc refers to a Java class name, not a website.

---

### Post by shadylookin on 2009-01-07
> **zpzpzp said:**
> When you have something like this in your java program, does that mean that your computer has to be online and have to connect to the google server in order to run the java program?

[INDENT]package com.google.gwt.gadgets.sample.hellogadgets.client;
import com.google.gwt.gadgets.client.Gadget;[/INDENT]


Thanks a lot.

Paul

no they should all be avail locally. In java package convention starts with com(or edu, org, gov, etc).websiteName.whatever.you.want

---

### Post by zpzpzp on 2009-01-08
> **shadylookin said:**
> no they should all be avail locally. In java package convention starts with com(or edu, org, gov, etc).websiteName.whatever.you.want

So how would you get those libraries? Do you have to download them and then put them somewhere? Do you also need to add classpath in your IDE?

---

### Post by cacycleworks on 2009-01-08
I don't know about IDE's but you will have the .js, JAR, or TOMCAT or some kind of file loaded on the web-server (or linked to locally if running pure java).

:)

---

### Post by zpzpzp on 2009-01-08
> **cacycleworks said:**
> I don't know about IDE's but you will have the .js, JAR, or TOMCAT or some kind of file loaded on the web-server (or linked to locally if running pure java).

:)

Could you explain a little more, and/or give an example?

Thanks in advance :)

Paul

---

### Post by myrtle1908 on 2009-01-08
First you should read up on Java packages.  A simple place to start would be [http://en.wikipedia.org/wiki/Java_package](http://en.wikipedia.org/wiki/Java_package).  Then onto the Sun Java site.

Second, you will need to download the GWT libraries from google (most likely distributed as JAR file(s) complete with supporting documentation and examples).

Once you have obtained the JAR files you simply place them in the classpath for the project you are working on (so that the compiler can find them when you *import* a GWT class).

If you are using Eclipse and your project is a Dynamic Web Application using Tomcat as your webserver then you should be able to simply drag the relevant JARs into your WEB-INF/lib folder within Eclipse.

Finally, no your computer will not communicate with the google servers when using their GWT packages.

---

### Post by zpzpzp on 2009-01-16
Thank you very much myrtle1908!

Paul

> **myrtle1908 said:**
> First you should read up on Java packages.  A simple place to start would be [http://en.wikipedia.org/wiki/Java_package](http://en.wikipedia.org/wiki/Java_package).  Then onto the Sun Java site.

Second, you will need to download the GWT libraries from google (most likely distributed as JAR file(s) complete with supporting documentation and examples).

Once you have obtained the JAR files you simply place them in the classpath for the project you are working on (so that the compiler can find them when you *import* a GWT class).

If you are using Eclipse and your project is a Dynamic Web Application using Tomcat as your webserver then you should be able to simply drag the relevant JARs into your WEB-INF/lib folder within Eclipse.

Finally, no your computer will not communicate with the google servers when using their GWT packages.

---

