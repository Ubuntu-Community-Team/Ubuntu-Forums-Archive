---
title: "executing/installing packages .sh files"
date: 2011-10-17
forum: Packaging and Compiling Programs
---

### Post by 1cookie on 2011-10-17
hi

Yes, am struggling with installing a .sh application, namely NetBeans. I've followed the steps in [http://netbeans.org/community/releases/70/install.html#install_windows](http://netbeans.org/community/releases/70/install.html#install_windows) with no joy.

Here's a code stub from my bash:

```

andy@andy-R519-R719:~/Downloads$ ls -l
total 160496
-rwxrwxrwx 1 andy andy 164340736 2011-10-17 18:16 netbeans-7.0.1-ml-javaee-linux.sh
andy@andy-R519-R719:~/Downloads$ sudo apt-get install netbeans-7.0.1-ml-javaee-linux.sh
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netbeans-7.0.1-ml-javaee-linux.sh
E: Couldn't find any package by regex 'netbeans-7.0.1-ml-javaee-linux.sh'
andy@andy-R519-R719:~/Downloads$ 

```I don't understand? Can someone help me install NetBeans? :)

---

### Post by haqking on 2011-10-17
> **1cookie said:**
> hi

Yes, am struggling with installing a .sh application, namely NetBeans. I've followed the steps in [http://netbeans.org/community/releases/70/install.html#install_windows](http://netbeans.org/community/releases/70/install.html#install_windows) with no joy.

Here's a code stub from my bash:

```

andy@andy-R519-R719:~/Downloads$ ls -l
total 160496
-rwxrwxrwx 1 andy andy 164340736 2011-10-17 18:16 netbeans-7.0.1-ml-javaee-linux.sh
andy@andy-R519-R719:~/Downloads$ sudo apt-get install netbeans-7.0.1-ml-javaee-linux.sh
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netbeans-7.0.1-ml-javaee-linux.sh
E: Couldn't find any package by regex 'netbeans-7.0.1-ml-javaee-linux.sh'
andy@andy-R519-R719:~/Downloads$ 

```I don't understand? Can someone help me install NetBeans? :)

It is in the software centre, 6.9 i think.

depending on your ubuntu version and repos

there is also this slightly out of date community docs [https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)

And you have already downloaded it and then doing a apt-get install ?

if you have a sh try running it with ./ first or sh first

---

### Post by ogomoe on 2011-10-17
Download the .sh file.

If you need to be root to install it, use```
sudo sh netbeans-7.0.1-ml-javaee-linux.sh
```If you don't need to be root, just omit the `sudo' at the beginning.

---

### Post by 1cookie on 2011-10-18
ah i see

another shell

```
dash — command interpreter (shell)
```.

I'd have never have got that! Thanks community. I can continue on my JavaEE journey. Thanks again.

:)

---

