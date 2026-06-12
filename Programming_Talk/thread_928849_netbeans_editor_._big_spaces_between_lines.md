---
title: "netbeans editor . big spaces between lines"
date: 2008-09-24
forum: Programming Talk
---

### Post by kestaz on 2008-09-24
I recently installed netbeans ide with c++ plugin. But i'm feeling uncomfortable using netbeans editor(writing code). I don't know how to change length of space between lines. [http://img338.imageshack.us/my.php?image=testzr5.png](http://img338.imageshack.us/my.php?image=testzr5.png) 

I am using newest ubuntu(7.10) and netbeans 6.1

---

### Post by xlinuks on 2008-09-24
I would suggest trying to change the font in the settings pane and/or install additional fonts from the restricted package.

---

### Post by kestaz on 2008-09-24
I tryed to change font, but no luck ;( I seams like that with Java code there's no such big lines

---

### Post by xlinuks on 2008-09-24
It seams? If you have also the standard Java pack intalled and the Java code looks fine then it's a C/C++ issue, in this case try changing all the settings that might apply to it. I have NetBeans 6.1 and the C++ code is fine, looks exactly like the Java one.

---

### Post by tinny on 2008-09-24
"Tools" > "Options" > "C/C++" > "Formatting Style"

If you scroll down the available properties you will find a section that deals with blank lines.

---

### Post by kestaz on 2008-09-25
Ok thanks for quick response . 

I went Options->C/C++->Formatting Style. And I only see such formatting parameters:

Blank Lines
  Before Class
  After Class Header
  Before Function

So setting all values to 0 didn't solved my problem

---

### Post by cerealk on 2008-11-03
kestaz,

I am having the same exact problems.  I'm pretty frustrated and can't figure it out.  Have you been able to figure this out?

Thanks in advance!

---

### Post by GjesBolan on 2008-11-09
Soory for my bad English, :(,

i had same problem and soloved it, just uninstaling open-Java, and instaling
sun's-Java, that's it. (remove it from sinaptic!)

Goood luck!

---

### Post by tinny on 2008-11-12
> **GjesBolan said:**
> Soory for my bad English, :(,

i had same problem and soloved it, just uninstaling open-Java, and instaling
sun's-Java, that's it. (remove it from sinaptic!)

Goood luck!

Open java does it AGAIN!!!

What version of Ubuntu are you running?

---

### Post by ddosia on 2008-11-12
hello, i have exactly the same problem in netbeans.
trying to install *msttcorefonts*, it doesn`t helps

have installed:
openjdk-6-jre (6b12-0)
openjdk-6-jdk (6b12-0)
sun-java6-jre(6-10-0)
sun-java6-jdk(6-10-0)
sun-java6-fonts(6-10-0)

Ubuntu 8.10
---
also found not solved post in archive:
[http://ubuntuforums.org/showthread.php?t=528671]("http://ubuntuforums.org/showthread.php?t=528671")

---

### Post by ddosia on 2008-11-12
try to do like was advised by [b]GjesBolan[b] and everything works:
del all packages like open-jdk-6-* and installed sun`s packages,
then run netbeans with command like 
```

./netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.10

```
where 1.6.0.10 - my version of installed sun`s java and that`s is.
also this solves some strange problems with java web start, which was occured during develop on java
but i want to see normal solvation of this problem

---

### Post by vlnikolic on 2008-11-12
installing of sun java jdk solves the problem
i had the same prob...
thanks a lot!

---

### Post by endresma on 2008-11-16
This issue seems to be related to this bug report:
[https://bugs.launchpad.net/ubuntu/hardy/+source/openjdk-6/+bug/234314](https://bugs.launchpad.net/ubuntu/hardy/+source/openjdk-6/+bug/234314)

---

### Post by terryroe on 2009-01-28
> **ddosia said:**
> try to do like was advised by [b]GjesBolan[b] and everything works:
del all packages like open-jdk-6-* and installed sun`s packages,
then run netbeans with command like 
```

./netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.10

```
where 1.6.0.10 - my version of installed sun`s java and that`s is.


You can also make this change permanent by editing the netbeans.conf file located at <netbeans install dir>/etc/netbeans.conf.  Edit the line in this file like the one below to indicate the location of your jre:

```
netbeans_jdkhome="/usr/lib/jvm/java-6-sun-1.6.0.10/jre"
```

I prefer this fix because it gives me the correct jre no matter how I launch netbeans.

TR

---

