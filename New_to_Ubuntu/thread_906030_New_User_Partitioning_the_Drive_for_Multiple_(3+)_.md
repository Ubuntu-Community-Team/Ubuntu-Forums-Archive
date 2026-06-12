---
title: "New User: Partitioning the Drive for Multiple (3+) OS's"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by KeithA45 on 2008-08-31
Hey guys,

Quick Background: I just replaced the dying hard drive in my Compaq Presario SR1230NX and upgraded from a 120 hard drive to a 320 hard drive, and with the extra space, I was hoping to partition the drive up a little bit and give linux a shot. I'm pretty familiar with Mac and Windows, but have never touched linux before.

I'd like to give two different types of linux a shot (1 of which being Ubuntu, and the other a friend recommended), so I'll need to make 2 more partitions. Should I...

1) Just follow the instructions for Ubuntu's partitioning, and use a different program to partition it again for the other OS?
2) Use a program to partition for Ubuntu AND the other OS?
3) Is there an option in Ubuntu's partitioning to make another parition for the third OS?

I can get access to Partition Magic pretty easily, or I've also heard about G-parted (although your forums tell me it's plenty slow enough) if those programs are useful

Thanks,
 - Keith

Edit: I should mention that the other linux I want to try is PCLinux OS, and I was told that I would need to do the partitioning myself (hence the nervousness)

---

### Post by swoll1980 on 2008-08-31
> **KeithA45 said:**
> Hey guys,

Quick Background: I just replaced the dying hard drive in my Compaq Presario SR1230NX and upgraded from a 120 hard drive to a 320 hard drive, and with the extra space, I was hoping to partition the drive up a little bit and give linux a shot. I'm pretty familiar with Mac and Windows, but have never touched linux before.

I'd like to give two different types of linux a shot (1 of which being Ubuntu, and the other a friend recommended), so I'll need to make 2 more partitions. Should I...

1) Just follow the instructions for Ubuntu's partitioning, and use a different program to partition it again for the other OS?
2) Use a program to partition for Ubuntu AND the other OS?
3) Is there an option in Ubuntu's partitioning to make another parition for the third OS?

I can get access to Partition Magic pretty easily, or I've also heard about G-parted (although your forums tell me it's plenty slow enough) if those programs are useful

Thanks,
 - Keith

Edit: I should mention that the other Linux I want to try is PCLinux OS, and I was told that I would need to do the partitioning myself (hence the nervousness)

When your using the Ubuntu installer when you get to partitioning choose manual configuration this will allow you to create as many partitions as you like, make sure you make a swap file twice as large as the amount of ram you have as well. You can find partitioning tutorials all over just use google

---

### Post by pranayama on 2008-08-31
Remember you're only allowed 4 logical partitions and ubuntu uses up 2 if you have the swap partition.

I never found gparted to be slow in shrinking or wiping partitions.

If what you really want to do is try out different distros, why not try out different live CDs, or create some virtual machines with VirtualBox on ubuntu.

---

### Post by cotcot on 2008-08-31
I recommend using the Gparted LiveCD and to make for example following partitions for both OS :

/ for ubuntu : primary ext3
/home for ubuntu : logical ext3
/ for 'the other OS' : primary ext3
/home for 'the other OS' : logical ext3
swap (1 swap can be used for both OS)

Other setups are possible for sure.

And it is not forbidden to name 'the other OS'. We are always interested in your findings.

---

### Post by jemate18 on 2008-08-31
> **pranayama said:**
> Remember you're only allowed 4 logical partitions and ubuntu uses up 2 if you have the swap partition.

I never found gparted to be slow in shrinking or wiping partitions.

If what you really want to do is try out different distros, why not try out different live CDs, or create some virtual machines with VirtualBox on ubuntu.

You are allowed only to have 4 PRIMARY partitions. To be able to avoid this limit, 1 of the 4 primary partitions should be EXTENDED partition. This EXTENDED partition can house multiple or arbitrary number of LOGICAL partitions.

LOGICAL partition may contain any .. swap, / , /usr/local, /opt. and so on and so forth.

hope this helps

jemate18

---

### Post by Shazaam on 2008-08-31
+1 on the Gparted Livecd.
Remember, every time you install a distro it will install it's own bootloader. Most distros are pretty good at picking up already installed os's but sometimes they don't. If that happens don't panic because it is easy to fix with a little editing.
AND, if you later decide to reinstall Windows it will re-write the mbr wiping out any other bootloader. Once again an easy fix.
Multi-disk multi-booting is easy. Here is an excerpt from my setup (edited for space)...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   620526689   310263313+   5  Extended
/dev/sda5             126    12546764     6273319+  82  Linux swap / Solaris
/dev/sda6        12546828    53817749    20635461   83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   301764959    82839141   83  Linux
/dev/sda9   *   301765023   461145824    79690401   83  Linux
/dev/sda10      461145888   615112784    76983448+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   146914424    73457181   83  Linux
/dev/sdc2       146914425   312576704    82831140    5  Extended
/dev/sdc5       146914488   312576704    82831108+  83  Linux

```
sda=SATA
sdb=PATA
sdc=PATA

---

### Post by wolfie2x on 2008-08-31
> make sure you make a swap file twice as large as the amount of ram you have
Not sure if this is required when you have more than 1GB. Just adding about 100mb more to the RAM size would be sufficient. I have 1GB RAM and 1.1GB swap, and never had a problem. (even half of the swap is never really utilized in my case). It would be an utter waste to have a 8GB swap if u have 4GB RAM (even if disk is cheap).

> You are allowed only to have 4 PRIMARY partitions
This is serious! Make sure you create a *huge* EXTENDED partition when u r partitioning. This will help u make any number of logical partitions in it, so that u can install and experiment with many different OSs. (Most modern OSs allow to install on a logical partition including ubuntu; exception=Solaris x86)

other points to note:

* make sure to create all your partitions before installing any OSs; This will save u a lot of trouble.
resizing and creating new partitions after installing OSs can break existing OSs due to partition numbers changing. 
(This will not break latests ubuntu distros since they use UUIDs, but other distros might break.)

* u can have a single SWAP partition and share it with all linux distros. 
(there can be some minor glitches due to the UUID scheme, but can easily be fixed. see [http://ubuntuforums.org/archive/index.php/t-560604.html]("http://ubuntuforums.org/archive/index.php/t-560604.html") )

---

### Post by indytim on 2008-08-31
Wolfie2x,

Wasn't your posting basically stated in the previous responses?

IndyTim

---

### Post by wolfie2x on 2008-08-31
> **indytim said:**
> Wolfie2x,
Wasn't your posting basically stated in the previous responses?

I don't see the '*non*-requirement of swap=doubel RAM', or 'single swap for multiple partitions' mentioned here before. 
also the emphasis on the 'extended partition' coz I got it wrong first and went through hell..  8-)

---

### Post by KeithA45 on 2008-09-02
Cool thanks guys, I think I'm ready to give this a try

The last thing I have left to ask is a rather odd one, but I'm curious about some opinions of sizes to make my Linux Partitions

I use mostly Windows and want to leave plenty of space on that for downloads, but I do want to have enough room for Ubuntu to do whatever I want with it (add-ons and such) that I'm not going to run out of room. I was thinking 50GB for each linux OS, but now it seems like too much. Suggestions?

Thanks

---

### Post by indytim on 2008-09-02
You should reasonably be able to get by with 3-5G for each ops. If you go the route of a dedicated /home partition for each ops (recommended at least for your "bread-and-butter ops), size that to accommodate the settings and whatever files you intend to store there.  I usually leave /home sized at ~10G with ample storage in other partitions also.

IndyTim

---

### Post by wolfie2x on 2008-09-02
Here's how I have it: 
* A large(50GB) separate partition (FAT32) to store all big files/data.  (shared among all OSs)
eg: music, videos, photos, games, VM files(2GB+) etc..
(can access on Windows too since it's FAT32)
* A 8GB ext3 partition for ubuntu 8.10. (still only 70% full even with loads of applications)
* and several other 8GB - 15GB partitions for testing other OSs  ;)

Even though I manage just fine with 8GB on my main OS partition, I think 10GB - 20GB would be safer.

---

### Post by KeithA45 on 2008-09-02
> **cotcot said:**
> I recommend using the Gparted LiveCD and to make for example following partitions for both OS :

/ for ubuntu : primary ext3
/home for ubuntu : logical ext3
/ for 'the other OS' : primary ext3
/home for 'the other OS' : logical ext3
swap (1 swap can be used for both OS)

Other setups are possible for sure.

And it is not forbidden to name 'the other OS'. We are always interested in your findings.

Thanks that's exactly what I'm going to do: 10GB for each / and 20GB for each /home, and a 2 GB swap (I have 1 GB RAM).

Finally, I was reading somewhere (I've already lost the site) that I need to set a mount point for the remaining Windows partition for that to be bootable, but when I tried the Ubuntu installer, it wouldn't let me set a mount point for the remaining windows parition

Do I really need to do that? help

Thanks in advance for helping out a true n00b =)
 - Keith

Edit: One more thing, do I make the "/" and "/home" partitions in GParted? Because I can't set the intended "/home" partitions to logical, it's just grayed out (I'm on the Live CD right now and posting on my laptop)

---

### Post by KeithA45 on 2008-09-02
*bump*

---

