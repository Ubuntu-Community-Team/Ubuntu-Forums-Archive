---
title: "How to compile cpp programes"
date: 2015-02-07
forum: Packaging and Compiling Programs
---

### Post by priyesh2 on 2015-02-07
Hi..

Sorry for this insane questions, but i searched a lot in google but got nothing.

I have ubuntu-14.04.1-desktop-amd64 installed on my system, but i don't know why g++ compiler is not present.
I have tried different versions, like ubuntu 12.04, fedora, opensuse... but none of them have g++ compiler.

```
priyesh@ubuntu:~$ g++
The program 'g++' is currently not installed. You can install it by typing:
sudo apt-get install g++
```

```
priyesh@ubuntu:~$ sudo apt-get install g++
[sudo] password for priyesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package g++
```

I have .deb g++ file, is there any way to install from .deb file (offline).

Thanks

---

### Post by steeldriver on 2015-02-07
Perhaps something is misconfigured in your repository sources? what happens if you do

```

sudo apt-get update

sudo apt-get install build-essential

```

---

