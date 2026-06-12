---
title: "How to install java SE on my Ubuntu 8.04 LTS?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Sublime John on 2008-09-14
Hi, I'm new to ubuntu and i have a real problem with some things(I love ubuntu system and how it works), to start with, how do I install java SE on my ubuntu computer? I need it for compiling .java files to class files (programming stuff). I got a .bin file on my computer when i downloaded it, how do I install it? It says that there is no application for that type of file... I downloaded the Linux version of java, is that the same thing as ubuntu? However, I have another pretty serius problem. My computer is the worst piece of junk the world will ever see (I hope...) and ubuntu 8.04 is a little bit too hardcore for my computer, it lags and sometimes freezes. I know that I should have read all the requirements and stuff but my computer is very worn - out. If you can help me please do.

---

### Post by Mornedhel on 2008-09-14
Allow me to introduce you to your new friend, the package manager.

Downloading installers directly from the website and executing them is not advised (not necessarily dangerous, but messes with library dependencies, isn't as easy to update...)

Start the Synaptic Package Manager from System > Administration.

In the main window, you'll find thousands of packages. Somewhere in the list are :

sun-java6-jdk
sun-java6-jre
sun-java6-plugin

Mark them for installation, click apply, watch as Synaptic does everything for you. You might want to install sun-java6-doc as well, but this requires a small additional manipulation.

---

### Post by shafi on 2008-09-14
> **Sublime John said:**
> Hi, I'm new to ubuntu and i have a real problem with some things(I love ubuntu system and how it works), to start with, how do I install java SE on my ubuntu computer? I need it for compiling .java files to class files (programming stuff). I got a .bin file on my computer when i downloaded it, how do I install it? It says that there is no application for that type of file... I downloaded the Linux version of java, is that the same thing as ubuntu? However, I have another pretty serius problem. My computer is the worst piece of junk the world will ever see (I hope...) and ubuntu 8.04 is a little bit too hardcore for my computer, it lags and sometimes freezes. I know that I should have read all the requirements and stuff but my computer is very worn - out. If you can help me please do.

Ver simple,
open a terminal and type:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by djheadley on 2008-09-21
What about those of us who have to have java installed in order to get on the internet?  I still have Netzero and until I can find another isp (only dialup is offered here) that has phone #s where I need them I am stuck with them.  I downloaded the jre for linux from sun, copied it to the dir I wanted in, did chmod, tried to run the bin file and nothing happens - no eula or anything!

---

### Post by Mornedhel on 2008-09-21
A general method for offline installation.

You can grab the packages from packages.ubuntu.com.

Specifically, for sun-java6-jre, which if I understand correctly is what you're looking for, you only need to get sun-java6-jre and sun-java6-bin. Their dependencies are available from the Ubuntu installation CD.

---

