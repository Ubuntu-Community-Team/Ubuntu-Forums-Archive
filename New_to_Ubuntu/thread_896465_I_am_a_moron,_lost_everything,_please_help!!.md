---
title: "I am a moron, lost everything, please help!!"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by LostAndDelerious on 2008-08-21
Hi all,
i planned to install ubuntu on a seperate partition of my hardrive but when asked the way the instaler would work with partitions i choose AUTOMATIC. Having realised what I had done I shut down the installer in action (doh!). Restarting produced a lovely grub error(22). I ran testdisk and found and rewrote the old partition table and so my hd looked normal again but the ntfs windows partition is totally wiped. This is the only bootable drive on the particular computer. The other partition is fine but  contains only data with no os. There is data on the other partition that I planned to write to but I could back that up externally and install an os on it(Had the data backed up on the windows partition..ironic..). At the mo I'm afraid of breaking anything else..

I see that there are a fair few recovery softwares out there but anyone know if any particular one is any good, if they would boot from a CD with no OS and if there are any decent tutorials to help(or nice people who would talk me through it). I'm terrified of touching anything in case I write over what's there already!!

Has this happened to anyone else or an I the only one stupid enough to do something like this?

Thanks 
T

---

### Post by unutbu on 2008-08-21
LostAndDelerious, take a deep breath. You are not alone. I did something similar once.

Am I correct in understanding that your data is safe and it is only your Windows partition that is broken?

And ultimately, is it a dual boot (windows+ubuntu) system that you want?

If that is the case, perhaps the best first step is to boot from the Windows CD and reinstall Windows. Use the BIOS menu to select "boot from CD". When you boot up the computer, usually a function key like F2 will take you to the BIOS menu. Some computers also have a "Boot from device" menu where you can select to boot from CD. On my computer the "Boot from device" menu is reached by pressing F12, but yours may be different.

As long as you can boot from a CD, you can install an operating system.

---

### Post by LostAndDelerious on 2008-08-21
Alas, no. The data that was stored in the Windows partition seems to be gone. And yes I want to have a dual boot system at the end of this (or even a system that runs). Installing windows will wipe it completely methinks. If I had that data I wouldn't mind reinstallig there's just a good few months of work stored there :( There was other seperated data on the other partition. But since I was going to install to that partition I figured that was the only data I had to back up.. Thanks a million for getting back to me :)

---

### Post by cooljeff3000 on 2008-08-21
I don't think installing windows will wipe your hd. But instead of risking it you should try putting a very small Linux distro onto a disk, and using that to transfer your files to a portable hd or even a thumb drive. I would recommend puppy linux.

---

### Post by eddVRS on 2008-08-21
You might be able to recover your data from the HDD.

I did a similar thing to an external HDD- completely borked it.

If you cannot boot from the disk at all get your disk put into another PC and run a recovery app (I used RStudio Recovery) you can recover most of the data.

---

### Post by Abu_Dayya on 2008-08-21
Maybe you can try this:
take the hard disk out and pulg it externally to another computer, see if you can access the disk and copy your files to that computer. If that works, you can then install windows and ubuntu on the original computer and copy your files later.

hope that helps

---

### Post by LostAndDelerious on 2008-08-21
My problem is that I cant get my files! I stuck in gparted and booted from CD and had a look at the hd. I can see 3 partitions. two of these are fine and I can see that they contain data but the third (my windows partition, the one i'm worried about) looks completely empty, like there is nothing in it.

Are you saying i should install windows on a seperate partition or this one that I am trying to recover? Sorry, for being an idiot, just a bit confused (and probably not being very clear, sorry).. Surely installing over this will format the partition again!? Which is the last thing I need! So sad :(

---

### Post by eddVRS on 2008-08-21
I would recomend putting your drive into another PC (if available) and run RStudio from windows on that PC.

What RSTudio does is read each individual sector on the disk and pieces together all the files on there as more often than not, it is just the Table of Contents that has been damaged, and not the actual data (does that make sense?)

I woudln't do anything to the partition you are trying to recover, as it could overwrite anything that's there.

Feel free to PM me if you want further help with this.

---

### Post by unutbu on 2008-08-21
LostAndDelerious, the data -- if it can be recovered from the Windows partition -- will be there in an hour, in a day, and even in a month. Whenever you are doing recovery work, it is best to be in a very calm mood. It's okay to take a break and walk away and do something different for a while. We'll be here when you get back.

That said, here are some thoughts:

[list]
[*] Here are instruction on how to mount partitions from the LiveCD: [http://ubuntuforums.org/showpost.php?p=5586420&postcount=3](http://ubuntuforums.org/showpost.php?p=5586420&postcount=3). You can then take a look to see what is automatically recoverable. If you have a USB key or USB external drive, you could transfer stuff there.
[*] Try TestDisk again. I'm not familiar with all its ins-and-outs, but it may be able to find an older file allocation table (FAT) which may at least partially restore your Windows partition.
[*] If you've searched through the menu options that TestDisk offers and there is no success, then you can try PhotoRec. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec). This is completely non-destructive. It will search the partition for anything it recognizes as a file and save it in another location. If you have a USB external drive or a different partition on your current drive that is big enough, you could save what PhotoRec finds there.
(Even though it is called PhotoRec, it can recover many types of files -- not just pictures).
[*] If you are really serious about recovering as much data as possible, then the first step is to clone the partition bit-for-bit so you can do your data recovery work on a backup copy of the partition, without altering the original. To do this, you'll need a computer from which to burn a Partimage CD: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). You'll also need a free partition which is the same size as your Windows partition. A USB external drive could also be used. 
[/list]

Good luck.

---

### Post by LostAndDelerious on 2008-08-21
hey eddVRS, took so long writing the last reply I missed yours :P

Gonna try that now :) Is RStudio Recovery easy enough to use? (ie idiot proof for someone like me :P)

I think there shouldn't be a prob booting from CD. Will I have to recover each file individually and then reinstall everything? Is everything in folders in the same location as they were originally or are the sporadically distributed all over the drive? Scared :(

bah!

---

### Post by eddVRS on 2008-08-21
> **unutbu said:**
> LostAndDelerious, the data -- if it can be recovered from the Windows partition -- will be there in an hour, in a day, and even in a month. When ever you are doing recovery work, it is best to be in a very calm mood. It's okay to take a break and walk away and do something different for a while. We'll be here when you get back.

<SNIP>

[*] If you are really serious about recovering as much data as possible, then the first step is to clone the partition bit-for-bit so you can do your data recovery work on a backup copy of the partition, without altering the original. To do this, you'll need a computer from which to burn a Partimage CD: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). You'll also need a free partition which is the same size as your Windows partition. A USB external drive could also be used. 
[/list]

Two very good points to consider

---

### Post by LostAndDelerious on 2008-08-21
oh and hey unutbu,

Thanks for the advice :) I will indeed walk away, gonna have some lunch and try all the good advice given here then in a calm and collected manner. Cheers, and I will probably talk to you all later.

Thanks again!

T x :)

---

### Post by LostAndDelerious on 2008-08-22
here goes nothing.. Wish me luck!

---

### Post by fmartinez on 2008-08-22
Why don't you try this: 
1: boot the live cd
2: see if you can mount the windows partition.
3. transfer your data to an external source

This may have already been asked but have you tried running the Win CD and logged into the recovery console. All that may have happened is that the MBR got written over by grub. 
All you may have to do is go into the recovery console provided as an option on the install CD and type the 
```
fix mbr
```
command and should the MBR.

---

### Post by Loaded.len on 2008-08-22
I'm going to run down my very recent experience in hopes that it will help you.  My wife freaked when her system refused to boot. It would try, then stall and fallback to busybox. Turns out that the boot sector is fried...So here's what I did.


[LIST]
[*]Booted from the 8.04 live-desktop cd.
[*]enabled all the repositories in System->Administration->Software Sources.
[*]opened a terminal...
[/LIST]
```
sudo apt-get update
sudo apt-get install nfs-common ddrescue
```I have a FreeNAS box setup, therefor the need for nfs...the drive in question is a 20gb, so I had enough room to make a complete image.  If you don't have such a resource, you could put another drive in. - make sure you do fdisk -l to make sure you know which is which before you start making an image.

[LIST]
[*]After that, I created a mount point for my NAS drive and mounted the share...
[/LIST]
```
sudo mkdir ~/recovery && mount -t nfs 192.168.0.250:/mnt/hegmata1 ~/recovery 
```192.168.0.250 is the IP of my FreeNAS box.

[LIST]
[*]Next I made an image of the failed drive.
[/LIST]
```
dd_rescue /dev/sda ~/recovery/20gb.img
```(that took a while, maybe because of network congestion, or because I was using the LiveCD which tends to slow things down a bit)

I like dd_rescue because it gives a status reports as it's bit copying... dd does it blind and will usually fail in some way if it comes accross bad sectors. dd_rescue at least tried to chug through it.

When I replaced the failed drive, I reinstalled Ubuntu on it, did the updates, installed my usual stuff, and connected back up to my NAS share. (mounted in ~/recovery)

The image cannot be mounted without a little bit of prior knowledge of the partition info, so I did
```
sudo fdisk -ul ~/recovery/20gb.img

You must set cylinders.
You can do this from the extra functions menu.

Disk 20gb.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b032c

      Device Boot      Start         End      Blocks   Id  System
20gb.img1   *          63    37383254    18691596   83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(2326, 254, 63)
20gb.img2        37383255    39102209      859477+   5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(2327, 0, 1)
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(2433, 254, 63)
20gb.img5        37383318    39102209      859446   82  Linux swap / Solaris

```Start of the partition I want to mount is 63 and the units are 512 so I mounted the partition like this..
```
sudo mkdir ~/20gbmount && mount -o loop,offset=$((63*512)) ~/recovery/20gb.img ~/20gbmount
```Then all my data appeared in the ~/20gbmount dir and I just pulled what I wanted into my wife's new home dir.  

If your data is corrupted, then you might do something similar up the part where you mount the image... instead you could install testdisk and try..

```
sudo photorec IMAGENAME
```I hope that helps you.  It saved my wife's data and subsequently my ability to live peacefully. :)

---

### Post by eddVRS on 2008-08-22
> **Loaded.len said:**
>   It saved my wife's data and subsequently my ability to live peacefully. :)

:lolflag:

---

