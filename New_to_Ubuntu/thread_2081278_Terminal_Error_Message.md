---
title: "Terminal Error Message"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by tonybrown on 2012-11-06
Hello - I am a ubuntu newbie and very much still at the beginners stage. I have tried to add brightness control through my terminal, but receive the following message:

tony@Ubuntu-12:~$ sudo apt-get install brightness-control-ext
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brightness-control-ext
tony@Ubuntu-12:~$ 

I followed the instructions and copied/pasted: sudo apt-get install brightness-control-ext, into the terminal. I am sure there is a very simple answer to this, but at the moment, ubuntu is a bit scarey! Can anyone please tell me why this has happened, and how I can solve this problem? Thanks in advance. 
Regards
Tony Brown

---

### Post by Cheesemill on 2012-11-06
You are trying to install something that doesn't exist.

Where did you get these instructions from?

---

### Post by ibjsb4 on 2012-11-06
Are you running Precise 12o4 with gnome-shell and trying to install a PPA?

[https://launchpad.net/~upubuntu-com/+archive/ext/+packages](https://launchpad.net/~upubuntu-com/+archive/ext/+packages)

---

### Post by gordintoronto on 2012-11-06
That program on this web page: 
[https://launchpad.net/~upubuntu-com/+archive/ext/+build/3469377](https://launchpad.net/~upubuntu-com/+archive/ext/+build/3469377)

However: it's only for 32-bit Ubuntu, and it's version 0.1. I would not install a program that was version 0.1

My computer uses an Nvidia proprietary driver, and there's a brightness control in "Nvidia X Server Settings". Perhaps that is why there isn't one in System Settings, Brightness and Lock.

---

### Post by tonybrown on 2012-11-07
Ok I seem to have misunderstood something. Thanks to you all for taking the time to give me your advice. I must start and research eveything from scratch regarding ubuntu installation. I guess you call this a newbie mistake! Thanks again. Regards, Tony Brown.

---

