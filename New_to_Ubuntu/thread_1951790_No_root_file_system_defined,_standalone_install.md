---
title: "No root file system defined, standalone install"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by QQQ6 on 2012-04-03
Sup. I'm a complete rookie when it comes to Linux.

I just got a Ubuntu 11.10 boot CD (Wubi) and I want to install it on a clean HDD. 

I only have that one drive, so I don't want dual boot or anything like that - just an HDD that automatically boots Ubuntu when I turn on the computer.

The problem is that when I boot using the CD, I can't do anything in the setup because the partition list is empty and when I click "Install", it says "No root file system defined" etc.

I was looking for solutions on other sites and saw this:

[http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png](http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png)

I don't see those options at all. 

The HDD has been cleaned with CCleaner (1 pass) and quick formatted in Windows 7, if that helps. Maybe I'm using the wrong setup CD? I dunno.

Help!

---

### Post by santosh83 on 2012-04-03
> **QQQ6 said:**
> Sup. I'm a complete rookie when it comes to Linux.

I just got a Ubuntu 11.10 boot CD (Wubi) and I want to install it on a clean HDD. 

I only have that one drive, so I don't want dual boot or anything like that - just an HDD that automatically boots Ubuntu when I turn on the computer.

The problem is that when I boot using the CD, I can't do anything in the setup because the partition list is empty and when I click "Install", it says "No root file system defined" etc.

I was looking for solutions on other sites and saw this:

[http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png](http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png)

I don't see those options at all. 

The HDD has been cleaned with CCleaner (1 pass) and quick formatted in Windows 7, if that helps. Maybe I'm using the wrong setup CD? I dunno.

Help!

I may be wrong here, since I've never used the WUBI version of Ubuntu, but I think it's meant to be installed from **inside** Windows, just like you'd install a normal Windows app. It'll install the entire Linux filesystem into a single ordinary Windows file. You'll **still** be presented with a boot-time menu, giving you the option to boot either Windows or Linux, since both are installed.

If you want to automatically boot Ubuntu without a boot-time prompt, then either install Ubuntu as the **sole** OS on your HDD, (thus overwriting your existing Windows), or after you've installed Linux alongside Windows, you can disable the entry for Windows in your bootloader menu (this is done from within Linux), and set the 'timeout' to 0, so it (bootloader) will not wait for your prompt and will automatically boot the only entry available (Linux.)

For installing alongside Windows (or replacing it) on a **separate** partition, you need the normal Ubuntu CD, not the WUBI based one.

Adding some useful links:
[Ubuntu Installation Guide]("https://help.ubuntu.com/community/Installation")
[Guide to WUBI]("https://wiki.ubuntu.com/WubiGuide")
[Starting point for the official Ubuntu docs]("https://help.ubuntu.com/")

---

### Post by Rodney9 on 2012-04-03
Welcome.

1. Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Very good pictorial Install Guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Check your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Rodney

---

### Post by QQQ6 on 2012-04-03
Will the alternate installer work (**ubuntu-11.10-alternate-i386.iso**)?

The one I used is **ubuntu-11.10-desktop-i386.iso**

I'm a bit confused.

Let's pretend I don't have any copy of Windows - no DVD, no installed system, no nothing.

---

### Post by santosh83 on 2012-04-03
> **QQQ6 said:**
> Will the alternate installer work (**ubuntu-11.10-alternate-i386.iso**)?

The one I used is **ubuntu-11.10-desktop-i386.iso**

I'm a bit confused.

Let's pretend I don't have any copy of Windows - no DVD, no installed system, no nothing.

Both should work for installing Ubuntu on a separate partition alongside Windows, or wiping Windows and installing exclusively. Neither is the WUBI based installer. Unless you have a particularly old system, or other special reasons, the desktop CD should work just fine!

---

### Post by QQQ6 on 2012-04-04
So I got a Windows 7 DVD from a friend, installed it on the drive and nothing's changed.

If I boot from the Ubuntu disc, I can't see any partitions and when I click install I get "no root file system defined".

If I run the setup from within Windows, Ubuntu installs, restarts the computer (like it should) and displays... the same message.

Should I manually create a partition on the HDD in Windows?

What the hell am I supposed to do? :confused:

---

### Post by critin on 2012-04-04
> **QQQ6 said:**
> Sup. I'm a complete rookie when it comes to Linux.

[COLOR=Red]I just got a Ubuntu 11.10 boot CD (Wubi) and I want to install it on a clean HDD. 

I only have that one drive, so I don't want dual boot or anything like that - just an HDD that automatically boots Ubuntu when I turn on the computer.[/COLOR] 

The problem is that when I boot using the CD, I can't do anything in the setup because the partition list is empty and [COLOR=Red]when I click "Install", it says "No root file system defined" etc.
[/COLOR] 
I was looking for solutions on other sites and saw this:

[http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png](http://i.techweb.com/infoweek/byte/howto/freshubuntu_kelley/4.png)

I don't see those options at all. 

[COLOR=Red]The HDD has been cleaned with CCleaner (1 pass) and quick formatted in Windows 7, if that helps. Maybe I'm[/COLOR] [COLOR=Red]using the wrong setup CD? I dunno.[/COLOR]

Help!

Wubi must be installed inside Windows.  If you don't have windows installed it won't install because of (no root system)

Do you mean you "quick formatted" the Windows7 partition?  So there is no longer a Win7?  If you had to borrow a Win7 cd I assume the disk is empty.  Good--that makes it easy.

[COLOR=Red]Wrong cd--yes.[/COLOR]
Download another iso and this time don't get a Wubi Windows installer version. ** Don't choose the (if you have windows) option.**

If the disk is empty, you can install on the entire disk and it will do the partitioning and formatting for you.  Keep it simple and let the installer do the work.

I would suggest you delete the wubi iso before downloading the second ubuntu so not to try to  install it by mistake.  (this won't apply since you haven't stored it on the computer.)

---

