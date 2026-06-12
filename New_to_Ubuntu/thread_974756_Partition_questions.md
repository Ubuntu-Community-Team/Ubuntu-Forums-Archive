---
title: "Partition questions"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Turbojoe on 2008-11-07
I just downloaded and burned 8.10 to give this a try again. I tried installing 8.04 a few months back and it failed at the very end. I get no dual boot screen. Nothing to indicate Kubuntu is on there except that the 200mb partition I created during installation is not available to windows and it doesn't even show in explorer. It's like my 500gb drive is now a 300gb drive. I was hoping that 8.10 would find that partition and install itself there. No luck. It's asking me how I want to partition. In the drive list shown I don't recognize the dev\sda* and dev\sdb* info. I have two drives installed. The storage drive has 3 partitions with no operating system. The main 500gb drive has a 300gb XP partition and a 200gb Kubuntu partition. I don't see those unused 200gb in the information window. I need to straighten this out without risking any loss of info from my XP partition. I aborted the 8.10 installation at the partition section. What do I do at this point?
Thanks for ANY help.

Joe

---

### Post by nhasian on 2008-11-07
can you please post the output of

```
sudo fdisk -l
```

---

### Post by Turbojoe on 2008-11-07
> **nhasian said:**
> can you please post the output of

```
sudo fdisk -l
```

How do I get this code output? Other than fdisk it doesn't look familiar to me. If 8.04 installed it is not accessible so I can't do anything with Kubuntu.

I just dug through a bunch of software my son gave me and I have Paragon hard disk manager 2008. I loaded it and now I can see the partition. It is shown as a Linux partition. Should I delete it or format it and try to reinstall?

I think I've said this here before but I know enough about computers to be dangerous. I don't make my living with them so not everything makes as much sense to me as it might to you. Not a newbie but...... 


Joe

---

### Post by louieb on 2008-11-07
> **Turbojoe said:**
> How do I get this code output? 
Boot the install CD to desktop.
If it were Ubuntu you would go to Applications>accessories>terminal.
In the KDE (Kubuntu) desktop just have to look around  the menu and find the  **terminal **option. The command **sudo fdisk -l**  (lowercase L) will display the partition table. 

Without the output from this command anything I could say would be just a guess.

If this computer has  multiple hard drives there is a good chance the problem was GRUB did not get installed correctly. May be able to get GRUB fixed. or at least will be able to guide you through the partitioning part of installing 8.10.

---

