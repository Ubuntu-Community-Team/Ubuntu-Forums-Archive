---
title: "installing linux on an xp system (partition question)"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by UIIIU on 2008-06-23
ok im not the brightest person in the world and have a question.  I have xp installed on my comp and decided to put ubuntu on it too so i could dual boot.  I started installing then got to the partition part and got very confused theres too many options.  heres what it says i chose manual because the guided just has it using my whole drive. heres what it looks like

prepare partitions

Device ()  Type ()  mount pt. ()  format? () size ()   used
/dev/sda
 /dev/sda1()fat16()/media/sda1 ()box   ()   106 MB ()   33MB
 /dev/sda2()ntfs()/media/sda2  ()  box ()99920 MB()  unknown


Edit partition / delete / etc.

()= just separating categories


any help on what to do would be greatly appreciated

---

### Post by omi291 on 2008-06-23
was there no option for resizing your windows partition at the partition menu?

---

### Post by UIIIU on 2008-06-23
Ya i couldnt find one. When i clicked on guided it just geve me one option and it was a 100GBs my whole hard drive

---

### Post by Victormd on 2008-06-23
The manual option is in fact the best way to go, much safer...
First of all, back up all your data.
You will need to edit the windows partition and resize it. Then try to leave ~5-10GB for Ubuntu and anywhere from 512MB - 1GB for swap.

---

### Post by UIIIU on 2008-06-23
victor i would go about doing this how? im not too worried about losing stuff in windows i would like to keep it but if its gone its no big deal so ill consider it all backed up but how do i resize the windows partition?

---

### Post by Victormd on 2008-06-23
Let me just fire up my other comp. so that I'll have the setup in front of me...

---

### Post by Dutch70 on 2008-06-23
Maybe this will help, if you dont have it already.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Edit: or this... [http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)

Dutch

---

### Post by Victormd on 2008-06-23
Ok. First, boot the live CD so we can use the partition program - GParted
Go to SYSTEM>ADMINISTRATION>PARTITION EDITOR
You will be presented with a graphical representation of your HD.

---

### Post by UIIIU on 2008-06-23
ok i have the cd booted up

Partition program im not to sure what that is

ok i fired up gparted
 
i have like 50 gbs used on my comp so should i go bigger?

it ssys minimum size is 53089 Mib and max is 95292 MiB

ok i think i did it right, but now i have 42 GBs of unallocated space

---

### Post by Victormd on 2008-06-23
Ok. In the graphical interface, click to select your XP partition and then click on the RESIZE/MOVE button and resize by entering 10512 (this is in MB - You can choose a larger partition if you'd like) in the "Free Space Following (MIB) box". and click on the Resize/Move button.
This will schedule Gparted to resize this partition and will leave 10512MB of free space after.
Now, click on the free space and the NEW Button

EDIT: I quoted your previous post so it moved on to the next page... :)

---

### Post by Victormd on 2008-06-23
***

---

### Post by Victormd on 2008-06-23
> **UIIIU said:**
> i have like 50 gbs used on my comp so should i go bigger?

it ssys minimum size is 53089 Mib and max is 95292 MiB

That's the minimum and maximum size of the existing partition. Ultimately, it will have ~84000MiB

You'll enter the 10512 in the space for the "Free Space Following (MiB)" and that means that your current partition will be reduced by 10512MB.

When you click the Move/Resize Icon to finalize the operation, you'll notice an information area at the bottom with 1 operation pending.

42GB of unallocated space? That means that your windows partition has zero space available... that's too much unallocated space (hit the undo button :)).

If you didn't hit the Apply button, don't do it, wait until all the modifications are made.

---

### Post by UIIIU on 2008-06-23
im not sure if i did it right but now i have a new partition with 15 gbs on it

i have 3 the first 2 were there when we started and the third one is the new one and there is no unallocated space

ok i reduced it i now have 590 mbs of unallocated space

---

### Post by Victormd on 2008-06-23
15GBs, that's fine! :)
Just so we're on the same track, how many partitions do you have (allocated and unallocated)?

Ok, now click on the partition you just created (the 15GB one)and you're going to resize it, reducing by 512MB (this will be used for linux-swap).

---

### Post by Victormd on 2008-06-23
> **UIIIU said:**
> im not sure if i did it right but now i have a new partition with 15 gbs on it

i have 3 the first 2 were there when we started and the third one is the new one and there is no unallocated space

ok i reduced it i now have 590 mbs of unallocated space

Now you'll have 4 partitions:
1 = XP Partition
2 = XP Recovery (I'm guessing here)
3 = Ubuntu partition (~14.5GB)
4 = Linux Swap (590MB)

Don't worry about formatting them, here we're just setting your HD up. The formatting will be done during the install.

If you have any operations pending (bottom of the GParted window), hit the apply button and you'll be ready to begin your install.

---

### Post by UIIIU on 2008-06-23
yep thats exactly how it looks

the 590 mbs is still unallocated is that alright?

an error came up when applying operations

it says the following operation could not be applied to disk 

resize/dev/sda2 from 93.06 gb to 78.13 gb

for more details it just says

create primary partition #1 (ext3, 13.67gb) on /dev/sda

---

### Post by Victormd on 2008-06-23
Ok, now to the install...
Just hit the install icon on the desktop and answer the questions until you reach the partition editor in the installation process.

> **UIIIU said:**
> yep thats exactly how it looks

the 590 mbs is still unallocated is that alright?

Yeah, we'll take care of that during the installation process (as long as there are no pending operations... :)).

When you get to the "Prepare disk space" dialog, choose the Manual option and it should show you a similar setup as you had in Gparted.

---

### Post by Victormd on 2008-06-23
> **UIIIU said:**
> it says the following operation could not be applied to disk 

resize/dev/sda2 from 93.06 gb to 78.13 gb

for more details it just says

create primary partition #1 (ext3, 13.67gb) on /dev/sda

Humm... let me think about this a sec...
Did you shut down windows properly before starting this?

---

### Post by UIIIU on 2008-06-23
yep i believe so the only thing i can think of is instead of having the new partition as the primary could i make itextended partition?  or maybe just have 2 partitions and 15 gbs of unallocated space?  

no that didnt work either

---

### Post by Victormd on 2008-06-23
> **UIIIU said:**
> yep i believe so the only thing i can think of is instead of having the new partition as the primary could i make itextended partition?

Well, you're allowed to have 4 logical partitions so that shouldn't be a problem. From the error you posted, it's not resizing your windows partition and that's what I'm trying to figure out why...

If you can leave just the 15GB of unallocated space, that would work... as long as it lets you resize...

---

### Post by Victormd on 2008-06-23
> **UIIIU said:**
> yep i believe so the only thing i can think of is instead of having the new partition as the primary could i make itextended partition?  or maybe just have 2 partitions and 15 gbs of unallocated space?  

no that didnt work either

Do you have 2 partitions on 1 HD or do you have 2 HDs?

Even though you have the installer open, you can still access ubuntu running off the live CD.
Go to Applications>Accessories>Terminal
and in the terminal, type
```
sudo fdisk -l
```
and post the output please.

NOTE:If this is a desktop connected via a wired ethernet cable, you should have access to the internet with it so you can just copy and paste.. :)

---

### Post by UIIIU on 2008-06-23
I dont have connection with  the laptop right now im restarting the comp and i will try that as soon as i get it started

---

### Post by Victormd on 2008-06-23
Ok. so no changes were committed to your HD?

---

### Post by UIIIU on 2008-06-24
there was some stuff before this but i think this is what u need

here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7

-u: give start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors



no changes to my hard drive and

---

### Post by Victormd on 2008-06-24
/dev/sda is the disk and /dev/sda1 is partition 1 of that disk. If you have two disks, you would have something like
/dev/sda1
/dev/sdb1
This is what mine looks like:
> 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4400    14860125   83  Linux
/dev/sda3            4401        4462      498015   82  Linux swap / Solaris
/dev/sda4            4463        9725    42275016    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008139c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Which means I have an 80GB HD with 4 partitions and a 320GB HD with 1 partition.

---

### Post by UIIIU on 2008-06-24
ya both mine that come up are sda

sda1 and sda2

---

### Post by Victormd on 2008-06-24
How big are sda1 and sda2? 


Let's try partitioning one more time.
Like before, open up Gparted and resize simply to create the 15GB unallocated space. We'll split the unallocated space in 2 during the install.

---

### Post by UIIIU on 2008-06-24
no dice it still wont re size the partition

---

### Post by Victormd on 2008-06-24
Is the second partition a recovery partition or is it a data partition? If it's recovery, have you made the recovery CDs?
The reason I'm asking, is because, if it's a recovery partition, you can delete it and install ubuntu on it... :)

---

### Post by UIIIU on 2008-06-24
i have no idea what it is the first drive which i left alone is sda1 and its only 101 mbs in fat16 the second one which i did the stuff to is 93 gbs and its labeled sda2 in ntfs

---

### Post by Victormd on 2008-06-24
> **UIIIU said:**
> i have no idea what it is the first drive which i left alone is sda1 and its only 101 mbs in fat16 the second one which i did the stuff to is 93 gbs and its labeled sda2 in ntfs

101MB is not enough... :)

It's strange that gparted won't resize your partition. I know it won't handle vista partitions yet but XP partitions it shouldn't have any problems with...

---

### Post by UIIIU on 2008-06-24
ya i have no idea what it is.  Just my endless curse of bad luck

---

### Post by Victormd on 2008-06-24
Ok, then, do you want to try to resize your XP partition using the installation Partition Editor?

---

### Post by UIIIU on 2008-06-24
ya why not

ok

when i click on edit partition it says just 2 things

use as: ntfs (with option to pick other things)

Mount point: /media/sda2 (with option to pick other things)

---

### Post by Victormd on 2008-06-24
Ok, start the installation and when you get to the partition manager, choose Manual.
click on /dev/sda2 (your windows partition) and click on the Edit partition button and under New partition size in megabytes, reduce it by 15Gb (~85000)

A dialog box with a warning will pop up, click Continue and it should now show the partition and an unallocated space (I don't remember if it applies as you go or if it will apply everything when you're finished). If it starts to apply, with no errors, it will take a while but at least it's resizing it. Let me know if it starts to apply automatically or not.

---

### Post by Victormd on 2008-06-24
> **UIIIU said:**
> use as: ntfs (with option to pick other things)

Mount point: /media/sda2 (with option to pick other things)

This showed up when you clicked on the edit and resized it (I'm asking because this is actually the first time I partition through the install...)?

Note: You want to use as ntfs otherwise you'll loose windows... :)
**[COLOR="Red"]DO NOT MARK THE "FORMAT THE PARTITION" OPTION[/COLOR]**
and the mount point will be /media/sda2

---

### Post by UIIIU on 2008-06-24
i didnt re size it i just clicked edit partition and it gave me those 2 options

it gives me no options for size whatsoever

i know what u r talking about tho because i pressed edit partition on the 101 mb partition and it gave me the option

---

### Post by Victormd on 2008-06-24
the first line should allow you to choose the size of the partition (New partition size in megabytes).

---

### Post by Victormd on 2008-06-24
> **UIIIU said:**
> it gave me those 2 options

it gives me no options for size whatsoever

what??? That's just odd!
What version of ubuntu are you trying to install?

---

### Post by UIIIU on 2008-06-24
i believe it is version 8.04

---

### Post by Victormd on 2008-06-24
That is very strange.
Earlier versions of Ubuntu didn't handle resizing NTFS (as far as I know), but if it's 8.04, it doesn't handle vista partitions but since this is XP, then I honestly don't know what's going on and why it won't let you resize... The only thing I can think of is that windows wasn't shut down properly (or was hibernating/standby) and this locks the HD for any type of editing. If this is the case the fix is, remove the boot CD, restart into windows, put in the boot CD and then from windows, restart the computer and try these steps again...

---

### Post by UIIIU on 2008-06-24
I just double checked that and it is not 8.04 its 7.04.  Well thats all im gonna try for tonight I cant thank you enough for all your time I know this is random but if your into poker you should come join my site tiltthetable.com

---

### Post by Victormd on 2008-06-24
I was just looking at [this thread]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3") and it seems like 7.04 will in fact give you a hard time partitioning NTFS and you'll need to download some other tools to do this. Download the latest version (8.04), burn the CD and go from there, or look at the link I posted. I believe it'll be easier to download and install the latest version.

---

### Post by Victormd on 2008-06-24
> **UIIIU said:**
> Well thats all im gonna try for tonight I cant thank you enough for all your time I know this is random but if your into poker you should come join my site tiltthetable.com

Yeah, I gotta go as well...

Not much of a poker player but will check out your site.

Download the latest version and follow the steps we went though here.
Let me know how it goes...

---

### Post by UIIIU on 2008-06-24
thanks ill burn the latest ill let ya know how it all goes when i get around to it

---

### Post by Victormd on 2008-06-24
Alright... good luck!

---

### Post by chronographer on 2008-06-24
One other option is if you don't want to DL the whole new ubuntu CD, to download gparted live cd [here.]("http://gparted.sourceforge.net/livecd.php") and it is much smaller than Ubuntu. 

Of course, if you can afford the downloads then get the 8.04 CD because it is a superior release! I am having a really good time with the gutsy gibbon, no problems so far!

agl

---

### Post by Victormd on 2008-06-24
Yeah, Gutsy is very nice. The version UIIIU has is Feisty Fawn though.
I've heard it's also very nice but Gutsy and Hardy have better hardware support.

---

