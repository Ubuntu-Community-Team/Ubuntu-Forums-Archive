---
title: "Leftover Partition"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Xenoverse on 2013-02-24
About a week ago I set up a dual-boot of the 12.10 release (alongside Windows 7) using the Wubi installer. Everything was fine for a few days and I was hoping to begin a complete transition to Ubuntu, so I attempted to copy my Windows files (documents, music, pictures, etc) into Ubuntu. The process was taking quite a long time, so I stepped away from my computer. When I returned it was completely shut down, so I booted back up. I wasn't given the prompt to choose between Windows or Ubuntu, it simply booted Windows as it did before I installed Ubuntu. I tried rebooting, same thing. I decided "screw it, I'll just reinstall," so I uninstalled Ubuntu (using Revo Uninstaller to get all the leftovers).

Here's my problem: when I examine my drive, there's still System Reserved (which I believe is the partition created for Ubuntu). Do I need to get rid of this before I try to reinstall? If so, how do I go about doing so? Also, did Windows do something to Ubuntu to make it stop working? Is it possible that in my process of copying files I maybe wiped the dual-boot prompt (or some similar file/program)?

---

### Post by Xenoverse on 2013-02-24
Wow, should've looked up what System Reserved is before posting this. :oops:

Would still like to find out why Ubuntu suddenly stopped working though.

---

### Post by fantab on 2013-02-24
Wubi installer is basically to TRY Ubuntu from within the Windows OS. It is not, what many would call, a true dual boot. You cannot, perse, make a "complete transition to Ubuntu if you have installed it via Wubi. 

I recommend that you completely uninstall Ubuntu from windows... then Install Ubuntu on its own partition (which you have to create rather than depend on the ubuntu installer to do if for you). There is loads of info on the www and on this form to help you set up a dual boot.

Remember to BACK UP your important DATA before you set out to partition your HDD.

Good Luck.

EDIT: After uninstalling Ubuntu from Windows you can also use 'System Restore' from Win to have your Windows install to state it was prior to the ubuntu Wubi install.

---

### Post by arpanaut on 2013-02-24
> Would still like to find out why Ubuntu suddenly stopped working though.I don't know for sure why it failed but would presume that the problem is related to the fact that wubi is installed within Windows in a virtual disk that has a 30 Gib limit in size.

So if wubi was not given enough space to accommodate the files being moved into it then the filesystem was filled to capacity and became unusable.

I have seen many posts here about wubi becoming unusable because of having no available space on the root filesystem... hence the previous suggestion for a full install of Ubuntu to it's own partition for long term use. 

There is also the issue of the situation that if the windows filesystem becomes corrupt then the wubi installation will become inaccessible/unbootable.

---

### Post by Xenoverse on 2013-02-24
Thanks for the replies. Reinstalled from a DVD and everything seems ok, I was able to copy what I wanted from Windows no problem. Loving Ubuntu so far.

---

