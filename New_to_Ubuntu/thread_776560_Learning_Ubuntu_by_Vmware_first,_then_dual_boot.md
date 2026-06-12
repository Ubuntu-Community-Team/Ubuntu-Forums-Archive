---
title: "Learning Ubuntu by Vmware first, then dual boot?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Chuck251 on 2008-04-30
I am new to Linux/Ubuntu, and want to play around with it in VMware on XP first, before switching to it fully or dual booting into it.

I am building a new system with a single 640GB Sata drive.  If while setting up XP I leave, say 60GB free as an unused partition, and later on want to move the Ubuntu system I've been running in VMware to this partion so I can now boot into it, how hard (or reliable) is this?

Thanks!

---

### Post by wheels. on 2008-04-30
why not just start with the dual boot configuration? Then you get a full feel of how it would work, and you get full performance as well! As for moving the vmware system to a partition and booting it, I think its just going to create a lot more work than you would have had had you just started off by dual booting, I am not sure if it is even possible.

just my $0.02

---

### Post by Tatty on 2008-04-30
I dont think that would really work.  

I have not tried doing what you are suggesting so someone may come and say it is possible, but im pretty sure that you would have to do a clean install in your new partition.

If you are planning to leave some space to install ubuntu into anyway then why not just install it straight off?  Running it in VMware is not as much fun as running it on its own, you will struggle with things like installing the proprietry graphics drivers etc.

---

### Post by iSplicer on 2008-04-30
Running in VMWare is a bad option, and there is no way to "copy" your virtual machine into a spare partition (there may be on second thought but its a bit pointless.)

I suggest dual booting now

---

### Post by Zralou on 2008-04-30
Why not just use the 'liveCD' to see how you like it, then install it to its own partition?.

Sara Lou

---

### Post by abhiroopb on 2008-04-30
By "move" I'm guessing you mean move your installed packages and settings. You can backup you're entire home folder (including all the hidden files), and take a not of all the packages. Then do a clean install of ubuntu and put the folders you had backed up into you're home folder. Also for packages:

[http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html](http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html)

---

### Post by lemming465 on 2008-04-30
Running ubuntu in vmware works fine; I do it all the time at work.

Another option for a Windows box you don't want to repartition is to use the fairly new *Wubi* installer; it creates a C:\Ubuntu directory, puts NTFS file space in there to hold root and swap filesystems that can be loopback mounted, and then adds an Ubuntu option to your windows boot menu.  If you hate it, it puts an uninstall option into add/remove programs.

The other advice in the thread - live CD, low risks of dual booting, and strategies for moving data files - is all good.

In general moving installs is not for the faint of heart, particularly between computers, since you can run into lots of issues related to CPU architecture, disk controllers, and boot loaders.  I've done it, but I don't particularly recommend it, and I **especially** don't recommend it to Linux neophytes.

---

