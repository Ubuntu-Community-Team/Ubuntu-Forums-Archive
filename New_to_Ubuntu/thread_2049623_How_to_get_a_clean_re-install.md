---
title: "How to get a clean re-install?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by docpat2511 on 2012-08-28
Hello, all.

I'm just starting out with Ubuntu (LTS, installed in dual-boot with Windows XP Prof using wubi). I did a real bad thing in the command line which appeared to start mass-deleting loads of packages. I stopped that process, after which the software center stopped working.

All my working data is in Dropbox, and I had a bunch of software installed I didn't really need so figured I would be better off nuking it all and restarting. I booted to Windows, uninstalled with wubi, then re-installed.

On booting into Ubuntu, it acted as if the old install wasn't purged - my userid and password were retained, and software center still crashed before completely opening. I updated all packages and nothing changed; then looked for other solutions and nothing seemed to work. I'm trying to find a way to just start over.

Are there remnants of the old install that need to be purged before a re-install with wubi? How can I clear them out?

Thanks a bunch.
~Pat.

---

### Post by micahpage on 2012-08-28
If your looking to completely start over, then a live disc of ubuntu (for example) will give you option to format the partition before install, which will clear everything as if it never existed for ubuntu.

If you have the partition already there for ubuntu, even if its messed up, you shouldn't have to go into windows for anything related to setting up and/or installing ubuntu. You can set the iso for ubuntu on a USB drive to boot from (easily with unetbootin) or do the same with a CD. Then you can jump into the live and check the old OS, or just start reinstalling. The process of reinstalling will format the partition anyways

---

### Post by mapes12 on 2012-08-29
Wubi installation is not dual booting. To completely remove wubi and start over try this:-

[https://wiki.ubuntu.com/WubiGuide/#Uninstallation](https://wiki.ubuntu.com/WubiGuide/#Uninstallation)

---

### Post by Bucky Ball on 2012-08-29
Welcome. Wubi is not really a dual-boot. It is a Wubi install inside Win. This is intended to check out Ubuntu for awhile and see if you like it, not a long term solution. Not uncommonly problematic.

If you are going to start again, for a better experience I suggest running 12.04 LTS from the LiveCD, check if things are working and you like what you see (if you don't you might like to try the lightweight Xubuntu or the all bells and whistles Kubuntu), and install to a partition(s) on the hard disk by clicking the icon on the desktop. 

More involved but better result. There are plenty of guides on how to dual-boot and any other questions just post or start a new thread here. ;)

---

### Post by docpat2511 on 2012-08-29
Thanks, guys. 

I was nervous about doing a "real" dual-boot because - well - I might do something exactly like this. I may still try wubi for a while, until I know I'm not going to screw up too much.

---

### Post by Bashing-om on 2012-08-29
docpat2511;

 That is ONE of the beauties of ububtu. You can not screw up too much. If you break it you can fix it!

 I also recommend get out of the wubi and install ubuntu (it will operate lots faster)// Then we will work to get you onto a single ubuntu operating system.


[INDENT]my 2 pennies worth <==BDQ

[/INDENT]

---

### Post by Karlchen on 2012-08-29
[SIZE=1]**<side issue>**[/SIZE]

> **Bashing-om said:**
> I also recommend get out of the wubi and install ubuntu (it will operate lots faster)Sorry, this is simply not true. The fact that a Wubi Ubuntu installation runs off a loop mounted ext4 filesystem does not necessarily make it run more slowly.

> **Bucky Ball said:**
> Wubi is not really a dual-boot. It is a Wubi install inside Win. [..] Not uncommonly problematic. After having used Ubuntu (Wubi installation) for my daily work for two years now, I do wonder why so many people tell so many bad things about Wubi without ever bothering to give one single piece of evidence.

Karl

[SIZE=1]**</side issue>**[/SIZE]

---

### Post by Bashing-om on 2012-08-29
@Karlchen;

  I stand corrected. I confess I have never used wubi.


[INDENT]BDQ
[/INDENT]

---

### Post by Karlchen on 2012-08-29
Hello, Pat.
> **docpat2511 said:**
> Are there remnants of the old install that need to be purged before a re-install with wubi? How can I clear them out?You uninstall a Wubi Ubuntu installation from inside Windows. Control Panel => Add/remove software (XP) or Software and Features (Vista/Win7).

This should remove the \ubuntu folder on the disk including its content. This should also remove the additional boot entry "Ubuntu" in the Windows boot menu. It should remove the files wubildr and wubildr.mbr from the Windows boot drive C:.

You  might like to check the folder and its content are really gone with the help of Windows Explorer. You might also like to check the "Ubuntu" boot entry is gone either by rebooting the machine or with the help of EasyBCD.

For more details on Wubi, you may like to read the official [**Wubi Guide**]("https://wiki.ubuntu.com/WubiGuide").

Cheers,
Karl

---

### Post by Bucky Ball on 2012-08-29
> **Karlchen said:**
> 
 After having used Ubuntu (Wubi installation) for my daily work for two years now ...


Good for you! Glad it's working for you. Horses for courses ... Just wonder if you've tried Ubuntu from a hard drive install  for comparison else a Wubi install is compared to what? How would you  know if it was faster or slower? :wink:

> **Bashing-om said:**
> @Karlchen; I stand corrected. I confess I have never used wubi. 
BDQ


I have and for me they are different beasts, the experience does not compare with a hard drive install in operation and, yes, Wubi was slower, at least for me. 

But back to the OP's issue ...

---

