---
title: "Songbird won't install!"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-08-13
After posting earlier asking about itunes alternatives, I settled on Songbird, but now I can't get it to install on my laptop. I can download the file and extract it no problem, but when I try to run the sudo apt-get install Songbird command, it comes up saying the following:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Songbird

any ideas what I'm doing wrong here and how to fix it?

---

### Post by SunnyRabbiera on 2008-08-13
Thats because its not in the repositories, and the method you suggest is totally wrong sorry to say.
Go here:
[http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird)

that will give you a debian package to install it with.

---

### Post by dje on 2008-08-13
it is not in the ubuntu repository but it is in my personal repository. you can find instructions on installing my repository [here]("http://djeastoe.co.cc/?p=14")
alternatively search [http://getdeb.net]("http://getdeb.net") for a songbird package. my repository has a later version than get deb (0.7 rc2 instead of 0.6.1)
after installing my repo, do:
```
sudo apt-get install songbird
```

hope that helps,
dje

---

### Post by SunnyRabbiera on 2008-08-13
You see the installation method you attempted before, downloading the songbird app from the songbird site and extracting it wont make it install with apt-get...
For a package to install via apt get is to have it in the repositories, or from a third party site like getdeb

---

### Post by Lorelei- on 2008-08-13
ah, that would explain it then and this would also be further proof of utter new-ness to Linux.

---

### Post by SunnyRabbiera on 2008-08-13
> **Lorelei- said:**
> ah, that would explain it then and this would also be further proof of utter new-ness to Linux.

Yeh it does indeed.
Most .tar packages you may find on the net dont have install scripts nor do they work like windows executables.
The closest you will find in ubuntu is files marked .deb that sort of work like windows installers but are closer to zip files (like .tar)

---

### Post by Lorelei- on 2008-08-13
interesting. and definately something to remember.

oh and I'll try and keep the stupid questions to a minimum from now on, sorry for being a bother this evening.

---

### Post by Dom Rivers on 2008-08-13
> **Lorelei- said:**
> interesting. and definately something to remember.

oh and I'll try and keep the stupid questions to a minimum from now on, sorry for being a bother this evening.

You wait and see some of the nonsense I'm going to have to ask :)

---

