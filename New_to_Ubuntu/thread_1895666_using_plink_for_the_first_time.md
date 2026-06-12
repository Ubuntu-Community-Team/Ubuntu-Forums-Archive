---
title: "using plink for the first time"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by KerryAP on 2011-12-15
I'm new to ubuntu, and have installed plink (plink-1.07-x86_64), but when I input 'plink' it says: 

The program 'plink' is currently not installed.  You can install it by typing:
sudo apt-get install putty-tools

But when I try that...

ubuntu@ubuntu-OptiPlex-GX520:~$ sudo apt-get install putty-tools
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package putty-tools

I then tried:
sudo apt-get update putty
E: The update command takes no arguments

What am I missing??:confused:

---

### Post by SlugSlug on 2011-12-15
can I ask why you need plink?

try 
sudo apt-get update 
sudo apt-get install putty-tools

---

