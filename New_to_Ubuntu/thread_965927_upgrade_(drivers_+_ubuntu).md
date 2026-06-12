---
title: "upgrade (drivers + ubuntu)"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Beshaba on 2008-10-31
Hi,

1. I tried to upgrade my graphic drivers. I really tried but I can't figure how to do it. I used these links.

[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

I am looking for more instructions on how to upgrade these Intel drivers. 

2. I tried to upgrade from 7.10 to 8.04. It worked perfectly, except that when I restarted the computer, I had to boot on another kernel (temporary boot, kernel 2.6.22-14 generic). 
I found the tutorial on how to boot permanently, but I am afraid of crashing the computer for good by making a mistake.
Any other tutorial to comfort me? Any advice on how to boot smoothly permanently with another kernel?

---

### Post by martrn on 2008-10-31
> **Beshaba said:**
> I tried to upgrade my graphic drivers. I really tried but I can't figure how to do it. I used these links.
[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)


Most software for ubuntu is stored in the ubuntu repositories.  There are GB's of software in the ubuntu repositories including kernel modules (drivers) and kernels, so it should not be too much of a problem to install what you need from there.  It even says that on one of your linux that kernel-module/driver packages could be obtained from public repositories.  These would be the ubuntu repositories if you are using ubuntu, wich would be the same place you could get any software package from like cards or LTetris or anyting you have installed on your workstation.

> **Beshaba said:**
> I am looking for more instructions on how to upgrade these Intel drivers. 
[http://packages.ubuntu.com/hardy/xserver-xorg-video-intel]("http://packages.ubuntu.com/hardy/xserver-xorg-video-intel")
If you are running ubuntu8.04 (hardy) from the Konsole/Terminal Try :
```
sudo apt-get install xserver-xorg-video-intel
```

Menu--> Utilities-->Terminal 
to get a terminal.

> **Beshaba said:**
> I tried to upgrade from 7.10 to 8.04. It worked perfectly, except that when I restarted the computer, I had to boot on another kernel (temporary boot, kernel 2.6.22-14 generic). 
I found the tutorial on how to boot permanently, but I am afraid of crashing the computer for good by making a mistake.
Any other tutorial to comfort me? Any advice on how to boot smoothly permanently with another kernel?

Linux Base Utilities include many kernels.  There are kernels for server systems that are optimised for disk use and not using screens.  There are generic kernels for general purpose workstations, and real-time (rt) kernels optimised multimedia work such as audio and video processing (plus others).   See
[http://packages.ubuntu.com/hardy/base/]("http://packages.ubuntu.com/hardy/base/") and try 
```
sudo apt-get install linux-image-2.6.24-16-generic
```
to install the generic kernel or any kernel image on that page.

Install all or as many kernels as you like, the more kernels you install the more you have to fall back on if one doesn't work or is not quiet right.  Don't be scared of installing one too many kernels.

---

### Post by Beshaba on 2008-11-02
Tanks. I am going to work on it and will come back soon with good news-hopefully.

---

### Post by Beshaba on 2008-11-02
Thanks. I am going to work on it and will come back soon with good news-hopefully.

---

