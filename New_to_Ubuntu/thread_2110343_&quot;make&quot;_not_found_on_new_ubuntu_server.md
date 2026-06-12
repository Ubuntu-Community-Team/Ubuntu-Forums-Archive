---
title: "&quot;make&quot; not found on new ubuntu server"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by JiMMaR on 2013-01-30
Hi There,
I've recently installed a fresh ubuntu 12.04 server but apparently "make" is not installed, how can I get it ?
my server has no internet connection, is there any way to get it installed by downloading a package from other computer and copying it on a flash drive ?


Edit: I've failed to do so [since I was booting ubuntu from a usb disk and not cd] so I ended up sharing an internet connection through lan and installing build-essentials through there

---

### Post by mlentink on 2013-01-30
A server without internet connection? How will you install things like security updates?

Anyhow, I don't really know whether they can be installed from cd, but you should:
```
sudo apt-get install build-essentials
```
which will give you make

---

### Post by Nr90 on 2013-01-30
To compile sources I think you'll want to install the build-essential package and all of it's dependencies (make is one of them)
Have a look here: [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)

---

### Post by JiMMaR on 2013-01-30
> **mlentink said:**
> A server without internet connection? How will you install things like security updates?

Anyhow, I don't really know whether they can be installed from cd, but you should:
```
sudo apt-get install build-essentials
```
which will give you make

the server will be used on internal network, I need "make" to build wvdial and connect to the internet for updates and stuff then disconnect it from the internet .. forever ? :P

I'll try this and report back, thanks :D

---

