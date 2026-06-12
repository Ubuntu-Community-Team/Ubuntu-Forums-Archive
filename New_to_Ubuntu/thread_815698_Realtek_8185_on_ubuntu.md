---
title: "Realtek 8185 on ubuntu"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Aarookie on 2008-06-01
I'm trying to get my desktop working with ubuntu as well as the laptop I'm writing this from.  My cable modem and router are behind the TV as this house has limited cable hook ups.  So my desktop is restricted to wireless access.  I've followed several read me's how-to's as far as installing the realtek 8185 via ndiswrapper, but it's not working.  More specifically I can't even get ndiswrapper working, I try to follow the tar.gz commands but I inevitabley get errors.  I'm not able to sudo apt-get because I have no internet on the computer other than wireless.  I can download files in XP and then copy them via file manager.  I dunno what else to put, atm I'm so confused I don't even know what questions to ask.

---

### Post by phidia on 2008-06-01
To compile ndiswrapper you need to have build-essential installed.
You can install that without internet since it's on the cd you installed ubuntu from. 
You would just type > sudo apt-get install build-essential and apt will ask you to insert the install cd.

But Check out the how to for your card [here]("http://ubuntuforums.org/showthread.php?t=772006&highlight=Realtek+8185") because perhaps you can get it working without ndiswrapper from the how to at that link.

---

### Post by Aarookie on 2008-06-01
That article is awesome and fairly straight forward thank you a bunch.  I don't know how to do an official thank you in the forum dealy.  Or I'd add a thanked to your profile thing.

---

### Post by Aarookie on 2008-06-02
do I have to be in a different directory or something to get it to ask for the cd, it just acts like it should be coming from the internet or something

---

### Post by Aarookie on 2008-06-02
woops found it

sudo apt-cdrom add or somethin like that hehe

---

