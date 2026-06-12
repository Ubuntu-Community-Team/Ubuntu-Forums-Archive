---
title: "Best Practices"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by manicjonah on 2011-09-18
I am getting ready to setup my first Ubuntu computer and could use a little guidance.  For starters, how should I partition the drive?  I have a 320GB drive.  I plan to use Ubuntu for basic Internet usage and for hosting virtual machines.  How much space does the OS partition require?

  In Windows I would never have a 320GB C: partition. I would make an 80 - 160 GB C: partition and use the remaining space for the D: partition.  The D: partition would be home to the VMs and other data.

Is there a common or best practice for partitioning in Ubuntu?  What type of file system should I be using?  
Am I better off letting Ubuntu install using the default options and then partitioning as needed in GParted? 
Is it necessary to relocate the swap file or create a swap partition?

I understand a lot about how Windows CAN be installed and then how it SHOULD be installed under different circumstances but I have no idea how to properly install and configure Linux.

Thanks for helping me get started.

MJ

---

### Post by Frogs Hair on 2011-09-18
Hello and Welcome

There are different ways to partition . If you want to share a data partition with Widows search for methods to do so . It is also possible create a separate home partition for Ubuntu . If you are planning on dual booting for the long term a data partition may be best . 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by georgemc on 2011-09-18
Just my opinion and 2cents worth.
 
 Most of the Linux installs are less than 10GB in root (/).
 My rule of thumb for swap == 2X memory.  Lots of opinions on this.
 Separate Home directory, saves you from head aches when upgrading.
 Q: sharing folders with Windows?  If yes than either Samba or a NTFS partition.
 

 So I would slice up that 320 as follows:
 
 20-50 GB for root
 2X memory for swap
 50-100 for home
 and the rest as a data partition, either NTFS or ETX4 with Samba
 
 For example I gave my main desktop 50GB of root so I can download and compile kernels when I want to.  I horde a lot in my HOME dirs so that partition is 50% of what remained and the other 50% is a ETX4  data disk using Samba for sharing.
 
 Now if your are planning dual booting then you need to take the other OS' requirements into account.

 I prefer defaults settings, however, when I slice up a drive the defaults never really worked for me.
 
Yes I use gparted most of the time and only native Windows tools when manipulating windows partitions.

 +1 “Frogs” links are good reads.
 

 Just another point of view.  Have fun.
 

 George

---

### Post by Lisiano on 2011-09-18
+1 for the above.
I must add that you should also remember that having too much Swap is just wasted space (Why do you need 16 gigs of Swap if you have 8 gigs of RAM?). If you plan to use VM's then swap is necessary because you have a higher chance of running out of RAM.
IMO if you have 2-4gigs of RAM then set around 4 gigs of Swap, for 4-8+ gigs, 2-4 gigs or if you plan to Hibernate, 4-8+ gigs. Usually the more RAM you have, the less you need to set for Swap, the only exception if you plan to Hibernate. Currently I have 8GiB of RAM and use 6GiB of Swap because I never use more than 4 gigs at a time, if I do, I close the programs that make me use more than 4 gigs of RAM.

Personally I would set your system as this:
/ - 40 gigs (Note, all programs [/usr, /bin, /sbin, /opt, etc], configurations [/etc], logs [/var/log], old temporary data [/tmp] is stored there)
/home - Rest minus Swap (I don't like Data partitions)
swap - Around 2-4 gigs. (Also your hibernation data location)

Do think about if you plan to use Windows during ANY time in the future.

---

### Post by anewguy on 2011-09-19
+1, with the following:  used to be that if you wanted to hibernate that swap needed to be 2x your physical memory plus a little overhead.  However, with modern equipment I really see no need to hibernate - just shutdown and reboot it later when you need it.  With hibernate it still has to load everything back in - just from swap instead.  It's still disk access.  The little extra it takes to just boot should be small.

I personally go with Lisiano and wouldn't create a separate data partition.  You can read/write ntfs partitions with Linux anyway so if you do install Windows it shouldn't be a problem.

Now, a little extra advice - if you want to also have Windows - dual boot - install Windows FIRST, defrag the disk a couple of times, then go to the ubuntu install setting up the partitions for ubuntu as you want.  This will save an extra post back here if you install Linux first and then Windows - you'd be asking how to get to Linux. So remember, Windows first, then Linux. ;)

Just my 2 cents worth!

Dave ;)

---

### Post by Lisiano on 2011-09-19
Or cooler. S3 Suspend. Turns off everything except power to your RAM. Most laptops can stay in this mode for a few days.
So the need for hibernation is mostly not-needed but it's up to the OP to decide if he wishes to use it.

EDIT: It seems this is my 7th post. Evil 111.

---

### Post by manicjonah on 2011-09-19
Thanks everyone for the replies.  I don't think I'll be dual booting.  Ubuntu will be the only OS on the computer and if I need Windows I'll fire up a VM in virtual box.

I created an install disk and am stuck on what should be an easy point in the install:

Erase Everything 
Something Else

If I choose Erase Everything how is the disk carved up?
Choosing something else leaves me with more questions.  What file system to I select for:
Root
Home
Swap
I don't think I will use a data partition because I'll be able to reach my Windows network in Places (right?).

This is a totally experimental install of Ubuntu for now.  I'm not totally ready to let go of things like Office so I'm not concerned about creating too much new content on the computer that I will someday need to share with my Windows machines.  Though I should easily be able to change this later by creating an NTFS partition right?

---

### Post by 3rdalbum on 2011-09-19
> **manicjonah said:**
> Thanks everyone for the replies.  I don't think I'll be dual booting.  Ubuntu will be the only OS on the computer and if I need Windows I'll fire up a VM in virtual box.

I created an install disk and am stuck on what should be an easy point in the install:

Erase Everything 
Something Else

If I choose Erase Everything how is the disk carved up?

As you'd expect: Everything erased, 100% to Ubuntu.

> Choosing something else leaves me with more questions.  What file system to I select for:
Root
Home
Swap
I don't think I will use a data partition because I'll be able to reach my Windows network in Places (right?).

You need a root "/" filesystem. It's the one that holds your new operating system. Format it to Ext4 format. You're correct, you don't need a separate data partition or a /home partition.

In the past, people used to say that you needed a separate /home partition so you could easily reinstall Ubuntu or do a fresh install of a newer version. Today, you don't need to as the Ubuntu installer will notice that you're installing to a partition that already contains an Ubuntu, and will preserve the existing /home.

As for swap, most people these days don't need it. If you have a gigabyte of RAM or less you might want to put a gigabyte of swap partition on your hard disk. It's temporary storage for things that can't fit in RAM. If you've got 1.5 GiB or more then you don't need to worry about it.

So basically, create a single partition, make it / and set it formatted as Ext4, and that's pretty much all you need.

> This is a totally experimental install of Ubuntu for now.  I'm not totally ready to let go of things like Office so I'm not concerned about creating too much new content on the computer that I will someday need to share with my Windows machines.  Though I should easily be able to change this later by creating an NTFS partition right?

If you need to share data with an existing Windows partition, you can access the Windows partition (read and write) from within Linux. If you want to share data with a different computer, you can use your Linux computer (or Windows one, for that matter) as a Samba file server.

---

