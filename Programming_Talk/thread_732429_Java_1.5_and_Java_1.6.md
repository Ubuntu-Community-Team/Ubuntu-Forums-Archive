---
title: "Java 1.5 and Java 1.6"
date: 2008-03-22
forum: Programming Talk
---

### Post by mario2409 on 2008-03-22
Can both of them be installed on the same machine?  If so, how can I install 1.5 in an ubuntu machine with 1.6 already installed.  I ask this because I am writing a java program in eclipse which should only work under 1.5.  Any help would be appreciate it.

---

### Post by nanotube on 2008-03-22
yes you can, just open synaptic and select the packages.

---

### Post by mario2409 on 2008-03-23
I did look for java 1.5, and selected java-package which supposly contains 1.5.  It installed sucessfully but once I tried to create a project in eclipse and I try to select a different JRE it doesn't show 1.5 :(  And I did try for Eclipse to look for different JREs installed and no sucess, any suggestions?

---

### Post by nanotube on 2008-03-24
ok, so the java5 package would be called "sun-java5-jdk"

the binaries would go here i think:
/usr/lib/jvm/java-5-sun/jdk/bin/

so you can find your javac in there, and that would be the java5

your java6 would of course be in
/usr/lib/jvm/java-6-sun/jdk/bin/

your /default/ javac would be in /usr/bin/javac, and will point to /etc/alternatives/javac

you can change your default java by using "sudo update-alternatives javac" 

or you can just use java5 javac directly by funding it in that dir i posted above.

hope that helps.

---

