---
title: "Changing partition size"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Nanur on 2012-06-18
So my Ubuntu partition was originally set for 10GB, but I have used up all that space and want to increase my partition size. I have ~9GB left on the hard disk I installed Ubuntu on, and would like to increase the partition size to 17GB (+7GB). What would be the easiest way to do this.
Thanks!

---

### Post by jkurtisr32 on 2012-06-18
> **Nanur said:**
> So my Ubuntu partition was originally set for 10GB, but I have used up all that space and want to increase my partition size. I have ~9GB left on the hard disk I installed Ubuntu on, and would like to increase the partition size to 17GB (+7GB). What would be the easiest way to do this.
Thanks!

Are you familiar with gparted? This would be the easiest way to re-size.

---

### Post by Nanur on 2012-06-18
I installed it, and looked at it, but couldn't find my Ubuntu partition

---

### Post by jkurtisr32 on 2012-06-18
> **Nanur said:**
> I installed it, and looked at it, but couldn't find my Ubuntu partition

Ubuntu runs off of several partitions. Usually including a SWAP area and ROOT (denoted as a '/'). You need to figure out which one is the ROOT and expand it.

ROOT will be the partition that is formatted in EXT4 usually.

---

### Post by Bucky Ball on 2012-06-18
The best (and only) way to do this is to boot from the LiveCD, 'Try Ubuntu', once at the desktop launch Gparted and away you go. Right click the partition you want to resize and click 'Resize'. You are not getting that option now because the partitions are mounted (which they won't be when you boot from the LiveCD).

The partitions need to be unmounted to resize. That is impossible if you are running the OS from the partition you're wanting to resize. ;)

@[jkurtisr32]("http://ubuntuforums.org/member.php?u=1128110"): Partitions mount points are clearly identified in Gparted and will appear exactly that way:

/ (root)
/swap

(OP may also have a separate /home or others.)

---

### Post by jkurtisr32 on 2012-06-18
> **Bucky Ball said:**
> The best (and only) way to do this is to boot from the LiveCD, 'Try Ubuntu', once at the desktop launch Gparted and away you go. Right click the partition you want to resize and click 'Resize'. You are not getting that option now because the partitions are mounted (which they won't be when you boot from the LiveCD).

The partitions need to be unmounted to resize. That is impossible if you are running the OS from the partition you're wanting to resize. ;)

@[jkurtisr32]("http://ubuntuforums.org/member.php?u=1128110"): Partitions mount points are clearly identified in Gparted and will appear exactly that way:

/ (root)
/swap

(OP may also have a separate /home or others.)

Ahhhhh, good points here.

---

### Post by Nanur on 2012-06-18
Okay, but this is what I see:
Odd picture. (running dual monitors)

---

### Post by Nanur on 2012-06-18
> **Bucky Ball said:**
> The best (and only) way to do this is to boot from the LiveCD, 'Try Ubuntu', once at the desktop launch Gparted and away you go. Right click the partition you want to resize and click 'Resize'. You are not getting that option now because the partitions are mounted (which they won't be when you boot from the LiveCD).

The partitions need to be unmounted to resize. That is impossible if you are running the OS from the partition you're wanting to resize. ;)

@[jkurtisr32]("http://ubuntuforums.org/member.php?u=1128110"): Partitions mount points are clearly identified in Gparted and will appear exactly that way:

/ (root)
/swap

(OP may also have a separate /home or others.)

Only problem here is I booted from flash drive (and installed) and I cleaned the flashdrive (wiped it)

---

### Post by Nanur on 2012-06-18
Also, I just put my flash drive in, and I cannot open it.
Says no applications can open it..

---

### Post by jkurtisr32 on 2012-06-18
> **Nanur said:**
> Only problem here is I booted from flash drive (and installed) and I cleaned the flashdrive (wiped it)

Gotta make a new one, bro

---

### Post by jkurtisr32 on 2012-06-18
> **Nanur said:**
> Also, I just put my flash drive in, and I cannot open it.
Says no applications can open it..

Use gparted and format that ************ to fat32

---

### Post by Nanur on 2012-06-18
Is it possible to edit partitions from Windows 7?

---

### Post by Bucky Ball on 2012-06-18
The flash you may need to mount manually to recreate your boot device (there is no other real way of resizing the / partition, as explained).

But first, could you give a screen shot only of the Gparted screen, please? In the screenshooter there is the option to take a shot of only the active window. Give yourself a couple of seconds interval before the shot, click the gparted window.

The one you've posted; the Gparted info is to small to read. ;)

[QUOTE=Nanur]Is it possible to edit partitions from Windows 7?[/QUOTE]

No. EXT* partitions are unrecognised. And definitely DON'T use gparted to resize windows install partitions (where Win is, not FAT or NTFS generally). That can cause real problems. But if you have Win installed, does the USB dongle work there? Sounds like perhaps it hasn't been shut properly. Insert (in Win), if recognised 'Safely Remove', try in Ubuntu again.

---

### Post by Nanur on 2012-06-18
Here is a better screenshot:

---

### Post by Nanur on 2012-06-18
> **Bucky Ball said:**
> 
No. EXT* partitions are unrecognised. And definitely DON'T use gparted to resize windows install partitions (where Win is, not FAT or NTFS generally). That can cause real problems. But if you have Win installed, does the USB dongle work there? Sounds like perhaps it hasn't been shut properly. Insert (in Win), if recognised 'Safely Remove', try in Ubuntu again.
The USB works fine in Windows. So I need to go into Windows and 'Safely Remove?'

---

### Post by Bucky Ball on 2012-06-19
Yes. Safely remove then try in Ubuntu. I think, though, that it is a problem with Ubuntu mounting so you may need a manual mount.

> **jkurtisr32 said:**
> Use gparted and format that ************ to fat32

This is pointless as the Ubuntu ISO is about to go there which will format the USB with EXT4. If all good in Win, then a Ubuntu mount issue. ;)

Put USB in with Ubuntu, open terminal, post back result of this command:

```
lsusb
```That will show if it is recognised. Incidentally, how did you create the USB install originally?

---

### Post by Nanur on 2012-06-19
So I booted onto Windows, did what you said, booted back into Ubuntu, and the USB works :D.
I used Universal USB Installer to put make the USB a bootable device.

So I have to boot back into Windows, and make my USB a bootable device (again)?
(I have to use Windows since there is no space to download the .iso file on my Ubuntu partition)

---

### Post by jkurtisr32 on 2012-06-19
> **Bucky Ball said:**
> 
This is pointless as the Ubuntu ISO is about to go there which will format the USB with EXT4. If all good in Win, then a Ubuntu mount issue. ;)


I usually use unetbootin to make my USBs, and I was pretty sure that it didn't alter the filesystem of the drive. Now you've got me second guessin'.

Either way, seems like you're doing alright with the OP, so I'm going to **** off

---

### Post by Nanur on 2012-06-19
Okay, I made the bootable USB stick, and booted into it. I see
the exact same thing in GParted as I did when I was on the 
regular Ubuntu partition. Err!

---

### Post by Bucky Ball on 2012-06-19
What do you see? Use the top right drop down to change to the USB (prob sdc).

Going back to your screenshot: What is /host? And is Ubuntu installed on there anywhere? I see no EXT* partitions. Is this a Wubi install (Inside Windows) or a virtual machine?

---

### Post by Nanur on 2012-06-19
> **Bucky Ball said:**
> What do you see? Use the top right drop down to change to the USB (prob sdc).

See attachment 
EDIT: attached wrong file, look at new one.
The attachment is of the USB.

> **Bucky Ball said:**
> 
Going back to your screenshot: What is /host? And is Ubuntu installed on  there anywhere? I see no EXT* partitions. Is this a Wubi install  (Inside Windows) or a virtual machine?
Yes, this is a Wubu install.
Also, on my Windows side, when I open my C: there is just a "Ubuntu" folder. 
If I remember correctly (a friend showed me) on the hard drive in Windows Explorer it showed a little line where the partition was.. my best drawing: [       |  ]
I may have been derping this whole time, and never actually set up a partition, but I am pretty sure when I installed Ubuntu, I clicked 10GB partition size.


Since I have a 300GB hard drive I use for storage mainly.. would it just be easier to re-install Ubuntu onto that drive and just make a much larger partition. The drive is internal by the way.

---

### Post by Bucky Ball on 2012-06-19
> **Nanur said:**
> 
Yes, this is a Wubu install.
Also, on my Windows side, when I open my C: there is just a "Ubuntu" folder. 
If I remember correctly (a friend showed me) on the hard drive in Windows Explorer it showed a little line where the partition was.. my best drawing: [       |  ]
I may have been derping this whole time, and never actually set up a partition, but I am pretty sure when I installed Ubuntu, I clicked 10GB partition size.

Ah, okay. This makes things clear. A completely different kettle of fish. No, there is no Ubuntu partition there (would show as EXT3 or 4); a Wubi install is basically like installing any other program in Win. You have given the Wubi install 10Gb ***inside*** the Win partition. 

Sorry to say, never use Wubi and wouldn't have the foggiest how to change the size of how much Windows allocates to it. It could be as simple as changing it in some preference menu or other.

This I will add; Wubi is for checking out Ubuntu to see how you like it, not a permanent solution. A full hard drive install - although perhaps not possible with your current setup - is a better, slightly faster, more flexible user environment.

---

### Post by Nanur on 2012-06-19
> **Bucky Ball said:**
> Ah, okay. This makes things clear. A completely different kettle of fish. No, there is no Ubuntu partition there; a Wubi install is basically like installing any other program in Win. You have given the Wubi install 10Gb inside the Win partition. 

Sorry to say, never use Wubi and wouldn't have the foggiest how to change the size of how much Windows allocates to it. ;(

This I will add; Wubi is for checking out Ubuntu to see how you like it, not a permanent solution. A full hard drive install is a better, slightly faster, experience, although perhaps not possible with your current setup.

Since I have a  300GB hard drive I use for storage mainly.. would it just be easier to  re-install Ubuntu onto that drive and just make a much larger partition.  The drive is internal by the way.
Also, is there a way to transfer over my current Ubuntu files and such over onto a new, permanent installation?

---

### Post by Bucky Ball on 2012-06-19
Data files in Ubuntu? I would think so. Install Ubuntu on the other hard drive and then just grab 'em from the Windows partitions. (Ubuntu can read/write NTFS and FAT fine and you should be able to see and access the Win partitions/folders fine, too). 

How much free space do you have on the other drive? For that you could boot from the LiveCD, open Gparted and you should be able to right click, unmount the partition, resize it to make free space for Ubuntu to install to (shrink the, I presume, 300Gb partition). Once this is done you could then continue with the Ubuntu install by clicking the icon on the desktop. 

Shrinking it with Windows is another option, though. Simple and Win already there.

---

### Post by Nanur on 2012-06-19
> **Bucky Ball said:**
> Data files in Ubuntu? I would think so. Install Ubuntu on the other hard drive and then just grab 'em from the Windows partitions. (Ubuntu can read/write NTFS and FAT fine and you should be able to see and access the Win partitions/folders fine, too). 

So by "grab 'em" you mean 'copy-paste' after I re-install?


> **Bucky Ball said:**
> 
How much free space do you have on the other drive? For that you could  open Gparted and you should be able to right click, unmount the  partition, resize it to make free space for Ubuntu to install to (shrink  the, I presume, 300Gb partition). 

I have about 200GB free space on the storage drive.
Also, I have ~100GB of important files/music on this drive.
Should I just leave all of my important things on, and make a 125GB partition for Ubuntu? (125GB because I want some free space on this drive)


> **Bucky Ball said:**
> 
Shrinking it in Windows would be the best option, though. Simple and Win already there.
Sorry, what do you mean by this?

---

### Post by Bucky Ball on 2012-06-19
> **Nanur said:**
> So by "grab 'em" you mean 'copy-paste' after I re-install?

Yes. Just don't erase your Wubi install until all this is done. I think you can install from Wubi also but it can be problematic so stick to making the stick.

> **Nanur said:**
> I have about 200GB free space on the storage drive.
Also, I have ~100GB of important files/music on this drive.
Should I just leave all of my important things on, and make a 125GB partition for Ubuntu? (125GB because I want some free space on this drive)

As you wish. Consider this: Ubuntu itself will install onto 10-15Gb (I've never installed onto bigger than 15). That is just the operating system and programs in / (root). You will then need a /home partition (where all your personal stuff goes) and /swap. I might suggest something like this:

/ = 15-20Gb
/home = 100Gb
/swap = 2Gb is fine

/home will be a directory in / if you don't create a separate partition for it. Having /home partition means you can reinstall the OS without losing your data as /home is not touched. 

> **Nanur said:**
> Sorry, what do you mean by this?

There is a partitioning tool in Win7. Shrink the partition on the other drive with it (leaving the free space for Ubuntu at the beginning of the disk).

PS: When you have your 125Gb free space you could make one extended partition with it during the Ubuntu install and put Ubuntu on logical partitions in that. There is a limit of four primary partitions a HD and if you want to put another partition on there you will be in trouble after three more for Ubuntu. You can put as many logical partitions in the extended partition. You'd end up with two primaries and one extended. ;)

---

### Post by Nanur on 2012-06-19
So, when all said and done, I will three Ubuntu partitions on my drive, and one partition for my important files. Correct?
Also, is it pretty straight forward on how to create these three separate partitions?

---

### Post by Bucky Ball on 2012-06-19
Yes. /, /home, and /swap are all defaults you can select in there. Make the extended partition for them to go in using Gparted and the free space you created from shrinking your existing 300Gb partition. This can be done prior to or during install (Gparted is what is used for partitioning during the install also).

This will help with the rest:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

From here:

[http://au.altavista.com/search;_ylt=A7exU8PwO.FPAGwAY6AK5gt.?p=ubuntu%20dual%20boot%20install&fr=altavista&fr2=sfp]("http://au.altavista.com/search;_ylt=A7exU8PwO.FPAGwAY6AK5gt.?p=ubuntu%20dual%20boot%20install&fr=altavista&fr2=sfp")

When you get to the partitioning section of the install choose 'Something Else'. This will allow you to create your own partitions and select which drive/partition to install to (the other methods on offer are automatic and you don't have much say as to sizes of/or specific partitions).

Which release of Ubuntu are you intending to install, incidentally?

---

### Post by HiImTye on 2012-06-19
the boot disk creator doesnt make an ext partition on the drive, it makes a FAT32 partition and then if you choose to use persistence it creates a persistence file and then formats that as an EXT type drive so the screenshot of your pendrive, if it has Ubuntu on it, is not indicative of a WUBI install, but rather, a regular Ubuntu boot disk

---

### Post by Nanur on 2012-06-19
> **Bucky Ball said:**
> 
Which release of Ubuntu are you intending to install, incidentally?

installed* haha. I installed Ubuntu 12.04 Precise.
Also, I set up those partitions you recommended and everything is working beautifully, and all my partitions are as I intended.
Thanks again man!
I can boot into Windows or Ubuntu, even know they are on separate disks. When I start my computer up it directly goes into the Ubuntu menu, and at the bottom is the option "Windows 7 loader" and when I enter that it changes into the Windows disk, and boots normally.

---

### Post by Bucky Ball on 2012-06-19
Excellent news! Enjoy the system and the learning curve. My pleasure and glad I could help. ;)

If your problem is solved please mark it solved from 'Thread Tools' at top right of this page to help others. 

Good luck with it all and post a new thread with any other questions/probs.

PS: You should now be able to access the Wubi directory on the Win partition when booted into Ubuntu and drag/drop those files into directories on your new /home partition.

---

### Post by Nanur on 2012-06-20
Thanks man! And I'm sure I'll have another issue/question sometime soon here :D

---

