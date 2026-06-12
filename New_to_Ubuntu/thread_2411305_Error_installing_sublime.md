---
title: "Error installing sublime"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by ziadhorat on 2019-01-28
Hi, i'm new to the forum and Ubuntu/Linux in general, moved over primarily due to Bash + Vim etc.


I've recently spent about 3 hours trying to install Sublime 3, i tried commands to install via apt from a host of different websites, aswell as downloading the package for 64 bit and running that all to no avail.

I keep coming to the following error: E: Package 'libstdc++6-4.8-dbg-arm64-cross' has no installation candidate
Initially there were 2, however i googled the other package and it was a simple install, however whenever i try to install this particular package it says it exists.

Any help would be appreciated! 
Thank you

---

### Post by ziadhorat on 2019-01-28
SOLVED: If anyone else gets this error trying to install sublime, just skip installing this package, seems to work without it.

---

### Post by 1clue on 2019-01-28
I used this one.

[http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/](http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/)

The error you get suggests that you're trying to install on an arm processor? Sublime AFAIK is not available for ARM.

---

