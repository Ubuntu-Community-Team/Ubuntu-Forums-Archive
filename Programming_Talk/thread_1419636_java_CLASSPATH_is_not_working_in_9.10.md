---
title: "java CLASSPATH is not working in 9.10"
date: 2010-03-02
forum: Programming Talk
---

### Post by franciskus on 2010-03-02
When I try to run an application using Netbeans I receive a message that an specific package was not found.

I suppose it's because java is not finding the .jar in the classpath:
```
 private com.toedter.calendar.JDateChooser dataInicioFaturamento;
/home/francisco/NetBeansProjects/SikLami/src/com/sikgraf/ui/reports/ListagemFaturamentoUI.java:80: package com.toedter.calendar does not exist
```
This package is in the file **jcalendar-1.3.2.jar**, which is in **/home/francisco/Sistemas/lib10anos** folder. 

And I have my environment file as following:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun/jre"
CLASSPATH="/home/francisco/Sistemas/lib10anos:.:/home/francisco/Sistemas/lib10anos/jcalendar-1.3.2.jar"
```
Shouldn't be everything working correctly???

Appreciate any help.
F.

---

### Post by Zugzwang on 2010-03-07
I'm not sure what you mean by "environment file". Does the program compile from the command line? Nevertheless, netbeans has its own facilities for dealing with dependencies you might want to try out. In the project settings, there are some "compile time libraries" and "run time libraries" you can specify. Add it to to both and you should be fine for running/compiling with netbeans.

---

### Post by Queue29 on 2010-03-07
Does your CLASSPATH entry show up if to you do:

```
env | grep CLASSPATH 
```

?

---

### Post by franciskus on 2010-03-08
> **Queue29 said:**
> Does your CLASSPATH entry show up if to you do:

```
env | grep CLASSPATH 
```
?Yes, it does.
```
CLASSPATH=/home/francisco/Sistemas/lib10anos:.:/home/francisco/Sistemas/lib10anos/jcalendar-1.3.2.jar

```

---

