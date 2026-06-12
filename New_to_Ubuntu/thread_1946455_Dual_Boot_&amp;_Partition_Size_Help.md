---
title: "Dual Boot &amp; Partition Size Help"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by Wi11iwaw on 2012-03-24
Hi all,
I am very new to Linux and was hoping I could get some help.  
I recently bought a Dell XPS 13 and would like to dual boot Ubuntu with  it.  I have installed Ubuntu before, but I have never tried a dual boot.

My first question:  Can I partition 1 for Windows, 1 for Window  recovery, 1 for Ubuntu and then 1 partition to store all data (photos,  docs, ect..) to be used for both OS at any given instance.  Is this  possible or ideal?

Also, I was wondering what your thoughts were on partition sizes for the  above set up.  I am currently using Ubuntu and am using about 10GB  total.

I have been looking around and have read this ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)).   It seem pretty strait forward, but I was wondering if anybody else had  some instructions to recommend...eg: booting into Unbutu first.

**EDIT**
My computer uses the i5 64bit, so I should use the 64bit Ubuntu download...right?

Thanks all for your help...and sorry for being such a noobie.

---

### Post by forrestcupp on 2012-03-24
During installation, there is an option to manually partition however you want. I can't remember for sure, but I think that option might be called something like "Do something else". Just make sure you back up all of your important files before you go messing with the partitions. The partition you use to share between Windows and Ubuntu should probably be NTFS, because Ubuntu does a lot better with NTFS than Windows does with Ext.

As for the sizes of the partitions, that all depends on how you want to use things, and what your priorities are. We can't even really help you at all with that without even knowing the total size of your hard drive.

And you should use 64-bit.

---

### Post by Bucky Ball on 2012-03-24
Your link looks pretty good.

One important thing to remember is that four primary partitions are the maximum on any one physical hard drive so I would recommend something like this:

* Install Windows FIRST. This makes life a LOT easier. 30Gb for the Windows OS is fine;
* Leave the rest free space for the Ubuntu install;
* Create an extended partition with all of the free space (you can do this with Gparted on the Ubuntu LiveCD.
* Install Ubuntu on logical partitions inside the extended partition (you can have as many logical partitions as you like - theoretically - inside an extended partition which negates the four partition limit);
* When you are installing Ubuntu and you get to the partitioning section, choose 'Something Else' to manually partition;
* Create your partitions thus:
/ = for Ubuntu OS; 20Gb fine
/home = your personal data; large as you like
/swap = 2Gb fine

You said you want a shared partition between the two OSs? You will need to make that an NTFS partition and put that inside the extended partition also. 

Another point: Ubuntu will happily live inside an extended partition on a logical drive, Windows will not ... put that first drive, first partition. It likes it that way. 

When you are doing this bit, you will plainly see the Win partitions (they will be NTFS) so just leave 'em alone and make sure they are not ticked to format (they shouldn't be by default). The free space should be plainly visible also (where you are about to install Ubuntu).

Yes, download the 64bit version. 10.04 LTS is rock solid and the current long-term support release with support for another thirteen months. The choice, of course, is yours (but I would avoid 12.04 LTS as it's still 'testing', not released yet and expect breakages).

Good luck ... ;)

---

