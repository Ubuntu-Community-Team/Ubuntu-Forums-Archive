---
title: "Complicated Partitioning scheme - Help needed"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Oxypunk on 2008-11-24
I have been using Ubuntu for about half a year, and love the way it is running now.  As good as Ubuntu is I occasionally still need to use windows. In other words I need to to dual boot my laptop.  Just splitting up my hard drive into 2 partitions for XP and Ubuntu would be a waste of a lot of memory.  I have a 100gb hard drive to work with.  Below is a list of how I would like to partition my computer:

XP (15GB)
Ubuntu (15GB)
A Linux distro to play around with like Slackware (10GB)
Media Storage (music, videos, common documents) (58.5 GB – Fat32 so any OS can use it)
Swap – Is it possible to have Linux and XP share a swap partition?(1.5GB)

Does this seem like a good layout and allocation of my hard drive memory?  I have a lot of music, so it is in my best interest to have have a partition that I can store music in for itunes to use in windows and Amarok with Ubuntu/Slackware.  Another question I have is it better to install Ubuntu first or XP?  I also really like having the extra partition for random Linux distributions so that I can try a lot of them out, but not affect my ability to be productive while learning how to use each distribution.  I won't actually be doing anything to my computer until winter break in a few weeks.  It is not worth messing with my computer with finals coming up so soon!

Any advice would be greatly appreciated.

---

### Post by Kellemora on 2008-11-24
Hi Oxy

I would advise placing your /home directory in it's OWN partition.
That way it can be shared by other distros, and it won't be messed up when you upgrade a distro.

Swap of 1 gig should be plenty!

You may possibly want to keep your music files on a partition of their own also, since you have so many of them.

Definitely install XP FIRST, it thinks it's GOD and don't like to have any other gods before it, hi hi.........

Then Any other Distro you want to install.
 
Finally install Ubuntu LAST, this will insure the Grub Boot Loader picks up all the other Distro's and will save you ton's of work in getting Grub configured correctly!

TTUL
Gary

---

### Post by egalvan on 2008-11-24
> **Oxypunk said:**
> I need to to dual boot my laptop.
Below is a list of how I would like to partition my computer:



[I]XP (15GB)
Ubuntu (15GB)
A Linux distro to play around with like Slackware (10GB)
Media Storage (music, videos, documents)[/I]

    Sounds reasonable.

***(58.5 GB – Fat32 so any OS can use it)***

   Personally, I would never use FAT32 on any partition over 4gb in size.
   I would either use NTFS, or ext3. I have done both.

    Windows can only read MS file systems ´out-of-the-box´.
    An ext2 driver exists for XP. I works well.
    
    Linux can read many different file systems, including almost all Windows stuff.

*Swap – Is it possible to have Linux and XP share a swap partition?(1.5GB)*

Windows cannot use Linux Swap Partitions. As far as I know.


*Does this seem like a good layout and allocation of my hard drive memory?*

    so far, yes.

*  store music in for itunes to use in windows and Amarok with Ubuntu/Slackware.*

Again, ext2 or ext3 would be a better choice, also NTFS.
Not FAT32.


*is it better to install Ubuntu first or XP?*

    Absolutley easier to **install Windows first**. Windows does not play nice with any other boot loaders.
Linux boot loader, such as GRUB, will respect most other OS it finds.


[I]  I also really like having the extra partition for random Linux distributions so that I can try a lot of them out, but not affect my ability to be productive while learning how to use each distribution.
[/I]

This is something that many are doing. I myself usually have two different Linux installed, along with XP.

---

### Post by laffinet on 2008-11-24
Seems like a good layout for what you are trying to do.

The only thing I'm not sure about is the swap partition, don't think you will be able to use the same partition for both windows and Ubuntu. Having said that, I don't think windows is using a partition for swap, but just a file.

Setting up dual boot (which is what you are trying to do) is always easier by installing windows first and then Ubuntu, so that's the way to go.

So, the process would be:

Install windows (if you haven't already done so)
Install Ubuntu, choosing manual partitioning when prompted, creating the partitions you need (root and home*, swap, extra partition for other distros, extra partition for use within linux/windows)

* depending how carried away you want to get you can have root and home on the same partition or separate partitions

There are good partitioning guides out there, don't have a link at the moment, will do some digging later and post here. Or just do a search yourself.

---

