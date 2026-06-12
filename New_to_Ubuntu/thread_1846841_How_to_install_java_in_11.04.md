---
title: "How to install java in 11.04?"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-09-19
I opened Synaptic package manager and found openjdk-6-jdk.  Is this the correct one?
 
Thanks

---

### Post by Jagoly on 2011-09-19
no, you want the jre. 

openjdk-6-jre

---

### Post by dniMretsaM on 2011-09-19
Isn't this installed by default? You could also install SunJava from the repos. And in case your wondering what the difference between JDK and JRE is:
JDK (Java Development Kit) is the Java virtual machine (that actually runs the Java programs) *and* the necessary tools for developing programs with Java. JRE (Java Runtime Environment) is just the virtual machine. So unless your a developer, go with the JRE.

---

### Post by Sergio.G on 2011-09-19
Hi!
Actually, Ubuntu comes with the ‘java-6-openjdk’ package by default which IMHO works ok, both are maintained. Each have their own set of bugs and fixes, it will depend of your preference or choice if you are a developer or intend to develop as Jagoly and dniMretsaM pointed out.

If you would like to install the JRE Java6 from (sun, now oracle) you can search in Synaptic 

sun-java6-jre
sun-java6-plugin

and accept all the other dependencies as well.

You can run openjdk and java6 side by side, but you have to tell Ubuntu which is your preferred application, you do that by opening the command line and type this:

sudo update-alternatives --config java
sudo update-alternatives --config javaws
sudo update-alternatives --config mozilla-javaplugin.so

Here are my outputs
```

sergio@petunia:~$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 


```

```

sergio@petunia:~$ sudo update-alternatives --config javaws
There are 2 choices for the alternative javaws (providing /usr/bin/javaws).

  Selection    Path                                        Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/javaws   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/javaws   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/javaws       63        manual mode

Press enter to keep the current choice[*], or type selection number:

```

```

sergio@petunia:~$ sudo update-alternatives --config mozilla-javaplugin.so
There is only one alternative in link group mozilla-javaplugin.so: /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
Nothing to configure.

```


Hope it helps,
Cheers!

---

### Post by Jagoly on 2011-09-19
> **dniMretsaM said:**
> Isn't this installed by default? You could also install SunJava from the repos. And in case your wondering what the difference between JDK and JRE is:
JDK (Java Development Kit) is the Java virtual machine (that actually runs the Java programs) *and* the necessary tools for developing programs with Java. JRE (Java Runtime Environment) is just the virtual machine. So unless your a developer, go with the JRE.

](*,) forgot about that.

Generally, to run a jar file, right click and then hit properrties, then head to the permissions tab then check "allow executing as program". Then close the properties window, and right click and press open with openjdk. You can set it to open with java by default.

---

