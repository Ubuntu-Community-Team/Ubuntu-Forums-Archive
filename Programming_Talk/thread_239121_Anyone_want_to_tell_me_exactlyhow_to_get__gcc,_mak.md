---
title: "Anyone want to tell me exactlyhow to get  gcc, make, etc to work?"
date: 2006-08-18
forum: Programming Talk
---

### Post by PixelCloud on 2006-08-18
Without an internet connection.

In order to get my wireless card working i will need to compile ndiswrapper. 

However, without a working network connection aptget is a no go.

Which packages do i need to download to get everything working correctly? Is there some website that will tell me which Dependencies i need to fullfill?

Switching between ubuntu and windows every 2 minutes i getting quite annoying, and i have be unable to find libc6.deb

---

### Post by Randomskk on 2006-08-18
The "build-essential" package, which seems to be all you need to compile, would install these:
libc6-dev | libc-dev, gcc (>= 4:4.0), g++ (>= 4:4.0), make, dpkg-dev (>= 1.13.5)

In other words, download the .deb for libc6-dev, gcc, g++, make and dpkg-dev from the ubuntu repo, and install them using "sudo dpkg -i <package>.deb".

---

### Post by Buffalo Soldier on 2006-08-18
What you need to install is the **build-essential** package. It contains all the essential compilers and tools for making a Debian package. And if I'm not mistaken (forgive me if I am) it's available in the instalation CD. Make sure your repository list file (**/etc/apt/sources.list**) contains an entry for the CD. Example:
```
**[color=red]deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted[/color]**

deb http://tw.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://tw.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://tw.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://tw.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```
After that just apt-get as usual.
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by PixelCloud on 2006-08-21
going to try this tactic with the cd. thanks

---

