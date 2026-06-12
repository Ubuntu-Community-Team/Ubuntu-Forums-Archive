---
title: "Trying to install openssl"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by bwbritt86 on 2014-01-06
Distribution: Lubuntu 13.10
CPU Architecture: i386

I'm completely new when it comes to anything Linux so please bear with me.
I downloaded the .deb file to my desktop and tried to install it with Gdebi Package Installer. I got the message "Error: Dependency is not satisfiable: libcurl3 (=7.34.0-1)". 

So I then tried to install it using Xterm.
```
sudo apt-get install libcurl4-openssl-dev-7.34.0-1_i386.deb
```
but I keep getting this
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libcurl4-openssl-dev-7.34.0-1i386.deb
E: Couldn't find any package by regex 'libcurl4-openssl-dev-7.34.0-1_i386.deb
```

I've already tried updating apt-get using the terminal. Not sure what to try next. 

I need to have an IRC server up and running by the end of the week. I will be using Anope 1.8.8 and Unreal 3.2.10.2. So any help in that area will be appreciated as well.

---

### Post by QIII on 2014-01-06
The version of libcurl3 in the Saucy repo is 7.32.

Is there some reason you did not install openssl from the repo?

---

### Post by bwbritt86 on 2014-01-06
Did a synaptic search and found that libcurl3 was in there. I totally thought that libcurl4 was actually an updated version - no wonder I was getting error messages. See, I'm trying to follow an installation tutorial to the letter so I don't screw something up.
Thank you for clarifying that there was already an openssl package in the distribution.

---

