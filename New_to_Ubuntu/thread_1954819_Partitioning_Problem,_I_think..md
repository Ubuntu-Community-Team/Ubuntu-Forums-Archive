---
title: "Partitioning Problem, I think."
date: 2012-04-08
forum: New to Ubuntu
---

### Post by JXR on 2012-04-08
I hope this problem isn’t a too convoluted
   
  Background:
  [FONT=Calibri]1)      [/FONT]I succeeded in installing Ubuntu 10.04 on a Dell Inspiron 2650
  [FONT=Calibri]2)      [/FONT]In order to get the Inspiron keyboard functional I successfully changed GRUB but it didn’t solve the problem.
  [FONT=Calibri]3)      [/FONT]Other advice from this forum encouraged me to try to load Ubuntu 10.04
  [FONT=Calibri]a.       [/FONT]After downloading necessary files (Using the Update Manager)- a process that took hours – I succeeded in getting to the install phase.
  [FONT=Calibri]b.      [/FONT]While in Install, the program froze (From what I could read of the partial window the program was asking me if I wanted to keep the altered GRUB install file. I was unable to click on the button, and after watching the CPU deadline for another 40 minutes I did a hard reset.
  [FONT=Calibri]4)      [/FONT]Not good installwise (Windows was the only system that booted.)
  [FONT=Calibri]5)      [/FONT]In order not to have to download all the material a second time, I got a copy of a Ubuntu 11.04 install disk but was informed I would have to download Wubi (2 Mb) in order to specify that I still wanted to install a dual boot.
  [FONT=Calibri]a.       [/FONT]I downloaded Wubi and ran it
  [FONT=Calibri]                                                               i.      [/FONT]Wubi informed me that it needed 256 MB and only 254 was available [I told it to continue]
  [FONT=Calibri]                                                             ii.      [/FONT]Wubi informed me that it needed 6144 MB disk space but only 3116 MB was available [I stopped it]
  [FONT=Calibri]6)      [/FONT]I decided I would try and reinstall Ubuntu 10.04 so that things would be copacetic on the computer (it would dual boot) AND THEN would try and install U 11.04
  [FONT=Calibri]a.       [/FONT]I installed 10.04.
  [FONT=Calibri]b.      [/FONT]I tried to run Wubi but it complained again.
  [FONT=Calibri]c.       [/FONT]I ran the 10.04 installer to look at the partition array. It said:
  [FONT=Calibri]                                                               i.      [/FONT]32.9 MB /dev/sda1    [Fat 16]
  [FONT=Calibri]                                                             ii.      [/FONT]19.1 GB MS Windows XP (/dev/sda2)   [ntfs]
  [FONT=Calibri]                                                            iii.      [/FONT]3.0 GB Free space
  [FONT=Calibri]                                                           iv.      [/FONT]4.3 GB Ubuntu 10.10 (/dev/sda5)   [ext4]
  [FONT=Calibri]                                                             v.      [/FONT]3.0 GB Ubuntu 10.04.3 LTS]   (/dev/sda7)  [ext4]
  [FONT=Calibri]                                                           vi.      [/FONT]/dev/sda 8          200 MB    swap
  [FONT=Calibri]                                                          vii.      [/FONT]/dev/sda 6          300 MB    swap
  [FONT=Calibri]d.      [/FONT]I tried to delete sda5 and sda6 figuring these were allotted to U 10.04 and hoping that if I could free up this space Wubi and U11.04 would be happier.
  [FONT=Calibri]                                                               i.      [/FONT]The program informed me “No root file system is defined (Please correct this from the partitioning menu)
   
  I WANT:
  [FONT=Calibri]-          [/FONT] To install Ubuntu 11.04 from the CD
  [FONT=Calibri]-          [/FONT]I want it to be a dual boot with Windows XP
   
  Questions:
  [FONT=Calibri]1.       [/FONT]At this point (Ubuntu 10.04 and XP dual boot working) should I be changing partitioning?
  [FONT=Calibri]a.       [/FONT]If so, how would you recommend I configure the partitions?
  [FONT=Calibri]2.       [/FONT]Is there another way to get Ubuntu 11.04 installed on this computer?

---

### Post by Basher101 on 2012-04-08
I got somewhat of an idea what you did, but i kinda lost it at the end..to give you more accurate advice please run Gparted (from your Ubuntu install or the live cd, you might need to install it when not using the live cd) and post a screenshot here.

Gparted can be found in the software center

---

### Post by oldfred on 2012-04-08
Post gparted screen shot as Basher101 suggests. 

Your drive does not look very large. You probably need to delete all the old linux & swap partition just to have barely enough room. The minimum install is now just over 4GB, but the minute you do updates you run out of room. 
You may be able to get by with 5 or 7GB, normally 10 is the suggestion so you do not have to houseclean and be careful on downloading too much.

Note that wubi is a different installer that installs inside your Windows install and if XP is only 19GB it would not have room for a wubi install.

---

### Post by JXR on 2012-04-08
GParted screeenshot attached.

[IMG]file:///home/joost/Desktop/Gparted%20screen.png[/IMG]

---

### Post by Basher101 on 2012-04-08
you have 2 swap partitions, which indicates you had 2 installs. So far so good. 

You should get rid of them both, both ext 4 partitions, the extended parition, then use the 2 gb unallocated space and the newly gained free space to create a new extended partition, which will include one ext4 partition and Swap. 

How much RAM do you have? you should use the same amount for the swap.

edit: so in the end you should have a ~10 GB extended partition.

---

### Post by JXR on 2012-04-08
you have 2 swap partitions, which indicates you had 2 installs. 
.      Right. The 10.10 (which didn't install completely), and the 10.04 (which did)

So far so good. 
.      Oh Good!! It feels good to have something good happen!

You should get rid of them both, both ext 4 partitions, the extended  parition, then use the 2 gb unallocated space and the newly gained free  space to create a new extended partition, which will include one ext4  partition and Swap. 
.      This will delete both installations of Ubuntu right? 
.      When I try and delete sda5 (Gparted) it tells me it is unable to do so until I unmount all logical partitions above sda5. I guess what it's really telling me is that I can't do the repartitioning while running Linux.
.       What do I do about the approximately 500 MB of linux swap space?
.       If I reboot with the LiveCD and use GParted to do this. Will I get the same root partition complaint from that program?
.      

How much RAM do you have? you should use the same amount for the swap.  
.       256 Mb   (not much)

---

### Post by GregA on 2012-04-08
Just a couple quick tips:

1).   Use a Live Linux CD such as "PartedMagic" to do your partioning and cleanup work (using the gparted app).   That way you will not have the issues you describe.  
2).   Do not try to install Ubuntu, your system is not up for it.  Try a lighter distro such as "Lubuntu" instead.

---

### Post by oldfred on 2012-04-08
Good advice above.

Does you XP work? It is my understanding that NTFS like 30% free, slows at 20% free and at 10% just about stops working. I think you also need to houseclean as much as possible from XP. If you did try to install Wubi you should uninstall.

---

### Post by mal1958 on 2012-04-08
Normally I would be pointing out that my old system can and does handle Ubuntu very well.  [COLOR="Blue"](P3 1Ghz, 512 mb ram, 2 60 gig HDs and an nVidia 6200 geforce vid card)[/COLOR]  But here I have to agree with GregA and oldfred.  I would recommend that you not go for Ubuntu but look at the lubuntu flavor.  I saw from your gparted pic that you have a total of 30 gigs on your HD.  If this were me, I would look at replacing the HD with one that had a bit more space.  30 gigs can go bye bye very quickly, and require a lot of effort in the house cleaning.

---

### Post by JXR on 2012-04-09
In order to do the housecleaning you recommend I
1) Booted from a LiveCD
2) Brought up Gparted

According to GParted help since I am booting off a CD all partitions are available to manipulate.

In actuality none of the partitions could be unmounted ("Unmount" was dimmed in the menu) except the Linux swap partitions for which the action "Unmount" was not even available!

Furthermore, a number of partitions seem locked and I can't find anything in GPartition help that addresses unlocking those partitions. 

So it seems I can do nothing with the partitions using GParted started from a LiveCD (to get to GParted I ran Unbutu from the CD).

Yes XP still works, but now much less of the space on the hard disk is available to it.

I would have been relatively happy to work with Ubuntu 10.04 in order to get acquainted with Linux but nothing anyone suggested (except upgrading to a more recent version where the keyboard/touchpad problem had been addressed) worked. I doubt the problem would have been addressed in a lighter/previous version of lubuntu--but I could be wrong about this.

(On a sidenote, why, whenever I want to post a reply do I have to log in to the forum repeatedly? I log in, I am welcomed, I locate the message and want to post a reply and I have to log in again...I read a reply to mine...then want to send a reply and I'm forced to log in again. This did not happen the other day when I was having problems loading Ubuntu. Have I committed some sort of greviance?)

---

### Post by oldfred on 2012-04-09
I just have it remember my login and it works, so not sure what your issue is there.

To edit partitions they all have to be unmounted. The liveCD often mounts swap(s) and will show the little key symbol to show they are mounted. You just need to click on each swap and right click choose swap off to unmount the swap partitions.

---

### Post by JXR on 2012-04-09
I decided to take your advice and boot to Lubuntu. But now I'm worried that the odd disk partitioning I was left with is messing up that install. After going through the blue screen/white letters Lubuntu install and instructing it to run Lubuntu to run from LiveCD it chugs for a while and presents a commandline (white letters on black screen - sudo) interface.

Is this the Lubuntu interface?????

---

### Post by oldfred on 2012-04-09
I know in Ubuntu that would probably mean a video issue of some sort but am not familiar with Lubuntu. 

The startup is different and I think you get the text mode menu? Can you add nomodeset from that?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

