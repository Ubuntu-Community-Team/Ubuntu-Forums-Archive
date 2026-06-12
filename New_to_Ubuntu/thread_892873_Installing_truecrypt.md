---
title: "Installing truecrypt"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by sharrakor on 2008-08-17
So I'm trying to install my first program, Truecrypt. I'm on a trip, and need to access my files (encrypted because I didn't want security to waste time checking my usbs).

The problem is, I don't know where to start. I download it from the truecrypt website... then what do I do?

---

### Post by K2712 on 2008-08-17
Take a look here:

[http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Compile+and+Install+TrueCrypt+5.1a+on+Ubuntu+8.04+LTS+(Hardy+Heron)/b5ibl](http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Compile+and+Install+TrueCrypt+5.1a+on+Ubuntu+8.04+LTS+(Hardy+Heron)/b5ibl)

---

### Post by sharrakor on 2008-08-17
Thanks. what do I put for "uname-r" if I'm running the LiveCD though?

---

### Post by t0p on 2008-08-17
This might not be what you want to hear: but I think Truecrypt is an awful program.

In my opinion, **cfs** is a far superior utility for created encrypted filesystems. And its in the repos.

```
sudo apt-get install cfs
```

---

### Post by sharrakor on 2008-08-17
I encrypted it with truecrpt.

What do I put for uname-r?

By the way, I get this error installing cfs:

ubuntu@ubuntu:~$ sudo apt-get install cfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cfs

---

### Post by t0p on 2008-08-17
> **sharrakor said:**
> I encrypted it with truecrpt.

What do I put for uname-r?

Sorry, I don't understand the question.  **uname -r** is a command you type into a terminal to find out what kernel you're running.  Like:

```
t0p@ubunty:~$ uname -r
2.6.24-16-generic

```


> **sharrakor said:**
> 
By the way, I get this error installing cfs:

ubuntu@ubuntu:~$ sudo apt-get install cfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cfs

Strange... cfs is in the universe repository.  You're using a Live CD, right?  Surely the universe repo is enabled??  You do have internet acces, right?

Anyway, thinking about it, cfs probably wouldn't be much good used from Live CD. I think it's really for an installed system.

---

### Post by sharrakor on 2008-08-17
I'm using the Live CD with internet access.
I'm trying to install truecrypt from wine, but it keeps getting stuck at the checking drivers part of the install. Any ideas? I can't get it to intall with that guide... I keep getting errors, and can't open the tmp directory.

---

### Post by Unanimated on 2008-08-17
> **sharrakor said:**
> I encrypted it with truecrpt.

What do I put for uname-r?

By the way, I get this error installing cfs:

ubuntu@ubuntu:~$ sudo apt-get install cfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cfs
That means..:
```
sudo apt-get update
```

---

### Post by t0p on 2008-08-17
> **sharrakor said:**
> I'm using the Live CD with internet access.
I'm trying to install truecrypt from wine, but it keeps getting stuck at the checking drivers part of the install. Any ideas? I can't get it to intall with that guide... I keep getting errors, and can't open the tmp directory.

Do you really need to install truecrypt from wine?  Truecrypt is available in a Linux version.

[www.truecrypt.org]("http://www.truecrypt.org")

---

### Post by t0p on 2008-08-18
> **t0p said:**
> This might not be what you want to hear: but I think Truecrypt is an awful program.


I have reevaluated Truecrypt.  It was a long time ago that I tried it last, and the curent version (6a) is much better.   In fact, it's pretty cool.

Unfortunately, Easycrypt (a simplified front-end for Truecrypt) doesn't seem to be working properly with Truecrypt 6a.  But bug reports have been filed on this issue, so hopefully it'll be fixed soon.  Then I'll be able to try Easycrypt too - something I've read lots of good reports on.

I still like cfs.  And I intend to try encfs soon.  My my, aren't we spoiled for choice of encryption utilities in ubuntu!

---

### Post by hyper_ch on 2008-08-18
if you want multi-plattform compatibility then truecrypt is the way to go. Furthermore the "traveller disk setup" where the truecrypt binary for windows is stored on the stick and which can be started through an autorun file is also quite nice as most people, you want to exchange data with, probably don't have TC installed.

---

