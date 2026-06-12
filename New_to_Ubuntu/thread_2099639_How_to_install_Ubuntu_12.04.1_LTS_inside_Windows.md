---
title: "How to install Ubuntu 12.04.1 LTS inside Windows"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by suman1989 on 2012-12-30
Hello i am new to Ubuntu. I have recently downloaded the version 12.04.1 LTS and i also have windows 7 running on my PC. I am not able to install Ubuntu inside my windows. please tell me the process how to install Ubuntu inside my windows 7.

---

### Post by 3rdalbum on 2012-12-30
> **suman1989 said:**
> Hello i am new to Ubuntu. I have recently downloaded the version 12.04.1 LTS and i also have windows 7 running on my PC. I am not able to install Ubuntu inside my windows. please tell me the process how to install Ubuntu inside my windows 7.

I'd just like to clarify what you mean.

It is possible to run Ubuntu inside a window on Windows, using virtualisation. In order to start Ubuntu you just double-click on an icon and you will have both systems running at the same time. Ubuntu's performance will be limited because of this, and you will not be able to use all your computer hardware within Ubuntu because it will be locked by the Windows 7 host system. Do you want Ubuntu running inside a window on your Windows 7 desktop?

Some people don't realise that Ubuntu is a self-contained operating system and is fully capable of running as the only operating system on a computer. Is this what you want?

It's also possible to "dual-boot" - that is, when you start your computer, you get the option each time of booting into Windows 7 or into Ubuntu. Only one will operate at any given time. To switch between them, you just need to reboot and choose from the menu. Ubuntu still has full use of the computer when it is running, including graphics acceleration and all your computer hardware. Is this what you want?

To dual-boot or single-boot Ubuntu, burn the Ubuntu ISO image to a DVD using the "Burn image to disc" or "Burn ISO image" function of your DVD burning software. Enter your computer's BIOS setup screen and tell it to boot from DVD before trying to boot from hard disk. Insert the Ubuntu disc and reboot. You will be taken through the options and will be given the option of installing Ubuntu alongside Windows as a dual-boot, or removing Windows and installing Ubuntu.

However, if you wanted the first option - Ubuntu in a window running on Windows - then you need to install a program called Virtualbox, on Windows. This program will allow you to set up a "virtual" computer that you can install Ubuntu into. This virtual computer runs on top of Windows. Therefore, Windows is the "Host OS" and Ubuntu is the "guest OS" and runs in a window.

---

### Post by mörgæs on 2012-12-30
Maybe [Wubi]("https://wiki.ubuntu.com/WubiGuide") is what you are looking for...?

---

### Post by superDave972 on 2012-12-31
> **mörgæs said:**
> Maybe [Wubi]("https://wiki.ubuntu.com/WubiGuide") is what you are looking for...?

When I was first being introduced to the Linux environment, Wubi is what I used. It is easy, and non-disruptive. Also, if you are used to installing applications on Windows, using Wubi will be a piece of cake. Wubi allows the user to install (or uninstall) Ubuntu on a windows machine just like any other application.

---

### Post by Fahim Abdun-Nur on 2012-12-31
Another possibility is to install Ubuntu on a VM (via virtualbox) [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Wubi is great for simplifying the dual boot process, but I *sometimes* find the need to have both OSes

---

### Post by Mark Phelps on 2012-12-31
> **suman1989 said:**
> I am not able to install Ubuntu inside my windows...

Why not?  Telling us what is going wrong when you attempt to install Ubuntu inside Win7 will go a long way to helping us understand what you need to do to work around that.

---

### Post by StevePMo on 2013-01-03
I have a similar question. I have heard that you can install Ubuntu while you are in Windows, I have a dual boot machine now, with Win 7 on a 1 TB drive, and Win XP on a 640 GB drive. I would like to install Ubuntu also. My MAIN concern is the possibility of borking my Windows install (s ) . What are the odds of this happening? And how easy is it to do the install from inside Windows? My plan is to install it from Win XP, IF i was to lose an install, I would prefer it to be XP, as I have migrated most of my files and programs to Win 7, I rarely boot into XP anymore...

---

### Post by Wim Sturkenboom on 2013-01-04
@StevePMo
It is often better to just start your own thread; it can become confusing who replies to who and if you were the thread starter, I'm sure that you would not be too happy to see new answers to your thread that are replies to somebody else's question in the thread.

To answer your question: installing using Wubi (inside Windows) is, in my opinion as a non-Wubi user, less risky than creating a dual boot of Win7 and WinXP as there is no partitioning involved. However, you might end up with two boot menus (e.g. you select WinXP first and next you can choose between WinXP and Ubuntu). I'm sure this can be solved but I'm not the person to help with that.

---

