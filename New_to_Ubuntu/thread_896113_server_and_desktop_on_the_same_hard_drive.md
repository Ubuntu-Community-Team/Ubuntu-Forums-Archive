---
title: "server and desktop on the same hard drive"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-08-20
Hello ya'll,

This is my first post to this forum, I am newbe to Linux and Ubuntu.  I am wanted to build a web server and was told that Ubuntu was the best.  I downloaded the latest server copy and burnt a cd, installed Ubuntu in a clean 10gb hard drive that Ubuntu reformatted and partitioned.  I quickly found out that the server copy is run with the command line only.  

If I download the desktop copy and run it on the same 10gb drive will I have an option come up to keep the server copy and the desktop copy install in the free space?  Will the desktop copy just be added to the GRUB to let me choose which system to boot or will I loose the server copy?  Is this drive large enough for both OS's and have any free space left to work in? I am thinking that I will be able to learn Ubuntu easier from the GUI on the desktop copy and then gradually move to the command line on the server.  

Thanks for any help in advance.

---

### Post by Vivaldi Gloria on 2008-08-20
You can install the ubuntu desktop using the command

```
sudo apt-get install ubuntu-desktop
```

Next time you boot you'll boot to gnome. So this will add the desktop environment on the server system.

---

### Post by Gregmond on 2008-08-20
Not being an expert, my understanding is that the server version is basically a no gui version with several extra services installed by default.
You should actually be able to upgrade the server version to have the gui. 

potentially something like "sudo apt-get install gdm" should do that, but it may not install everything you need so don't take it as gospel.

oooh looks like someone beat me and its ubuntu-desktop not gdm :)

---

### Post by JKHinton CPBD on 2008-08-21
thank you Gregmond and Vivaldi Gloria both for your responses.  

I should have mentioned thats part of my problem no internet connection yet. I have a dual boot system with XP on another hard drive. I have DSL connection on another machine and I have the 2 connected with a cat 5 cable and I know the systems are communicating through my 3 user network through XP but not through ubuntu so far at least I havn't been able to confirm any communication through Ubuntu back to XP on any of the other systems.  I guess I have to get the server copy of Ubuntu to connect to the internet first and then try your solution to getting the GUI to better learn Ubuntu.  Any suggestions on how to get Ubuntu server to connect to my DSL connection and be able to download? These are all desktop units connected with CAT 5 no wireless involved.  

Thanks again.

---

