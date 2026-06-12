---
title: "Java se Development Kit"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by anderskitson on 2008-05-22
I have to install the Java se Development kit for a sdk of a program as a prereqisite, the problem I have is after I chmod 755 the file then ./"file"
everything works fine, but when the license agreements loads up its a blank box and I cant do anything, so is this common?

---

### Post by stchman on 2008-05-22
> **anderskitson said:**
> I have to install the Java se Development kit for a sdk of a program as a prereqisite, the problem I have is after I chmod 755 the file then ./"file"
everything works fine, but when the license agreements loads up its a blank box and I cant do anything, so is this common?

Type this in a terminal:

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This will install the JRE, fonts, browser plugin (32 bit only), and the JDK compiler.  Netbeans is also in the repos.

---

### Post by anderskitson on 2008-05-22
Wait so is that so I can view the text box?

---

### Post by stchman on 2008-05-22
After the install of the JRE and JDK you can type:

java

javac 

in a terminal to compile and run Java programs.

---

### Post by Inxsible on 2008-05-22
Unless you are going to code/develop java programs, you do not need the SDK. All you need to run java programs is the JRE.

You can install jre using stchman's command but exclude the package sun-java6-jdk, unless you have a need for it.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by anderskitson on 2008-05-22
I will need to create programs, but I am not going to be doing it most likely, I am installing a open source cancer database program for a hospital lab, java sdk is one of the prerequisites. They have prebuilt tools in java for the program, but they also want to build some custom ones for there lab. They are going to get some comp sci students to help me later.

In the install instructions it talks about Environmental variables these are the instructions.
> Verify that the environment variables ANT_HOME and JAVA_HOME are set and
that your PATH statement includes the locations of the Ant and Java binaries. For
7
example., PATH should include C:\apache-ant-1.6.5\bin;
C:\j2sdk1.4.2_06\bin. 

what am i supposed to do, mind you there instructions are for windows

---

### Post by Inxsible on 2008-05-22
Well, in that case, you should use the entire command that stchman provided. Once you do that, the Java environment variables will be automatically set.

About Ant, well you also have to install Ant. But I am not sure if it is in the repos. You may have to manually install Ant, if its not.

---

