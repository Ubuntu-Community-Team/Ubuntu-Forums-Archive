---
title: "Setting environment variables for  jdk6 and Maven on Ubuntu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by library on 2008-05-29
Dear all,
Greetings
Iam newbie here and to Ubuntu.I have installed ubuntu 7.04 desktop on my computer. Also I have installed java6 through synaptic manager. 
Testing java
When I type
*java -v on the command line it is working*
when I type 
[I]echo $JAVA_HOME  no output
[/I]

I tried to such through the old posts, got some ideas but did manage to make it work.
The problem is to find the proper location of java file because I can find it in /usr/local/jvm and /usr/local/java and /usr/java/bin.I dont know whcih is which.

I have tried to edit bash file but didnt work and found one post describing to make separate script like bash_profile,but I dont know where to place it.
similar for maven
thank for you help

---

### Post by RealPSL on 2008-05-29
I am not sure if you installed the runtime or the sdk but either will work here. The name of the sdk package is java6-sdk and the runtime is java6-runtime. A quick way to determine the location of the installation is 

```
dpkg --listfiles java6-sdk
```. Replace the sdk package name with the runtime as appropriate.

You can use the above command to determine the location JAVA_HOME. Once you determine what JAVA_HOME is you can add it to your .profile as
```
JAVA_HOME=/some_path; export JAVA_HOME
```

---

### Post by library on 2008-05-30
RealPSL

Thanks for your help.I will give a try a later after solving problem of login

late you  know

---

### Post by library on 2008-05-30
Sorry, I have simple question,You said

Once you determine what JAVA_HOME is you can add it to your .profile as

How can add it on the .profile?.please,anyone can show me how to do it.

Thank you again

---

### Post by RealPSL on 2008-05-31
From the menu:

Applications > Accessories > Text Editor

When it comes

File > Open

Choose your home directory as the current working directory on the left. Enter ".profile" in the location window.

Edit your file and save it. Log out and back in to view the change.

You can check the change the the shell prompt with echo $JAVA_HOME. 

You can also make the change from the command prompt using gedit ~/.profile.

---

