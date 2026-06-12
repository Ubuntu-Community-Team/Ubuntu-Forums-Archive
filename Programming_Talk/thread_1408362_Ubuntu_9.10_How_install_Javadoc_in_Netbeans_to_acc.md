---
title: "Ubuntu 9.10 How install Javadoc in Netbeans to acces realtime descriptions"
date: 2010-02-16
forum: Programming Talk
---

### Post by Enav on 2010-02-16
Description:
-----------------
- Every time you click on "Show Javadoc" this fail and show nothing
- Every time the Javadoc windows pop up it says "javadoc not found. either javadoc documentation"

Details:
 -----------------
- Ubuntu 9.10 by default is not using "sun-java6-jdk" instead it is using "openjdk-6-jdk"
- If you try to install "sun-java6-doc" the system thrown an error and some times crash
- To solve the problem you need to install "openjdk-6-doc"

Solution:
 -----------------
1) Close "Netbeans"
2) Open "Synaptic Package Manager"
3) Quick search for "openjdk-6-doc"
4) Mark and Install that package
5) Open "Netbeans"
6) Enjoy :D


:arrow: Remember to send a reply, if this information solved your problem

---

### Post by Logical Dream on 2010-02-17
for me its still not working after installing open docs ; 
I installed it true terminal , guess that can not be problem

---

### Post by Reiger on 2010-02-17
You probably refer to platform (JDK) javadocs:

Tools -> Java Platforms -> fill in the zip file under the Javadoc tab of the platform you want.

---

### Post by Logical Dream on 2010-02-17
I guess I wil set it up later , I have issue now with setting path and Java Home .
Is there any newer link for complete setting Java on Ubuntu , as I cant find proper tutorial

---

### Post by Reiger on 2010-02-17
OpenJDK is via the package manager; however for Lucid Lynx at least the SUN Java packages have been dropped.

Still, as long as you stick to OpenJDK Netbeans ought to figure everything out by itself.

---

### Post by Turgon_Noldor on 2011-03-01
Worked like a charm.
Thank you.

Note: installing openjdk-6-doc solves the same problem with eclipse

---

