---
title: "?Clear failed installs from Ubuntu partition?"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2012-04-23
I have two bad installs of Ubuntu on a partition (Dual with XP).And no good installs. And I have full backup.

One of the installs is 10.04 and I am able to log in to that one. Don't know what the other Ubuntu even was.

I want to prepare for a clean install of 12.04. 

Can you tell this failed newbie how to (simply) get rid of the junk? I've had too much hassle with Ubuntu installs to want old files laying around to screw things up again

---

### Post by Cheesemill on 2012-04-23
Can you boot from your working Ubuntu installation and then fire up gparted and post a screen shot (you may have to install gparted first).
```
sudo apt-get update && sudo apt-get install gparted
```

This will let us see what sort of state your partitions are in.

---

### Post by cmont899 on 2012-04-23
When setting up the partitioning in the 12.04 installer there will be 2 options, remove all partitions and install, and remove linux partitions and install. Choose the former to remove old windows AND Ubuntu installs.

Alternatively you can fully zero out the hard drive with the following steps:

1) Boot from the Ubuntu CD
2) Choose "Try Ubuntu"
3) Launch "Terminal"
4) Run the following command:

sudo dd if=/dev/zero of=/dev/sda

Done :D

---

### Post by kc1di on 2012-04-23
> **MickeyPilgrim said:**
> I have two bad installs of Ubuntu on a partition (Dual with XP).And no good installs. And I have full backup.

One of the installs is 10.04 and I am able to log in to that one. Don't know what the other Ubuntu even was.

I want to prepare for a clean install of 12.04. 

Can you tell this failed newbie how to (simply) get rid of the junk? I've had too much hassle with Ubuntu installs to want old files laying around to screw things up again

can you go to a terminal in your 10.04 install and type the following and past the results here?
```
sudo fdisk -l
```

---

### Post by MickeyPilgrim on 2012-04-23
I do not have partitioning experience and hope to just get rid of old files to prepare for a clean install of 12.04.  I do not want to get rid of my dual boot with XP.  You suggestion seems to require me to remove one or both partitions. I am asking if there is a simple way of cleaning the Ubuntu partition that I have.
Thanks

==========================================
> **cmont899 said:**
> When setting up the partitioning in the 12.04 installer there will be 2 options, remove all partitions and install, and remove linux partitions and install. Choose the former to remove old windows AND Ubuntu installs.

Alternatively you can fully zero out the hard drive with the following steps:

1) Boot from the Ubuntu CD
2) Choose "Try Ubuntu"
3) Launch "Terminal"
4) Run the following command:

sudo dd if=/dev/zero of=/dev/sda

Done :D

---

### Post by MickeyPilgrim on 2012-04-23
I'll try and get Gparted.  Thanks.

===========================
> **Cheesemill said:**
> Can you boot from your working Ubuntu installation and then fire up gparted and post a screen shot (you may have to install gparted first).
```
sudo apt-get update && sudo apt-get install gparted
```

This will let us see what sort of state your partitions are in.

---

### Post by Cheesemill on 2012-04-23
Deleted

---

### Post by MickeyPilgrim on 2012-04-23
It will take me a while to get back to this project.  Please check in a few hours.

MickeyPilgrim



> **MickeyPilgrim said:**
> I'll try and get Gparted.  Thanks.

===========================

---

### Post by MickeyPilgrim on 2012-04-23
Hi kc1di,
  I was able to get into a terminal and run  sudo - fdisk -1 and this is what it said ...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

madhack@madhack-desktop:~$ sudo fdisk -1
[sudo] password for madhack: 
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

madhack@madhack-desktop:~$ 





> **kc1di said:**
> can you go to a terminal in your 10.04 install and type the following and past the results here?
```
sudo fdisk -l
```

---

### Post by jerome1232 on 2012-04-23
> **MickeyPilgrim said:**
> Hi kc1di,
  I was able to get into a terminal and run  sudo - fdisk -1 and this is what it said ...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

madhack@madhack-desktop:~$ sudo fdisk -1
[sudo] password for madhack: 
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

madhack@madhack-desktop:~$

the letter l, not the number 1

---

### Post by MickeyPilgrim on 2012-04-23
Ah Ha !
Here we go.
======
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x628e628e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9931    79769858+   7  HPFS/NTFS
/dev/sda2            9931       19458    76519425    5  Extended
/dev/sda5           19064       19458     3161088   82  Linux swap / Solaris
/dev/sda6            9931       14430    36138240   83  Linux
/dev/sda7           18803       19064     2088960   82  Linux swap / Solaris
/dev/sda8           14431       18617    33628160   83  Linux
/dev/sda9           18617       18802     1487872   82  Linux swap / Solaris

Partition table entries are not in disk order


> **jerome1232 said:**
> the letter l, not the number 1

---

### Post by audiomick on 2012-04-23
Leave sda1 alone. That is your windows install.

Leave sda 2 as it is. That is an extended partition, and is fine.

Delete sda 5, sda6, sda7, sda8 and sda9 and use the free space for your new install.

---

### Post by MickeyPilgrim on 2012-04-23
How do I delete those items; sda 5,6,8, and 9 ?
As asked I got Gparted and will attach a screen shot. See Attached.
Thanks for all the help.


> **audiomick said:**
> Leave sda1 alone. That is your windows install.

Leave sda 2 as it is. That is an extended partition, and is fine.

Delete sda 5, sda6, sda7, sda8 and sda9 and use the free space for your new install.

---

### Post by audiomick on 2012-04-23
Ok. You see how sda2, sda8 and sda9 have a picture of a key next to them? That means they are mounted. In the case of sda2, that is, I believe, because the other two, which are both swap partitions, are mounted. Sda2 is an extended partition, and if logical partitions inside of it are mounted, which is the case, it is also mounted.

So..
right click on sda8 and sda9 in turn an choose "swap off". When you have done that, I believe that sda2 will then also be unlocked.

Then click on one of the partitions you want to change and go to the "partition" menu, as can be seen in my screenshot, and choose what you want to do with the selected partition.

Mine is in German. The option that the mouse is pointing at is "format as", but there is also a "delete" option. "Entfernen" is the German word.

---

### Post by Bartender on 2012-04-23
Right-click either on the partition in the map (I call the visual display across the top of the window the "map"), or right-click directly on the text description of the partition below.  A context window will open.  One of the options will be to Delete.

Delete every single partition to the right of sda6.  Then delete sda6.  When you're done (I can't quite tell from the screenshot) you should have either one extended partition (sda2) or a bunch of unallocated space.  

Or maybe some of both.  If you end up with the sda2 extended partition, and unallocated space to the right of that, then delete sda2 also.  You should then have one continuous block of unallocated space.  Right-click on that space, click on New, and create one primary ext4 partition.  Then get out of GParted.  That's probly the simplest.

You could also create one big extended partition, then get out of GParted.

Or create primary & extended partitions for /, swap, and /home.  But that's more complicated.  Not a lot more, but maybe you can tackle that the next time...

EDIT: audiomick beat me to it, plus I forgot about the mounted partitions.  That's why I always use a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") instead of Ubuntu disc.  With a GParted LiveCD I don't have to futz with unmounting partitions...

---

### Post by audiomick on 2012-04-23
I would leave sda2, and if necessary extend it into any available space to the right (and left) of it. Ubuntu works fine installed into logical partitions (inside an extended), and it leaves you more flexible if you want to make any changes at a later date.

I thought the OP was working from a Gparted CD, but having looked at the screenshot again, I don't think so now. I would also recommend working from a Gparted CD or a Ubuntu live CD. I see now that one of the mounted partitions is not a swap, but rather a / partition. I don't think it is possible to change the partition that the machine is booted from.

---

### Post by MickeyPilgrim on 2012-04-24
Yes, I got Gparted from the command line-terminal, which I guess is the same as a repository. But I have also downloaded Gparted from the web source and could burn a cd (I need to find out if it has to be a data cd or a video cd, don't I/) Will it be useful in getting this old crud swept away?
====================================


> **audiomick said:**
> I would leave sda2, and if necessary extend it into any available space to the right (and left) of it. Ubuntu works fine installed into logical partitions (inside an extended), and it leaves you more flexible if you want to make any changes at a later date.

I thought the OP was working from a Gparted CD, but having looked at the screenshot again, I don't think so now. I would also recommend working from a Gparted CD or a Ubuntu live CD. I see now that one of the mounted partitions is not a swap, but rather a / partition. I don't think it is possible to change the partition that the machine is booted from.

---

### Post by audiomick on 2012-04-24
You could burn a Gparted CD and use that, but if you are planning to install, you could also use the install CD. Boot into the live environment, the "try without changing" option. There is a Gparted on there which you can use. Then you can go straight on to installing when you have your partitions cleaned up without having to re-boot. 

You could even do the clean up during the install, but I like to do it separate so that I have a nice clean partition set-up when I get to that in the install.

---

### Post by Bartender on 2012-04-24
I consider the stand-alone GParted LiveCD _the_ single most important tool for installing/partitioning tasks.

I never use the Ubuntu installer disc because it always mounts some partition and adds a layer of confusion to the process.  With the stand-alone GParted CD I can wipe everything off the drive without complications.

If you have a Windows PC, get the latest stable download from sourceforge, and use ImgBurn to convert the .iso download to a bootable CD.  The rest of the process is just like installing Ubuntu from a CD - make sure to boot from the CD.  You'll have to answer a few questions, such as leave the keyboard alone, language (English is default) and video driver.  I've almost always been able to use the defaults.  Once or twice I had to boot into the video safe-mode.

EDIT: audiomick's advice on sda2 is sound - instead of blowing it away you can just expand it to the far end of the drive.

---

