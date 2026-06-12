---
title: "Add Platform in Netbeans"
date: 2013-01-28
forum: Programming Talk
---

### Post by akoskm on 2013-01-28
Hi Community!

I'm trying to find out how to add a freshly installed OpenJDK 7 platform (installed through software center) to NetBeans 7.2.

When I navigate to Tools > Java Platforms > Add Platform and select the **/usr/lib/jvm directory** the JDK installations are showing up but except the **/usr/lib/jvm/java-1.6.0-openjdk-amd64** and **/usr/lib/jvm/java-6-openjdk-amd64** the Next button is greyed out when I'm selecting the JDK7 folders.
[IMG]http://i47.tinypic.com/2urxcer.png[/IMG]

Is there any way to add the OpenJDK platform to Netbeans 7.2?

---

### Post by iMac71 on 2013-01-28
you might give a look to what's suggested in the following thread: [thread=1969338]Installing jdk in ubuntu 12.04 (64 bit)[/thread].

---

### Post by akoskm on 2013-01-28
> **iMac71 said:**
> you might give a look to what's suggested in the following thread: [thread=1969338]Installing jdk in ubuntu 12.04 (64 bit)[/thread].

Installation of the OpenJDK 1.7 went fine through software center. It is installed into the same folder as 1.6 (see the screenshot).
I have problem when I'm trying to add jdk 7 as new platform in NetBeans.

---

### Post by iMac71 on 2013-01-28
As you can read in this post of [netbeans forum](http://netbeans.org/bugzilla/show_bug.cgi?id=210664), there are problems using openjdk-7-jdk with netbeans on ubuntu.

---

### Post by dennismulder on 2013-02-17
I've got the exact same problem, did you solve it?

---

### Post by slickymaster on 2013-02-18
> **akoskm said:**
> Hi Community!

I'm trying to find out how to add a freshly installed OpenJDK 7 platform (installed through software center) to NetBeans 7.2.

When I navigate to Tools > Java Platforms > Add Platform and select the **/usr/lib/jvm directory** the JDK installations are showing up but except the **/usr/lib/jvm/java-1.6.0-openjdk-amd64** and **/usr/lib/jvm/java-6-openjdk-amd64** the Next button is greyed out when I'm selecting the JDK7 folders.
[IMG]http://i47.tinypic.com/2urxcer.png[/IMG]

Is there any way to add the OpenJDK platform to Netbeans 7.2?

You can edit the **netbeans.conf** file and change 'netbeans_jdkhome=' value according to your JDK location. Something like this:
```
netbeans_jdkhome="path/to/your/JDK/location"
```

---

