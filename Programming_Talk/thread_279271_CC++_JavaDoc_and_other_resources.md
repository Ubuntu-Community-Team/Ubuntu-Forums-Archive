---
title: "C/C++ JavaDoc??? and other resources???"
date: 2006-10-17
forum: Programming Talk
---

### Post by rekahsoft on 2006-10-17
Hi all, i am experianced in java programming and have been learning C/C++ and was wondering if there is anything like JavaDoc. It is a great utility not to mention it is great to have the docs around. Also is there any good C/C++ debuggers? It also would be nice to have a C/C++ IDE with all the documentation, debugger front end and compiler.

---

### Post by PhrankDaChickenGeek on 2006-10-17
I use the Anjuta IDE for my programming stuff.
Should be in Synaptic!

---

### Post by hod139 on 2006-10-17
> **rekahsoft said:**
> Hi all, i am experianced in java programming and have been learning C/C++ and was wondering if there is anything like JavaDoc. It is a great utility not to mention it is great to have the docs around. 
Check out doxygen, it even recognizes the javadoc commenting style.

> 
Also is there any good C/C++ debuggers? 

Depends what you mean by good.  gdb is the standard gnu debugger and it contains all the features you would want in a debugger.  However, it there is no standard gui for it.

> It also would be nice to have a C/C++ IDE with all the documentation, debugger front end and compiler.
This is most likely going to come down to taste.  I have been using the codeblocks IDE lately.

---

### Post by amo-ej1 on 2006-10-18
There are in fact multiple guis for gdb available, you might want to look at ddd and many IDEs have also a frontend to gdb. Eclipse for example.

I've been using Eclipse/CDT for the past week or so for doing some C++ development and I'm rather pleased (thank you emacs keybindings) with it. The only negative thing is that it isn't capable of parsing the doxygen comments yet :(

---

### Post by ahjiefreak on 2007-11-27
Hi amo-ej and others,

I need help especially I am relatively new to Ubuntu(linux). I am using Ubuntu 6.06(Dapper) and I actually have installed the Eclipse CDT. However after I extract out, I cant find any executables to execute the Eclipse CDT.

I am quite confused that iis Eclipse CDT refers to Eclipse IDE for C/C++ Developers? If anyone is using Eclipse CDT in Ubuntu 6.06, please help to explain what steps did I missed out.


Thanks. HOpe to hear from you guys soon.


Rgrds,
Jason

---

### Post by smartbei on 2007-11-28
@ahjiefreak - My first question is: *Why are you using Dapper as a new user?*

Now, about your question - how did you install Eclipse/CDT? Did you use apt-get/aptitude or did you download it from a website? What steps did you follow?

Yes, CDT is for C/C++. CDT stands for C/C++ Development Tools.

---

### Post by jespdj on 2007-11-28
> **ahjiefreak said:**
> I need help especially I am relatively new to Ubuntu(linux). I am using Ubuntu 6.06(Dapper) and I actually have installed the Eclipse CDT. However after I extract out, I cant find any executables to execute the Eclipse CDT.
What exactly did you download and how did you install it? Eclipse CDT is an add-on for the Eclipse IDE.

First, make sure you have a good version of Java, because Eclipse does not run well on GNU Java (which is a slow and incomplete version of an old version of Java):
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
You might need to run the following after installing Java to make sure that Sun Java 6 is the default Java used on your system:
```
sudo update-java-alternatives --config java
```
(Choose Sun Java 6).

Eclipse 3.2 is in the Ubuntu repository and you can install it with:
```
sudo apt-get install eclipse
```
(Well, I don't know if it is in the repository for Ubuntu 6.06 - why are you using such an old version of Ubuntu?)

Alternatively you can download Eclipse from the Eclipse website: [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)
(The current version is 3.3.1.1).

There is one package ("Eclipse IDE for C/C++ Developers") that already includes the CDT.

If you already have the Eclipse IDE and you want to add CDT to it, then start up Eclipse and select Help / Software Updates / Find and Install. Then choose "Search for new features to install" etc.

---

