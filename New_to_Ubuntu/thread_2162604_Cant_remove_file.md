---
title: "Cant remove file"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by cnra on 2013-07-15
I was following a guide to get java for my browser, but something was messed up while copying the Tar from the download folder to /usr/local/java. Instead of a java folder I now have a java file in local which I'm unable to remove niether with the file manager nor the rm command in terminal window. I have tried to restart in case the file was locked by a program, but no succes. How to proceed?

---

### Post by dannyboy79 on 2013-07-15
since /usr/local/ is owned by root, only root can move it or delete it. you can use sudo to do what you want to the file.

---

### Post by leunam12 on 2013-07-15
sudo rm -rf foofile

---

### Post by dannyboy79 on 2013-07-15
PLEASE BE VERY CAREFUL using leunam12 command, -rf is very DANGEROUS!

---

### Post by cnra on 2013-07-15
THX guys - it worked. To bad the java part didnt.. :-S

---

### Post by Cheesemill on 2013-07-15
The easiest way to install Java is to run the following 3 commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

This information can be found on the Ubuntu Wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Cheesemill on 2013-07-15
The easiest way to install Java is to run the following 3 commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

This information can be found on the Ubuntu Wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by ajgreeny on 2013-07-15
Do you really need Oracle-java or will openjdk version not work for your purposes.

It is many years since I installed Sun (now Oracle) -java, and I have no problems using any web-pages from my bank, or anywhere else.

---

### Post by cnra on 2013-07-15
>Cheesemill

I just need the browser-plugin, I've allready got Java running, and I created a link for the browser as explained in the guide, but for some reason it do not start up when I go to a webpage with Java..

---

### Post by QIII on 2013-07-15
Hello, cnra --

We don't know what guide you used, so it is impossible for us to even take a stab at what might have gone wrong.

I will tell you that most guides are unnecessarily esoteric and do not install Java in a manner consistent with the way that Ubuntu's package manager does.  That sometimes makes things difficult to diagnose or remove.

The directions Cheesemill provided are the most effective way to install Oracle Java 7 on Ubuntu, since webupd8.org has made it consistent with Ubuntu's package management.  Also, when Oracle releases updates, the files are updated automatically when you do your normal updates.

Using webupd8's method, you do not need to bother with symlinks.  All of that is taken care of.

If you run those commands now, regardless of what you may have done before, Oracle Java 7 will be installed and properly configured for use -- including the browser plugin.

Cheers!

---

### Post by cnra on 2013-07-15
Well I took the advice and tried, but still has problems..

Now when I go to a webpage with java, chrome tells me that my java version is outdated, but if I test java version in terminal window, it says 1.7.0.25 (newest version). If I tell Crome to run java anyway, the java box on the webpage just turns in to a grey box. Any suggestions?

---

### Post by cnra on 2013-07-16
Hmm - think I'll move this problem to a new thread. No need to answer here - thx for the help guys :-)

---

### Post by Elfy on 2013-07-16
Thread closed.

---

