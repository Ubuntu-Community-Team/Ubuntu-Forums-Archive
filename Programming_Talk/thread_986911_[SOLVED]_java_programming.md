---
title: "[SOLVED] java programming?"
date: 2008-11-19
forum: Programming Talk
---

### Post by aszxcv on 2008-11-19
i use sudo apt-get install sun-java6-jdk netbeans 
to download netbeans and jvm and java sdk my question i just print a basic hello world in netbeans without seting any java path to sdk bin like you have to on a windows pc
does netbeans on linux automatically detect java jdk

---

### Post by leg on 2008-11-19
Netbeans looks for the jdk when it is installed (even on windows) so it keeps a path to it when for when you compile.

---

### Post by aszxcv on 2008-11-19
so regardless if the path is set or not it finds the jdk

so setting the path to bin is really helpful for dos/command line program

---

### Post by leg on 2008-11-19
From within NetBeans yes I believe that it does. It has been a while since I used it though.

---

### Post by drubin on 2008-11-19
> **aszxcv said:**
> i use sudo apt-get install sun-java6-jdk netbeans 
to download netbeans and jvm and java sdk my question i just print a basic hello world in netbeans without seting any java path to sdk bin like you have to on a windows pc
does netbeans on linux automatically detect java jdk

> **leg said:**
> Netbeans looks for the jdk when it is installed (even on windows) so it keeps a path to it when for when you compile.

Netbeans is written in Java. So at least the JRE must be present in order for even netbeans to run. 

But you can go to preferences and manually set it.

---

