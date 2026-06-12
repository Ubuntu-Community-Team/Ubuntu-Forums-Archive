---
title: "Windows on C drive, install Ubuntu on E Drive?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by you123456 on 2008-11-20
Hi all, 
i am currently using windows XP sp2, and it is installed in C drive of windows. I have 2 partitions, hence  i drives C and D.

I intend to install a new drive ( drive E ) manually and install Ubuntu 8.10 on drive E. ( without removing windows on drive c )

May i know if this is possible? What do i need to look out for?

Best Regards,
Eugene
PS: I have already downloaded ubuntu 8.10 and burned it on a cd.  i intend to install from disk.

---

### Post by TripitakaUK on 2008-11-20
That was timely! Apologies for the hijack but it is relevant, I promise!

I have just installed hardy in this config (almost) and put the boot loader in the sda drive where sda1 is my Windows install. Ubuntu has installed on sdb.

When I reboot, all I get is GRUB GRUB GRUB filling the screen and scrolling, so...

1) watch out for that and,
2) how do I fix it?

---

### Post by rbprogrammer on 2008-11-20
It sounds like what you want to do is dual boot windows and ubuntu.  Basically all you really need to do is set up two partitions, one formatted as ext3 (as big as you want) and one formatted as swap (about 1/2 GB to 1 GB).  Then in the ubuntu installer you choose the ext3 partition to mount as "/" (without quotes) and the swap partition will be handled automatically.  The installer will handle everything regarding the dual boot, meaning it will give you the option when you start your computer which operating system you want to boot into.

Hope that wasn't too confusing..

---

### Post by rbprogrammer on 2008-11-20
Also, for the record if you didn't find this out yet, but in Linux, there are no drive letters ie C: or E:, there are mount points.  It gets a little confusing, but I think all you really need to know is the mount / at the "ext3" partition and swap space in the "swap" partition

---

### Post by billgoldberg on 2008-11-20
> **you123456 said:**
> Hi all, 
i am currently using windows XP sp2, and it is installed in C drive of windows. I have 2 partitions, hence  i drives C and D.

I intend to install a new drive ( drive E ) manually and install Ubuntu 8.10 on drive E. ( without removing windows on drive c )

May i know if this is possible? What do i need to look out for?

Best Regards,
Eugene
PS: I have already downloaded ubuntu 8.10 and burned it on a cd.  i intend to install from disk.

Sure, just fire up the Ubuntu installer and pick the empty partition/drive.

Just to let you know, naming the drives with a letter (C drive, E drive) is a Windows only thing.

In Ubuntu your drive will be called "sda1" or something.

---

### Post by philinux on 2008-11-20
> **TripitakaUK said:**
> That was timely! Apologies for the hijack but it is relevant, I promise!

I have just installed hardy in this config (almost) and put the boot loader in the sda drive where sda1 is my Windows install. Ubuntu has installed on sdb.

When I reboot, all I get is GRUB GRUB GRUB filling the screen and scrolling, so...

1) watch out for that and,
2) how do I fix it?

Best to start your own thread. Then it would be more relevant.

---

### Post by LowSky on 2008-11-20
> **you123456 said:**
> Hi all, 
May i know if this is possible? What do i need to look out for?
  

Yes it is possible but Linux does not use drive letters( like C:\)

It will still find the drives, when installing use the option to manually partition the hard drive, a screen will com up and show you a bunch of gibberish if you have never seen it before.

Your Windows Partition will have the partition formated to NTFS so look for that, infact all you pre partitioned drives will be there, the new drive will not have any formats unless you have mede them, so be on the lookout

find the drive you want and partition it the way you like, I suggest 15GB for / (root), a seperate /home patition of any size you like over 4GB and the a swap partition of about 2GB

---

### Post by you123456 on 2008-11-21
HI al, than k you for the reply.
May i know if the new hard disk (&#65353;&#65358;&#12288;&#65357;&#65369;&#12288;&#65347;&#65345;&#65363;&#65349;&#12288;&#65289;should be set to slave ? While the C drive remains as master drive?

Best.

---

### Post by you123456 on 2008-11-21
> **LowSky said:**
> .....

Your Windows Partition will have the partition formated to NTFS so look for that, infact all you pre partitioned drives will be there, the new drive will not have any formats unless you have mede them, so be on the lookout

find the drive you want and partition it the way you like, I suggest 15GB for / (root), a seperate /home patition of any size you like over 4GB and the a swap partition of about 2GB


By the way, how do i check for the file system on my PC? How do i know if it is NTFS ?

Best.

---

### Post by you123456 on 2008-11-21
Oh just another question: does installing ubuntu ( dual boot ) have to be on a empty drive?

---

### Post by hyper_ch on 2008-11-21
have a read here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

furthermore: Be sure to have backups. Re-partitioning your drive can corrupt it (not the case normally - but you can make mistakes).

---

