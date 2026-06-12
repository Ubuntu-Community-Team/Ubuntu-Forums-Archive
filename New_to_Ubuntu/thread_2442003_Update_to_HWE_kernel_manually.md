---
title: "Update to HWE kernel manually"
date: 2020-04-28
forum: New to Ubuntu
---

### Post by peterthegreat2 on 2020-04-28
Hello, I have installed arm64 Ubuntu 18.04 LTS LXDE using the Linux Deploy app on Android in a chroot environment. My SOC is a Snapdragon 855 (Adreno 640 GPU). Literally yesterday, I was able to install mesa and get hardware acceleration working. Unfortunately, I messed that session up in an unrelated way and decided to start from scratch instead of reverting my actions (I should've backed up!). Unfortunately my memory isn't great but I simply don't remember getting this error yesterday from the same command. In order to use the drivers, I must update my kernel. Here is the PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers), and the command given is the standard:

```
sudo apt install --install-recommends linux-generic-hwe-18.04
```

However the error that I'm getting that I don't recall getting yesterday is:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-generic-hwe-18.04
E: Couldn't find any package by glob 'linux-generic-hwe-18.04'
E: Couldn't find any package by regex 'linux-generic-hwe-18.04'
```

I did an apt-cache search and found out that only 16.04 packages are there. Here's a random snippet:

```
linux-virtual-hwe-16.04 - Minimal Generic Linux kernel and headers (dummy transitional package)
linux-virtual-hwe-16.04-edge - Minimal Generic Linux kernel and headers (dummy transitional package)
fonts-sil-taiheritagepro - typeface reflecting the traditional hand-written style of the Tai Viet script
libarchive-any-lite-perl - simple CPAN package extractor
r-cran-slam - GNU R sparse lighweight arrays and matrices package
ruby-sinatra - Ruby web-development dressed in a DSL
xmir-hwe-16.04 - Transitional package for xmir-hwe-16.04
xorg-server-source-hwe-16.04 - Transitional package for
xorg-server-source-hwe-16.04
xserver-xephyr-hwe-16.04 - Transitional package for
xserver-xephyr-hwe-16.04

```
My repository ports.ubuntu.com does have 18.04 packages, it's all visible in a browser, but for some reason it's not available to install. So my two questions are: 

1. How do I get the correct packages in the apt-cache?
2. If it's easier, how do I manually install an HWE stack using .deb downloads from [http://ports.ubuntu.com/pool/main/l/linux-hwe?](http://ports.ubuntu.com/pool/main/l/linux-hwe?)

As you can see in the link, there is a mix between 16.04 and 18.04 versions, I need specifically 18.04 and arm64 architecture. Anything past Linux kernel 5 is good for me.

Output of uname -sr:

```
Linux 4.14.176-iMMENSITY-g4fff1070
```

(This is my android kernel)

The real hope for me is that I got it working yesterday. I have no idea about this kernel stuff, the fact that I don't remember from yesterday proves that I didn't pay attention to it which means it must've went really smooth. This is a fresh install so I don't know what could be wrong. glxgears ran at around 200-220 fps when it worked yesterday, now since the drivers aren't installed it's giving me the no RGB error.

Any help is greatly appreciated!

---

### Post by wildmanne39 on 2020-04-28
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by CatKiller on 2020-04-28
> **peterthegreat2 said:**
> I need specifically 18.04 and arm64 architecture. 

I have no idea what's going on there, but the *bionic-updates* repository has arm64 builds of linux-generic-hwe-18.04 even though the *bionic* repository doesn't; bionic seems to only have amd64 and i386 for whatever reason.

---

