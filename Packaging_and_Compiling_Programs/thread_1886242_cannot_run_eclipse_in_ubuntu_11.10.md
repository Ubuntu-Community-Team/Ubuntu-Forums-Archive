---
title: "cannot run eclipse in ubuntu 11.10"
date: 2011-11-24
forum: Packaging and Compiling Programs
---

### Post by cosoikez on 2011-11-24
Hello, everybody!
I upgrated my ubuntu from 10.04 to 11.10 release and I have the problem below. When I run the eclipse then the following error message occurs:
------------------------------------------------------------------------------------------
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/eclipse/jre/bin/java
java in your current PATH
------------------------------------------------------------------------------------------

I have already installed java in my pc and when I run sudo update-java-alternatives then the output is: 

java-1.6.0-openjdk 1061 /usr/lib/jvm/java-1.6.0-openjdk

However in the /usr/lib/jvm directory there are also exist the :

default-java  java-1.5.0-gcj-4.6  java-1.6.0-openjdk  java-6-openjdk

folders. 

I have multiple times installed and uninstalled the eclipse program, but the same error returns. 

I have already followed the instructions of [https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE), however I had no solution to my problem.

Do you have any idea about what can be going wrong?

Thanks in advance.

---

### Post by ptrakk on 2011-11-24
try 'ln -s /usr/bin/java /usr/lib/eclipse/jre/bin/java'
basically it is looking in your eclipse folder for java instead of your bin folder. that command creates a shortcut to it in your eclipse folder.

---

### Post by cosoikez on 2011-11-24
Actually there is no folder /usr/lib/eclipse/jre/bin/java. 
Inside the /usr/lib/eclipse/ exist only the folders below:

about_files    buildscripts   debian-swt  eclipse      features  plugins
artifacts.xml  configuration  dropins     eclipse.ini  p2

However, in my office I have the same release installed, where eclipse runs without problem and there the output of the directory is also the same to the one above.

---

