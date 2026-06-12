---
title: "Advice for which version of Ubuntu would be best"
date: 2023-12-01
forum: New to Ubuntu
---

### Post by archibaldmike828 on 2023-12-01
I have recently bought a Lenovo Ideapad 4G 

Device name    DESKTOP-SC998FA
Processor    Snapdragon (TM) 8c @ 2.46 GHz   2.46 GHz
Installed RAM    8.00 GB (7.55 GB usable)
Device ID    90BCFB0C-95C3-4372-9DDC-D9325B784379
Product ID    00342-20776-24929-AAOEM
System type    64-bit operating system, ARM-based processor
Pen and touch    No pen or touch input is available for this display

I want to put a linux distro on it.  This is where I put my hand up and say that I didn't realise what an arm processor was.  Preferably one that is relatively simple to install.

Once it's installed would it be able to run the majority of available apps?

Many thanks in advance.

---

### Post by TheFu on 2023-12-01
I don't have any Lenovo computers, so I really don't know anything exactly.  OTOH, I was paid as a cross-platform software developer for over a decade, supporting many OSes and many different CPU architectures, so hopefully, I'm not completely full of you-know-what. ;)

> **archibaldmike828 said:**
> I have recently bought a Lenovo Ideapad 4G 

Device name    DESKTOP-SC998FA


A few friends bought cheap Ideapads and had nothing but problems getting different parts of the hardware to work.  About a year later, they did finally manage to manually install some drivers, after lots and lots of learning, googling, etc. but it is wasn't an easy install.  

> **archibaldmike828 said:**
> 
I want to put a linux distro on it.  This is where I put my hand up and say that I didn't realise what an arm processor was.  Preferably one that is relatively simple to install.


The only way to actually KNOW if any OS will or won't work on any specific hardware is to try it out: [https://askubuntu.com/questions/986878/will-my-device-work-with-ubuntu](https://askubuntu.com/questions/986878/will-my-device-work-with-ubuntu) Short of that, it is a guess.

Computer chips all have different instruction sets.  That's why PowerPC-based MacOS systems all didn't work with x86-based software even running MacOS.  Now again, Apple decided they didn't like people being able to build much more powerful systems, cheaper than Apple wanted to sell them based on x86-64 CPUs, so they decided to take full control of the hardware chain and created the Apple M1 and M2 Arm-based CPUs.  These are only available from Apple and the current MacOS only supports those CPUs.

ARM-based CPUs have been used for lower-end desktops/servers for about a decade.  The are typically what smart phones and tablets use, but there are different models of ARM CPUs.  Sorta like how there are different models of Intel CPUs - Atom, Celeron, Pentium, Core i3/i5/i7/i9 and Xeon.  The basic instruction set is the same, but some models have more or less actual instructions designed for specific types of processing.

In short, you'll need to only get software that is made for ARM CPUs of the major type the Ideapad has.  You won't be downloading any x86 or amd64 software, at least if you expect it to work on that system.  

The good news is that Linux is architected to be cross-platform, so there are many different platforms which are supported by the core Linux kernel and userspace tools.
The bad news is that Canonical doesn't support every possible CPU architecture.  They dropped 32-bit x64 CPUs a few years ago.  No Ubuntu from 20.04 and later supports 32-bit CPUs.  It was a business choice.  This means that you'll have problems trying to run 32-bit Linux software on Ubuntu-based systems.  That might be absolutely critical or completely unimportant - just depends on the exact software you want to run.

> **archibaldmike828 said:**
> 
Once it's installed would it be able to run the majority of available apps?


Most desktop and server software will work on both ARM64 and x86-64 Linux systems. You won't be able to tell the difference.  Some highly complex software doesn't, but I can think of only 1 software that wasn't ported to ARM and it is unlikely 99.9999% of the world would use it.

Majority of apps?  Most definitely and if you are a typical user, not using many PPAs, then I wouldn't expect many exceptions.  It will probably be fine.   Er ... until it isn't.

Which OS should you use?  Well, Debian has the widest support for different Linux architectures, so for the widest support, debian would be my recommendation.  With any ARM-based CPU, you'll want to stay on the lower-end of fancy graphics, since I can't imagine a very powerful GPU would be possible.  That would be a GUI like XFCE, Mate, LXQt, Budgie [https://ubuntubudgie.org/](https://ubuntubudgie.org/)  or PopOS.  

There are ways to have even lighter GUIs, but those aren't beginner friendly.

---

### Post by ian-weisser on 2023-12-01
> **archibaldmike828 said:**
> Once it's installed would it be able to run the majority of available apps?

The majority of available **Linux** applications. Not Windows applications. Not MacOS applications.
Applications that are built for your release of Ubuntu (plus snap applications, of course).

Applications in the (huge) Ubuntu deb repositories and Snap store will work and are supported here.
Random software you find on the dirty, dirty internet is more of a "depends" answer.

---

### Post by dakspyker on 2023-12-05
Hi,

I use KUbuntu 23.10 for almost two months now on my Lenovo Ideapad 3. I have a slight issue with the bootup sequence (search my userid posts and you will see the problem) but it is no big deal and the system runs stable with no other issues. 

All the software I need runs fine, Firefox, Thunderbird, Dropbox, Obsidian, digiKAM, office suite etc.

J

---

