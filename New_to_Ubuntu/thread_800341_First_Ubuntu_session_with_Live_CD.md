---
title: "First Ubuntu session with Live CD"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by jukingeo on 2008-05-19
Hello all,

Ok, tonight I took the dive and booted up the Live CD for Ubuntu.  To my amazement quite a few things were working right away for one the web browser went right to this website, I didn't have to set up my ethernet card or anything.  Now that is a big WOW!

Ok, email through Evolution...no big deal Evolution seems to operate A LOT like Outlook so I didn't have a problem to find my way around.  I DID have to set up my POP server address for connection, but I did get my email and I even sent email.

Next thing...printer.  I saw the printers tab under system preferences.  It didn't see my printer right away, but I just clicked on the add new printer tab and it detected my printer.  GREAT!

Ok, so now for the not so good news:

The first thing I noticed that I can't see my hard drives.  All my CD-Roms and the floppy shows up on the list, but none of my drive partitions.  Under the Administration Device Manager I DO see the partitions there, but not on the drives list.

The next thing is that the time is now 7:30pm, but the clock on Ubuntu says 11:30pm  Worse I can't change it without a "Bug Report" screen from popping up.  I am assuming this problem is due to the fact that I am running a live CD and not from the hard drive.  I find it a bit weird that I cannot change the time because now all my emails will probably be off.

The next thing is a biggie.  No sound.  I have two sound devices on my computer, one is the Alesis Firewire IO|26 audio interface and of course my resident sound card, the Sound Blaster X-Fi.

I did do some early reading and found out that Ubuntu will detect quite a few versions of Sound Blaster including the Sound Blaster 16, the Sound Blaster Live, and even Audigy.  However, I didn't see the X-Fi on the list.  So does that mean I am out of luck for sound?

What about Firewire and my Alesis interface?  That is even more important to me because I use that for audio recording.

I am going to chalk up many issues to the fact that I am running the Live CD and not yet off the hard drive.  But I definitely would like to get the above problems straitened out before hand (unless of course I have to install Ubuntu on my machine at that point.

I just find it weird that I cannot change the clock, or see my hard drives.  I guess the sound could be a given because I didn't see the X-Fi supported on the Ubuntu sound card list.

Hopefully there is a fix.

Oh! I also don't have video, but I was trying to view a video on You Tube and it was asking to install a Java applet.  My guess that wouldn't work with the Live CD.

Ok. So that is pretty much as far as I got with Ubuntu tonight.

Geo

---

### Post by EXCiD3 on 2008-05-19
The partitions need to be mounted on a LiveCD and arent mounted automatically.

Note sure about the time problem, should resolve itself after you install and/or update.

There is support for the x-fi and you can find a tutorial for installing the beta drivers here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656)

Firewire should work out of the box. What is Alesis? I've never heard of it before, haha!

The LiveCD is almost exactly what you will have from a installation, provided there will be a few differences, such as updates to download and your hard drives will be mounted.

Youtube has had some issues recently because of a change in how the audio is handled with flash video. It was causing it to crash constantly but should be fixed with updates.

Wish you luck!

---

### Post by jukingeo on 2008-05-19
> **EXCiD3 said:**
> The partitions need to be mounted on a LiveCD and arent mounted automatically.

Note sure about the time problem, should resolve itself after you install and/or update.

There is support for the x-fi and you can find a tutorial for installing the beta drivers here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656)

Firewire should work out of the box. What is Alesis? I've never heard of it before, haha!

Wish you luck!

Hello,

The clock problem DID resolve itself and when I went into Ubuntu again tonight (I am in it now), it was fine.

Ok, the hard drive mounting thing is driving me nuts.  I don't know what to do.  I searched here and I did get as far as opening up the terminal program and typing this line in: sudo fdisk -1.  From there I can see both my hard drives (I have two on board) and my partitions.

There were a couple of other "sudo" lines I tried to mount the disk, but apparently they were not successful because I still cannot see any of my partitions.  So I don't know what I am doing wrong.

I have not investigated the sound card issue.  ...Too tired for tonight.

Alesis is a company that makes audio equipment for computers.  The particular device I have is very much like a sound card on steroids.  It is a box that sits on my desktop it has 8 mic/line inputs, several outputs and a few knobs on it.  Kind of like a mixing console except it also connects to the computer via a firewire connection (USB is too slow for this item).

So that is where I am for tonight.

I am going to research what I have to do with the sound card tomorrow, but I am definitely going to need some assistance with the hard drive mounting thing.  The Terminal program is a pretty scary thing and I don't want to type the wrong thing in there and end up wiping my Windows hard drive...if you catch my drift.

Thanx,

Geo

---

### Post by EXCiD3 on 2008-05-20
Dont feel overwhelmed. Yes there is a lot to learn, but then again, there is Ubuntu Forums to save your day! ;) If you ever need some quick help, just contact me on IM. I'd be glad to help!

As for your drive mounting issues. You can have them automounted when you boot. It really isnt as hard as it sounds. ;) Just post the output of sudo fdisk -l and i can walk you through the rest.

The Alesis device sounds pretty sweet! I have a small song collection (10,000 or so songs) and am somewhat of an audiophile. :) I cant wait until i can get a desktop with an x-fi because they sound so good. I don't do any recording so i won't have need for anything like the Alesis thing, but it sounds pretty cool. What exact device do you have? I've found a couple different topics and all say that the firewire drivers arent usable yet. :(

You shouldn't worry too much about your windows partition. I've got vista and ubuntu dual boot and haven't had a problem yet. I transfer files between them almost every day and nothing has gone wrong.

EXCiD3

---

### Post by indiecast on 2008-05-20
why would anyone use the live cd for anything more than system utilities and installing ubuntu?

just install it

if you dont like it you can take it off. or leave it there and come back to it some other time

---

### Post by archer6 on 2008-05-20
> **EXCiD3 said:**
> 
You shouldn't worry too much about your windows partition. I've got vista and ubuntu dual boot and haven't had a problem yet. I transfer files between them almost every day and nothing has gone wrong.

After installing Ubuntu 7.10 on an older ThinkPad R51e and working with it for a short period of time (very short). I'm really impressed. My question is I would like to install either 7.10 or 8.04 on my main laptop (as dual boot with XP) which is a ThinkPad T60. It has a 100GB hard drive so I have plenty of space. 

Here is my concern. The ThinkPad has a hidden partition that has an image of XP Pro called Rescue and Recovery. So if your system crashes, instead of restore disks, you may press F11 during boot up and it gives you the option of wiping the drive and restoring it the out of box as new condition. Then you simply reload your software apps, and your data and you are all set as good as new. 

How to I install Ubuntu as dual boot without wiping out that rescue partition? 

And which version 7.10 or 8.04 do you suggest. 7.10 is working perfectly on my R51 thus I'm rather inclined to also put it on the T60 as I can always upgrade later. Since the T60 is mission critical that I make my living with daily, I want to do this as carefully as possible. Having a dual boot config with XP Pro which is already on the T60 and 7.10 Ubuntu would be the ultimate for me. Especially since I travel so much and want to carry just one laptop. 

Thanks for your help.

---

### Post by EXCiD3 on 2008-05-20
> **archer6 said:**
> After installing Ubuntu 7.10 on an older ThinkPad R51e and working with it for a short period of time (very short). I'm really impressed. My question is I would like to install either 7.10 or 8.04 on my main laptop (as dual boot with XP) which is a ThinkPad T60. It has a 100GB hard drive so I have plenty of space. 

Here is my concern. The ThinkPad has a hidden partition that has an image of XP Pro called Rescue and Recovery. So if your system crashes, instead of restore disks, you may press F11 during boot up and it gives you the option of wiping the drive and restoring it the out of box as new condition. Then you simply reload your software apps, and your data and you are all set as good as new. 

How to I install Ubuntu as dual boot without wiping out that rescue partition? 

And which version 7.10 or 8.04 do you suggest. 7.10 is working perfectly on my R51 thus I'm rather inclined to also put it on the T60 as I can always upgrade later. Since the T60 is mission critical that I make my living with daily, I want to do this as carefully as possible. Having a dual boot config with XP Pro which is already on the T60 and 7.10 Ubuntu would be the ultimate for me. Especially since I travel so much and want to carry just one laptop. 

Thanks for your help.

I would recommend using 8.04. You can resize your windows partition (defragment first to free up a chunk of free space) and then install Ubuntu in the free space. You don't have to worry about erasing any partitions when you resize and both the regular XP and the recovery XP partition will show up as options when you boot. I had this a while back but decided to scrap the recovery partition and make use of the wasted space since i already have recovery discs and actual windows XP cd's anyways.

---

### Post by archer6 on 2008-05-20
> **EXCiD3 said:**
> I would recommend using 8.04. You can resize your windows partition (defragment first to free up a chunk of free space) and then install Ubuntu in the free space. You don't have to worry about erasing any partitions when you resize and both the regular XP and the recovery XP partition will show up as options when you boot. I had this a while back but decided to scrap the recovery partition and make use of the wasted space since i already have recovery discs and actual windows XP cd's anyways.

When you talk about resize, is that using the utility that comes on  8.04?
By the way what's the fastest way for me to obtain a CD with 8.04, my burner is not working so I cannot burn an ISO, I must find a disk. Thanks

---

### Post by EXCiD3 on 2008-05-20
Every time you install Ubuntu you get to the partition setup screen. You can choose to have Ubuntu resize a drive to create free space to install Ubuntu in. You can have it automatically do it for you or you can manually setup your drive partitions in the installer on the LiveCD or the alternate cd. Everything you need is built in to ANY version of ubuntu, not just 8.04 so you could use the older version if you like. Seeing as you have had good luck with a previous version this newer one should work fine, if not you can wipe the 8.04 install and install 7.10 to where it used to be.

---

### Post by Paqman on 2008-05-20
The easiest way to mount partitions when you're in the LiveCD is to right click on a panel, add a "disk mounter" and just click on whatever partitions you want to mount/unmount.

---

### Post by EXCiD3 on 2008-05-20
> **Paqman said:**
> The easiest way to mount partitions when you're in the LiveCD is to right click on a panel, add a "disk mounter" and just click on whatever partitions you want to mount/unmount.

True, but i have a feeling he wants them automounted on each boot. This is much easier, but it also becomes a pain to have to configure each time.

---

### Post by EXCiD3 on 2008-05-20
> **archer6 said:**
> When you talk about resize, is that using the utility that comes on  8.04?
By the way what's the fastest way for me to obtain a CD with 8.04, my burner is not working so I cannot burn an ISO, I must find a disk. Thanks


If you dont have access to an 8.04 cd you can order one from [http://www.ubuntu.com](http://www.ubuntu.com) but they take like 4 weeks, you could order one: [http://www.linuxcd.org/?ref=distrowatch](http://www.linuxcd.org/?ref=distrowatch) or you could try to get someone to download and burn it for you ;)

---

### Post by Paqman on 2008-05-20
> **EXCiD3 said:**
> True, but i have a feeling he wants them automounted on each boot. This is much easier, but it also becomes a pain to have to configure each time.

For sure, but at the moment he's only using the LiveCD.

Re: Dead Cd burner, you could always try Wubi. Grab the downloader from their site and it'll download the correct Ubuntu disk image for installation. No actual disk required.

---

### Post by EXCiD3 on 2008-05-20
> **Paqman said:**
> For sure, but at the moment he's only using the LiveCD.

Re: Dead Cd burner, you could always try Wubi. Grab the downloader from their site and it'll download the correct Ubuntu disk image for installation. No actual disk required.

lol, looks like im getting ahead of myself. and yes wubi is a great idea plus you dont have to partition with it! and you can easily uninstall it from windows. I'm not sure if that would disable the F11 to boot into the recovery partition though. do you know how wubi installs grub? ive never used it before and always forget about mentioning it.

---

### Post by archer6 on 2008-05-20
When I decided to try Ubuntu, I purchased the live CD (ver 7.10) from Amazon. Not because I wanted to run it only from the CD, but because I always like to have my software on Disk. I used that disk to install it on my ThinkPad R51 and chose the option to use the entire hd thereby wiping both XP & the recovery partition. Therefore I have not re sized a disk before and wonder if this time when setting it up as dual boot if I will actually "see" the recovery partition so as to avoid writing over it?  

Ideally I would like to have about half of it for XP & the other half minus the rescue partition space, for Ubuntu.

Since this is my business machine & I'm on the road constantly, keeping the rescue partition for XP is important. The ability to have both XP & Ubuntu in a dual boot config would be ideal.

---

### Post by jukingeo on 2008-05-20
> **EXCiD3 said:**
> Dont feel overwhelmed. Yes there is a lot to learn, but then again, there is Ubuntu Forums to save your day! ;) If you ever need some quick help, just contact me on IM. I'd be glad to help!

As for your drive mounting issues. You can have them automounted when you boot. It really isnt as hard as it sounds. ;) Just post the output of sudo fdisk -l and i can walk you through the rest.

The Alesis device sounds pretty sweet! I have a small song collection (10,000 or so songs) and am somewhat of an audiophile. :) I cant wait until i can get a desktop with an x-fi because they sound so good. I don't do any recording so i won't have need for anything like the Alesis thing, but it sounds pretty cool. What exact device do you have? I've found a couple different topics and all say that the firewire drivers arent usable yet. :(

You shouldn't worry too much about your windows partition. I've got vista and ubuntu dual boot and haven't had a problem yet. I transfer files between them almost every day and nothing has gone wrong.

EXCiD3

I thought the drive mounting thing was something that was pretty trivial and easy to fix, but I am finding it isn't so easy and to me that did seem unexpected.  I figured like with Windows, the drives would all just pop up.  Yeah, as I said I did get as far as 'venturing' into the Terminal and tried the "sudo fdisk -l" command and I did see my drive list.  However, posting that list will have too wait until this evening, as I am at work right now.

The Alesis unit is the IO|26 Firewire audio interface/mixer. 

Here is the beast:

[http://www.musiciansfriend.com/product/Alesis-iO26-Portable-26-Input-FireWire-Audio-Interface?sku=246031](http://www.musiciansfriend.com/product/Alesis-iO26-Portable-26-Input-FireWire-Audio-Interface?sku=246031)

The Firewire light doesn't come on on the unit.  So I know it isn't connecting to Ubuntu.  As soon as I go back into Windows, the Firewire light comes on.

Prior to my buying the Alesis unit I bought a Sound Blaster X-Fi, which at the time it came out it was a VERY expensive sound card.  This card pretty much replaced the Live and Audigy cards.  I did hear there is a Beta driver for the X-Fi for Linux, but I have not tried it yet.

Well, I am a bit worried about poking around in the Terminal because I don't want to inadvertently erase something.

I am slowly getting ready to go with a dual boot system.  I am currently moving files around and freeing up some of my partitions on my second hard drive.  Once I do that I should have about 10g to 12g to put a full Ubuntu install on.

Anyway, I have to run.

Thanx for the info.  I will come back tonight withe the fdisk list.

Geo

---

### Post by Paqman on 2008-05-20
> **EXCiD3 said:**
> lol, looks like im getting ahead of myself. and yes wubi is a great idea plus you dont have to partition with it! and you can easily uninstall it from windows. I'm not sure if that would disable the F11 to boot into the recovery partition though. do you know how wubi installs grub? ive never used it before and always forget about mentioning it.

Wubi actually uses the Windows bootloader.

---

### Post by archer6 on 2008-05-20
> **Paqman said:**
> Wubi actually uses the Windows bootloader.

That's very interesting. I'm so new to Linux (weeks) that I'm soaking it up like a sponge. Very interesting. I'm really happy to have found this forum as everyone here is very helpful. 

Cheers!

---

### Post by EXCiD3 on 2008-05-20
> **archer6 said:**
> When I decided to try Ubuntu, I purchased the live CD (ver 7.10) from Amazon. Not because I wanted to run it only from the CD, but because I always like to have my software on Disk. I used that disk to install it on my ThinkPad R51 and chose the option to use the entire hd thereby wiping both XP & the recovery partition. Therefore I have not re sized a disk before and wonder if this time when setting it up as dual boot if I will actually "see" the recovery partition so as to avoid writing over it?  

Ideally I would like to have about half of it for XP & the other half minus the rescue partition space, for Ubuntu.

Since this is my business machine & I'm on the road constantly, keeping the rescue partition for XP is important. The ability to have both XP & Ubuntu in a dual boot config would be ideal.

If you want to be super sure that you are not going to erase anything, choose Manual Partitioning. You will be able to see each partition, their format, space used and then you can be sure that you dont erase anything accidentally. You can also use manual partitioning to have it mount your windows drive to /media/windows or something like that so you can access it right away from Ubuntu. Mounting extra partitions like this also automatically configures the fstab so you don't have to go through the trouble of adding them later to automount. :)

> **jukingeo said:**
> I thought the drive mounting thing was something that was pretty trivial and easy to fix, but I am finding it isn't so easy and to me that did seem unexpected. I figured like with Windows, the drives would all just pop up. Yeah, as I said I did get as far as 'venturing' into the Terminal and tried the "sudo fdisk -l" command and I did see my drive list. However, posting that list will have too wait until this evening, as I am at work right now.

The Alesis unit is the IO|26 Firewire audio interface/mixer. 

Here is the beast:

[http://www.musiciansfriend.com/product/Alesis-iO26-Portable-26-Input-FireWire-Audio-Interface?sku=246031](http://www.musiciansfriend.com/product/Alesis-iO26-Portable-26-Input-FireWire-Audio-Interface?sku=246031)

The Firewire light doesn't come on on the unit. So I know it isn't connecting to Ubuntu. As soon as I go back into Windows, the Firewire light comes on.

Prior to my buying the Alesis unit I bought a Sound Blaster X-Fi, which at the time it came out it was a VERY expensive sound card. This card pretty much replaced the Live and Audigy cards. I did hear there is a Beta driver for the X-Fi for Linux, but I have not tried it yet.

Well, I am a bit worried about poking around in the Terminal because I don't want to inadvertently erase something.

I am slowly getting ready to go with a dual boot system. I am currently moving files around and freeing up some of my partitions on my second hard drive. Once I do that I should have about 10g to 12g to put a full Ubuntu install on.

Anyway, I have to run.

Thanx for the info.  I will come back tonight withe the fdisk list.

Geo

Dont be worried about the terminal. Just make sure you know what the commands do before running them. Only commands that require sudo (aka root privileges) can do harm to your system, but you should just make sure someone explains what each command does before you use them just to be on the safe side. Be wary of the rm command as it is used to delete files and folders. Otherwise I can safely say, terminal is your friend. After all my life using Windows and being accustomed to using graphical tools for everything, i can say that i actually prefer using terminal instead. It gives you so much more feedback on what is going on and can help out so much trying to solve problems. 10gb will be plenty for an install of Ubuntu, mine currently is only 4gb and ive got xubuntu on my dad's asus eee pc laptop with a 4gb hdd and its only using 2gb of space. :)


> **Paqman said:**
> Wubi actually uses the Windows bootloader.
I figured as much, i just wondered what happened between the windows bootloader and booting ubuntu. This helps explain a little more: [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

---

### Post by Exsecrabilus on 2008-05-20
> **jukingeo said:**
> The next thing is that the time is now 7:30pm, but the clock on Ubuntu says 11:30pm  Worse I can't change it without a "Bug Report" screen from popping up.  I am assuming this problem is due to the fact that I am running a live CD and not from the hard drive.  I find it a bit weird that I cannot change the time because now all my emails will probably be off.
Did you go **System** >> **Administration** >> **Time and Date**?

Maybe this is due to the Live CD being a Live CD, so you can't do certain stuff.

I'm pretty sure when you install it, it'll work just fine.

P.S. Try setting the **Configuration** to *Keep synchronized with Internet servers*.
That will keep you automatically in-time, unlike *Manual*, in which you have to set the time yourself.

---

### Post by archer6 on 2008-05-20
> **EXCiD3 said:**
> If you want to be super sure that you are not going to erase anything, choose Manual Partitioning. You will be able to see each partition, their format, space used and then you can be sure that you dont erase anything accidentally. You can also use manual partitioning to have it mount your windows drive to /media/windows or something like that so you can access it right away from Ubuntu. Mounting extra partitions like this also automatically configures the fstab so you don't have to go through the trouble of adding them later to automount. :)

Ok, this is beginning to make sense to me now, your time and patience is greatly appreciated. HeH! I just don't want to mess up my work computer even though I paid for it....:)
When you say to have it mount I understand that, to /media/windows or something like that, am I to understand that I will be naming the partition? and If so what is the proper conventions? "so you can access it right away from Ubuntu" meaning that it will recognize and boot up quicker?
Finally "so you don't hav to go through the trouble of adding them later to "automount"? please explain.

Cheers

---

### Post by EXCiD3 on 2008-05-20
> **archer6 said:**
> Ok, this is beginning to make sense to me now, your time and patience is greatly appreciated. HeH! I just don't want to mess up my work computer even though I paid for it....:)
When you say to have it mount I understand that, to /media/windows or something like that, am I to understand that I will be naming the partition? and If so what is the proper conventions? "so you can access it right away from Ubuntu" meaning that it will recognize and boot up quicker?
Finally "so you don't hav to go through the trouble of adding them later to "automount"? please explain.

Cheers

In linux you don't really use drive names. You mount them to folders instead and the folder name is essential the drive name. You can name USB drives because they are automatically mounted for you with the folder name of the drive. Name of drives in linux really only matters with external drives. Here are a couple links on that:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[https://help.ubuntu.com/community/RenamingExt3Partitions](https://help.ubuntu.com/community/RenamingExt3Partitions)

What i meant by saying you can access it right away in ubuntu was that, by default you are not able to view or edit anything on the windows partitions. They are NOT mounted to any folder so you cant access them to transfer files between Ubuntu and that partition. When you set them to mount in the manual partition editor, they are automatically mounted every time ubuntu starts, instead of you having to manually mount them by hand. Automounting just means that ubuntu will mount the drive for you.

Here is a quick tutorial on what you would have to do manually to mount a partition, while setting it up to automatically mount (during manual partitioning) would take care of all this for you: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jukingeo on 2008-05-20
> **EXCiD3 said:**
> lp!

As for your drive mounting issues. You can have them automounted when you boot. It really isnt as hard as it sounds. ;) Just post the output of sudo fdisk -l and i 

EXCiD3

Ok!  I am back and Ubuntu-fied.   I did the fdisk -l thing in the Terminal and these are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
16 heads, 63 sectors/track, 39703 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5080     2560288+   c  W95 FAT32 (LBA)
/dev/hdb2            5081       39703    17449992    f  W95 Ext'd (LBA)
/dev/hdb5            5081        9144     2048224+   b  W95 FAT32
/dev/hdb6            9145       13208     2048224+   b  W95 FAT32
/dev/hdb7           13209       17272     2048224+   b  W95 FAT32
/dev/hdb8           17273       21336     2048224+   b  W95 FAT32
/dev/hdb9           21337       29463     4095976+   b  W95 FAT32
/dev/hdb10          29464       39703     5160928+   b  W95 FAT32
ubuntu@ubuntu:~$ 

Like I said, this is how far I got. Now I know it does sound stupid that I have so many partitions on one drive.  This second drive used to be a main drive on an older computer.  Naturally I moved it to this computer because it has important data on it.  Much of higher partitions I am clearing off right now and making room for Ubuntu.

So now how do I go about mounting these drives AND then how to I find them using the file browser?

I would be extremely happy if I can get this going tonight, because then I can work on my sound card issues.

Thanx in advance!

Geo

---

### Post by jukingeo on 2008-05-20
> **Paqman said:**
> The easiest way to mount partitions when you're in the LiveCD is to right click on a panel, add a "disk mounter" and just click on whatever partitions you want to mount/unmount.


Yeah...I tried that.  All I see on the Disk Mounter is the floppy drive.  I don't know if it could be that my Live Disc has an older version of Ubuntu (6.10).  But I cannot see my hard drives anywhere except in the Device Manager or if I go into the terminal and type "sudo fdisk -l".  Then I can see them, but from there I don't know what to do.

I just posted the results a few mins ago here on my results of my fdisk command.

Geo

---

### Post by EXCiD3 on 2008-05-20
> **jukingeo said:**
> Ok!  I am back and Ubuntu-fied.   I did the fdisk -l thing in the Terminal and these are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
16 heads, 63 sectors/track, 39703 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5080     2560288+   c  W95 FAT32 (LBA)
/dev/hdb2            5081       39703    17449992    f  W95 Ext'd (LBA)
/dev/hdb5            5081        9144     2048224+   b  W95 FAT32
/dev/hdb6            9145       13208     2048224+   b  W95 FAT32
/dev/hdb7           13209       17272     2048224+   b  W95 FAT32
/dev/hdb8           17273       21336     2048224+   b  W95 FAT32
/dev/hdb9           21337       29463     4095976+   b  W95 FAT32
/dev/hdb10          29464       39703     5160928+   b  W95 FAT32
ubuntu@ubuntu:~$ 

Like I said, this is how far I got. Now I know it does sound stupid that I have so many partitions on one drive.  This second drive used to be a main drive on an older computer.  Naturally I moved it to this computer because it has important data on it.  Much of higher partitions I am clearing off right now and making room for Ubuntu.

So now how do I go about mounting these drives AND then how to I find them using the file browser?

I would be extremely happy if I can get this going tonight, because then I can work on my sound card issues.

Thanx in advance!

Geo

If you wish to mount the partitions manually via terminal follow this guide: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c)

Otherwise you can edit your fstab to have them mounted automatically by editing your /etc/fstab file.

Open fstab: ```
sudo gedit /etc/fstab
```

Add entries based on their partition format:

NTFS: ```
/dev/hda1       /media/hda1        ntfs    defaults        0       0
```
FAT32: ```
/dev/hda1       /media/hda1        vfat defaults        0       0
```

the first parameter "/dev/hda1" is the partition, the second "/media/hda1" is where it is going to be mounted to, the third is the format and the rest you can read about here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Just add these as appropriate for the partitions you wish to have mounted. Once mounted (as long as they are in /media) they should appear in the Places menu. You can also find them in My Computer > File System > media (aka /media).

If you want to read up more about mounting partitons automatically check this link out: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by jukingeo on 2008-05-20
> **EXCiD3 said:**
> 

Dont be worried about the terminal. Just make sure you know what the commands do before running them. Only commands that require sudo (aka root privileges) can do harm to your system, but you should just make sure someone explains what each command does before you use them just to be on the safe side. Be wary of the rm command as it is used to delete files and folders. Otherwise I can safely say, terminal is your friend. After all my life using Windows and being accustomed to using graphical tools for everything, i can say that i actually prefer using terminal instead. It gives you so much more feedback on what is going on and can help out so much trying to solve problems. 10gb will be plenty for an install of Ubuntu, mine currently is only 4gb and ive got xubuntu on my dad's asus eee pc laptop with a 4gb hdd and its only using 2gb of space. :)



The truth is I just started my first full Ubuntu session last night.  I didn't know I would be in the Terminal on the first night!  So the answer to is that I certainly DON'T know what I am doing in there. I only picked up a few things here and there such as the fdisk command and I DO know to stay away from the deadly letters "rm".  But I don't know what other dangers lurk in the Terminal.

I will say that I have been a Windows user since version 3.1.  In school we were still using Dos.  Back in Windows 3.1 and Win 95 most problems that I fixed had to go through Dos.  The Terminal in Ubuntu does remind me much of Dos.  So I really just have to get used to the commands and phrase structures.  But in a way it is kind of familiar site.

I was hesitant at first to use the Terminal, but I do have to reconfigure my partitions on my hard drives and supposedly Ubuntu's utility for that is much better than Windows partitioning tool.  So I would like to do it in Ubuntu.  However, as of now I cannot even access my drives in Ubuntu.  Through the terminal and Device Manager, I can "see" the drive partitions, but don't know what to do from there.

Geo

---

### Post by jukingeo on 2008-05-20
> **Exsecrabilus said:**
> Did you go **System** >> **Administration** >> **Time and Date**?

Maybe this is due to the Live CD being a Live CD, so you can't do certain stuff.

I'm pretty sure when you install it, it'll work just fine.

P.S. Try setting the **Configuration** to *Keep synchronized with Internet servers*.
That will keep you automatically in-time, unlike *Manual*, in which you have to set the time yourself.

The funniest thing was that when I went into Ubuntu again last night the clock was fine.  It is fine now as well.  I don't know, I think it burped the first time I started Ubuntu.  I couldn't even adjust the clock. I would get a "Report Bug" message on my screen.  It is fine now, I can get into the adjust screen fine.

I will keep the Internet Server sync in mind though.

Thanx,

Geo

---

### Post by EXCiD3 on 2008-05-20
> **jukingeo said:**
> The truth is I just started my first full Ubuntu session last night.  I didn't know I would be in the Terminal on the first night!  So the answer to is that I certainly DON'T know what I am doing in there. I only picked up a few things here and there such as the fdisk command and I DO know to stay away from the deadly letters "rm".  But I don't know what other dangers lurk in the Terminal.

I will say that I have been a Windows user since version 3.1.  In school we were still using Dos.  Back in Windows 3.1 and Win 95 most problems that I fixed had to go through Dos.  The Terminal in Ubuntu does remind me much of Dos.  So I really just have to get used to the commands and phrase structures.  But in a way it is kind of familiar site.

I was hesitant at first to use the Terminal, but I do have to reconfigure my partitions on my hard drives and supposedly Ubuntu's utility for that is much better than Windows partitioning tool.  So I would like to do it in Ubuntu.  However, as of now I cannot even access my drives in Ubuntu.  Through the terminal and Device Manager, I can "see" the drive partitions, but don't know what to do from there.

Geo

If you want to do partitioning you can install GParted. You can search Applications > Add/Remove Programs to install it. You cannot perform actions on drives that are mounted, so i would recommend mounting them manually at first then do your transferring of files, then once you have the partition setup settled down, then add them to your fstab. 

To get started learning terminal commands (also known as bash) here is an excellent cheat sheet to get you accustomed to some of the commands: [http://files.fosswire.com/wpu/2007/08/fwunixref.pdf](http://files.fosswire.com/wpu/2007/08/fwunixref.pdf)

And an excellent tutorial on Terminal can be found here on the forums: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by archer6 on 2008-05-20
> **EXCiD3 said:**
> In linux you don't really use drive names. You mount them to folders instead and the folder name is essential the drive name. 

EXCiD3, I would like to sincerely thank you for your generous support, and the links which I shall study, as I work on getting up to speed on this new OS I'm learning. It's people like you that are the cornerstone of encouragement, motivation and growth of the new people such as myself. 

This is a true role reversal for me, as I'm a moderator on two different special interest forums where I'm in your role as the experienced one, sharing and educating the new members. Something that I take great enjoyment in. 

I look forward to ramping up my knowledge so that I can begin to give back to this great forum and community. 

Cheers!
archer

---

### Post by jukingeo on 2008-05-20
> **EXCiD3 said:**
> If you wish to mount the partitions manually via terminal follow this guide: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c)

Otherwise you can edit your fstab to have them mounted automatically by editing your /etc/fstab file.

Open fstab: ```
sudo gedit /etc/fstab
```

Add entries based on their partition format:

NTFS: ```
/dev/hda1       /media/hda1        ntfs    defaults        0       0
```
FAT32: ```
/dev/hda1       /media/hda1        vfat defaults        0       0
```

the first parameter "/dev/hda1" is the partition, the second "/media/hda1" is where it is going to be mounted to, the third is the format and the rest you can read about here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Just add these as appropriate for the partitions you wish to have mounted. Once mounted (as long as they are in /media) they should appear in the Places menu. You can also find them in My Computer > File System > media (aka /media).

If you want to read up more about mounting partitons automatically check this link out: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I am still not getting it.

I did manage to open the fstab window but what do I do from there?  Do I enter the FAT32 code (I want to access those partitions) in the fstab window or do I do that in the Terminal?

I did try to do it both ways but I don't see anything come up in the Media folder.

Where exactly am I supposed to see the partitions?

Oh! The Disk Mounter is still only showing the floppy.  So something is wrong someplace or as I said above, I am just not getting it.

Lets try something simpler.  Could you post the whole code here in the forum that would allow me to mount every single partition on my system?  This way I can copy that into the Terminal and see what I get.  If again nothing happens then perhaps there is a bigger problem afoot.

Thanx,

Geo

---

### Post by jukingeo on 2008-05-21
> **EXCiD3 said:**
> If you wish to mount the partitions manually via terminal follow this guide: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c)

Otherwise you can edit your fstab to have them mounted automatically by editing your /etc/fstab file.

Open fstab: ```
sudo gedit /etc/fstab
```

Add entries based on their partition format:

NTFS: ```
/dev/hda1       /media/hda1        ntfs    defaults        0       0
```
FAT32: ```
/dev/hda1       /media/hda1        vfat defaults        0       0
```

the first parameter "/dev/hda1" is the partition, the second "/media/hda1" is where it is going to be mounted to, the third is the format and the rest you can read about here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Just add these as appropriate for the partitions you wish to have mounted. Once mounted (as long as they are in /media) they should appear in the Places menu. You can also find them in My Computer > File System > media (aka /media).

If you want to read up more about mounting partitons automatically check this link out: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

OK, thusfar here is the scoop,

I followed this to the tee and I still cannot mount the partition.  So something is wrong.  It is either me or the machine.

I finally found were the partition is supposed to show up.  I experimented with the mkdir command and saw that I could make a directory appear in the file system part of the COMPUTER tab.

I can even get to sudo gedit /etc/fstab and its window comes up.  However, adding the lines that follow to fstab seem to have NO effect and the partition STILL doesn't show up in the file browser

I think what I need is someone to walk me step by step on what to do after  getting fstab up.  While walking through to do checks through COMPUTER to see if what I am doing is correct.  For some reason it sounds simple, but yet I cannot get any partitions to show up in the File Browser for the life of me.  

So now, if I am following the directions properly and cannot mount my partitions I am wondering...could there be any problems with my computer in general? My computer is a Dell Dimension 4600.

Just for the record I am trying to mount the partitions on the "hdb" drive and not the "hda" drive.  Not that it matters, I actually tried to mount all the partitions and none show up in the File Browser and none show up on the Disk Mounter.

So I really don't know what to do now.  I am beginning to think that it isn't me and perhaps there is a problem with my Ubuntu Disc or even my computer.

---

### Post by EXCiD3 on 2008-05-21
> **archer6 said:**
> EXCiD3, I would like to sincerely thank you for your generous support, and the links which I shall study, as I work on getting up to speed on this new OS I'm learning. It's people like you that are the cornerstone of encouragement, motivation and growth of the new people such as myself. 

This is a true role reversal for me, as I'm a moderator on two different special interest forums where I'm in your role as the experienced one, sharing and educating the new members. Something that I take great enjoyment in. 

I look forward to ramping up my knowledge so that I can begin to give back to this great forum and community. 

Cheers!
archer

Hey, no problem, Linux is just something i love and enjoy...and i've only been using linux for a little over a year! :) I have found that the forums here are the most helpful by far when it comes to linux help. Everyone is friendly and helpful, i just figured i should give back to the community too!

---

### Post by avtolle on 2008-05-21
I think part of the problem may be with fstab changes is that the computer needs to be restarted for the changes to take effect. As I understand what you've posted, you have been running from the Live CD, which is the conservative approach you have taken to preserve your Windows install while working with Ubuntu. The changes made and steps you have taken are in RAM only, and a restart would, of course, cause them to be lost. Just a thought, based upon my impressions from what you have posted. Best of luck to you.

---

### Post by EXCiD3 on 2008-05-21
> **jukingeo said:**
> OK, thusfar here is the scoop,

I followed this to the tee and I still cannot mount the partition.  So something is wrong.  It is either me or the machine.

I finally found were the partition is supposed to show up.  I experimented with the mkdir command and saw that I could make a directory appear in the file system part of the COMPUTER tab.

I can even get to sudo gedit /etc/fstab and its window comes up.  However, adding the lines that follow to fstab seem to have NO effect and the partition STILL doesn't show up in the file browser

I think what I need is someone to walk me step by step on what to do after  getting fstab up.  While walking through to do checks through COMPUTER to see if what I am doing is correct.  For some reason it sounds simple, but yet I cannot get any partitions to show up in the File Browser for the life of me.  

So now, if I am following the directions properly and cannot mount my partitions I am wondering...could there be any problems with my computer in general? My computer is a Dell Dimension 4600.

Just for the record I am trying to mount the partitions on the "hdb" drive and not the "hda" drive.  Not that it matters, I actually tried to mount all the partitions and none show up in the File Browser and none show up on the Disk Mounter.

So I really don't know what to do now.  I am beginning to think that it isn't me and perhaps there is a problem with my Ubuntu Disc or even my computer.

If you are still trying to do this on the LiveCD modifying the fstab will do you no good. You have to restart for the fstab changes to take effect. You can however use the folders you created and use the manual "mount" tool to mount them. After you install you can use the fstab to have them mounted for you every time instead.

Since you already modified your fstab, you need to "refresh" ubuntu's partitions, by running ```
sudo mount -a
``` This will remount the partitions in the fstab and should give you access to your drives that you added to fstab.

Otherwise you can mount each partition one at a time, by using this command ```
sudo  mount  -t vfat /dev/hdb1 /media/hdb1
```This is just basically a slight variation of the fstab entries. the "-t vfat" just means to use the vfat format type when mounting. "-t ntfs" will mount ntfs drives.

If you want to unmount a partition, just use ```
sudo umount /media/hdb1
``` on the folder that a drive is mounted to.

---

### Post by jukingeo on 2008-05-21
Hello All,

I'M BAAAACK!!!

UPDATE:  Both news and version.

I dropped by Borders today and picked up a copy of Linux Magazine Pro.  Figured it can't hurt to do some extra reading.  Of course it came with a CD.  Low and behold it came with a version of Ubuntu on it (As well as a few other distributions such as Linux Mint 4.0, Dream Linux, Kubuntu, and Simply Mepis 7.0.  The disk live boots to Ubuntu.  Sadly it isn't version 8.04, but it is 7.10 (Gutsy) which is obviously better than 6.10.

First thing I noticed with 7.10 is that there were more options...especially for sound.  Sadly, because I have SB X-Fi...that still isn't working.

However, I went right away into the COMPUTER tab and guess what?  I CAN SEE MY DRIVES!!!  YAH BABY!!!

Clicking on them I guess 'mounts' them and puts them on the desktop and I can view the contents.

Well, I know this isn't the latest version, but at least now I can move around my computer fully in Ubuntu.

Now I know the reason for this is probably because of the newer version, but this time around with a Live CD I didn't even have to go in to Terminal.  So I am curious as to what major changes were made between 6.10 and 7.10.  Thusfar I AM seeing quite a few.

Oh! some more news.

I went to the computer store today and they had a sale on hard drives.  So I ended up picking up a 500gb drive and I am going to use this for my second drive to replace the 20 gig drive.

However, now I am obviously not going to use the full 500gb for Ubuntu.  But armed with this much space...I am definitely going to go with a dual boot.

I do still have quite a bit of data on the 20gig drive that I am going to replace...however, I do have quite a bit of space left on my main hard drive, so I can temporarily put my information on that drive.  Thus I am not going to touch the 80gig drive which is my primary.

So while I am going to start with a fresh new hard drive, I am open to any suggestions on what I should do to prepare this drive for a full installation of Ubuntu (but I also want to use it to store files for my Windows programs).  What I am thinking is that I should split the drive into 2 partitions and use 250g for Ubuntu and the other half for Windows programs.  Of course I could go 2/3 Ubuntu and 1/3 Windows as well.  The whole point is that in the end I just want to keep Windows for those programs that I cannot run on Ubuntu.

Finally on the news bulletin for today, I also picked up a 4 gig Flash Drive that was on sale as well.  As I understand I COULD create a bootable version of Ubuntu with this flash drive, but I still have to find a way around the problem that my machine doesn't boot from USB.

I was thinking about something on the way home from work today and I though that my machine does have a floppy drive.  Is there a program I can put on a bootable floppy drive that could tell the computer to boot up Ubuntu from the Flash Drive?  It really isn't that big of a deal anymore since I have the big hard drive, but I am thinking that if I have a bootable floppy and an Ubuntu installation on that flash drive...I could effectively have a personal Ubuntu set up that I can take to any computer and boot up Ubuntu on.  Again not really a priority now...but just a thought.

But I will say that I am very happy that with version 7.10  I can see AND mount my drives. 

Well, I am going to experiment for now and report back with any new findings.

Anyway, thanx again for all your help with trying to help me with version 6.10.  I don't know why I had so many mounting problems with that.  I guess maybe there was something wrong with the disk.  But version 7.10 seems to be much better and it booted faster too.  So now I only can imagine what the latest version will do!

Thanx,
Geo

---

### Post by aktiwers on 2008-05-21
Hey mate,

This is how I would go.

1) Back up your current data. (You could do this from the liveCD using your new Harddrive)
2) Install Windows (pick any size you want). Back when I used Windows, I always created a 10gb partition for XP and a bigger one for all my files/apps. If you backup your data from the LiveCD as I suggested, the partition you choose to create in step 1 could be this other Windows drive. Just remember to format it in Fat32.

3) Next install Ubuntu. In the partitioning part pick "manual partitioning".
Create a 1gb SWAP partition
Create a between 5-15gb EXT3 partition with mountpoint /
And use the rest for a partion in EXT3 with mountpoint /home

Now ubuntu will install and the bootloader (called Grub) will be used when it is done.
This means you will be able to pick between Windows or Ubuntu when you turn on your PC.
Good news is that you should be able to manually edit this bootloader, so that it sees your USB as well.

By the way, it is important that you install Windows first, then Ubuntu. As Windows overwrites Grub (the bootloader) and does not understand well how to boot Ubuntu.

4) When this is done, all you need is to install the EXT3 driver in windows, to let it view your files from Ubuntu. Ubuntu can see the windows drives by default.

Hope this makes sense :)

Good luck and welcome!

Edit: By the way, why not just download Ubuntu 8.04? It's an LTS release (long supported) and it got all the newest stuff. :)

---

### Post by jukingeo on 2008-05-21
> **aktiwers said:**
> Hey mate,

This is how I would go.

1) Back up your current data. (You could do this from the liveCD using your new Harddrive)
2) Install Windows (pick any size you want). Back when I used Windows, I always created a 10gb partition for XP and a bigger one for all my files/apps. If you backup your data from the LiveCD as I suggested, the partition you choose to create in step 1 could be this other Windows drive. Just remember to format it in Fat32.

I have two hard drives in my computer now, an 80 gig and 20 gig.  Windows XP is loaded on to the 80 gig drive and that drive is unpartitioned.  The 20 gig drive I am going to replace with a 500gig drive.  This is obviously WAY too large for my average needs, so what I was thinking of doing was splitting this drive into two partitions.  The first one will be a dedicated partition for Ubuntu.  The second partition could be extra storage space for either windows or Ubuntu files. 

I have no intention of touching the 80 gig drive at all.  So being that I have a Windows installation already and I am locating Ubuntu on a totally different drive.

Just to clarify, I am not setting up a totally new machine.  This machine is already a two hard drive machine.  I am just going to replace the tiny 20gig 2nd drive with the mammoth 500gig drive.

I figure, why box myself in a corner with a small 20 gig drive?  Sure over time I could use the 80 gig drive for space as I use less and less Windows and more and more Ubuntu.

> 3) Next install Ubuntu. In the partitioning part pick "manual partitioning".
Create a 1gb SWAP partition
Create a between 5-15gb EXT3 partition with mountpoint /
And use the rest for a partion in EXT3 with mountpoint /home

You loast me in this part.

> Now ubuntu will install and the bootloader (called Grub) will be used when it is done.
This means you will be able to pick between Windows or Ubuntu when you turn on your PC.
Good news is that you should be able to manually edit this bootloader, so that it sees your USB as well.

So even if I don't have a boot from USB setting in my Bios I can add it to that bootloader (Grub) menu?  That WOULD be cool.

> By the way, it is important that you install Windows first, then Ubuntu. As Windows overwrites Grub (the bootloader) and does not understand well how to boot Ubuntu.

4) When this is done, all you need is to install the EXT3 driver in windows, to let it view your files from Ubuntu. Ubuntu can see the windows drives by default.

Hope this makes sense :)

Good luck and welcome!

Edit: By the way, why not just download Ubuntu 8.04? It's an LTS release (long supported) and it got all the newest stuff. :)

Ok, got the rest of it.  As for going with 8.04.  Well that is complicated.  I am in the midst of changing burning software so I don't know which program to go to next.  In addition, I really burned audio only CD's so I have yet to learn how to burn a data cd...let alone a bootable one.

I know others suggested that I could launch the 8.04 installation without a disk, so I am exploring that option. But, as of now I really don't know which way to go.  Someone did bring up a valid point that burning it to CD would give me a hard copy.  We will see.  I am sure that if I did install from the new 7.10 disk I got perhaps the upgrade to 8.04 would even be easier, right?

Thanx,

Geo

---

### Post by aktiwers on 2008-05-22
> I have no intention of touching the 80 gig drive at all. So being that I have a Windows installation already and I am locating Ubuntu on a totally different drive.

Just to clarify, I am not setting up a totally new machine. This machine is already a two hard drive machine. I am just going to replace the tiny 20gig 2nd drive with the mammoth 500gig drive.

Okay, sorry I misunderstood you there. Then simply begin with exchanging the 2 drives.

> You loast me in this part.

Please forget that part then.
Though I will try to explain it further for you if you would like to install with manual partitioning. The good thing about that setup I mentioned is that you can easily reinstall Ubuntu, without loosing current configuration. 

>  I really burned audio only CD's so I have yet to learn how to burn a data cd...let alone a bootable one.

This is not a hard thing to learn really.
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I would rather go for the download and burn option, rather than upgrade as I have seen a lot more problems with upgrading than installing from Disc.


To get back to your first question. After exchanging the 20gb with the 500gb I would go like this:

1) Download and burn 8.04 as described in the link above.
2) Boot the CD and go to Applications => Accessories => Terminal
and type:
```
gksu gparted
```

 gparted is a program that lets you create partitions and so on. Now on your 500gb create a partition that fit the size you want for extra storage space. You could either choose the EXT3 filesystem on this partition or Fat32. 

Fat32 can be read and written to from both Windows and Ubuntu.
Ext3 can be read and written from both Windows and Ubuntu, if you install the EXT3 driver on Windows. So this is up to you. I like EXT3 best. 

3) After creating that partition, start the install and go through all the questions asked.
When you get to the partitioning part, pick the "manual" solution.

(this makes sense when you are actually doing it)
Pick your 500gb disk from there.
Pick Create new partition and make it 1gb.
Then a dialog will show up where you pick filesystem. Pick SWAP here and click create.

Next you want a partition for Ubuntu. Create a partition for the rest of the space on the disc. Then in the dialog pick EXT3 filesystem. And under "mountpoint" type in: /
And click create.

Then you are done! 
Proceed with the install and you should have a dualboot option.

When done, you could configure Grub (the bootloader) to so that you can boot from your USB, even though BIOS does not allow it. When you get this long, make a new thread here on the forums and we can help you with that.

Good luck :)

---

### Post by jukingeo on 2008-05-22
> **aktiwers said:**
> Okay, sorry I misunderstood you there. Then simply begin with exchanging the 2 drives.

Yeah, I am just changing the "D" (Windows) or "B" (Ubuntu). Since I already had a two disk setup I want to keep it that way to avoid having to touch my Windows drive.  That has an 80gig drive and probably will be fine until I no longer use that machine. 



> Please forget that part then.
Though I will try to explain it further for you if you would like to install with manual partitioning. The good thing about that setup I mentioned is that you can easily reinstall Ubuntu, without loosing current configuration. 



This is not a hard thing to learn really.
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I would rather go for the download and burn option, rather than upgrade as I have seen a lot more problems with upgrading than installing from Disc.

I had another fellow in another thread I started reference that site to me.  Some how even though I started the threads differently they ended up similar.

He recommended that I also burn a disk and set up my partitions in such a way that I can keep my memorized data in a "/home" partition and then set up a small partition just for the Ubuntu program itself.  Then when the time comes to upgrade I all I have to do is obliterate the old installation and start fresh.

I do eventually want to learn to create a hard drive of flash drive to install from because I can see it now that every 6 months I will be making a 'coaster' (as Ubuntu seems to be updated twice a  year).  That is kind of wasteful for a disc

Anyway, I am going to stick with burning a disk for now because it is the easiest and most sure way to go.


> To get back to your first question. After exchanging the 20gb with the 500gb I would go like this:

1) Download and burn 8.04 as described in the link above.
2) Boot the CD and go to Applications => Accessories => Terminal
and type:
```
gksu gparted
```

 gparted is a program that lets you create partitions and so on.

Yeah, I saw there was a link for it in one of the desk top menus and I was able to get into the program.  I didn't have to go into the Terminal.

>  Now on your 500gb create a partition that fit the size you want for extra storage space. You could either choose the EXT3 filesystem on this partition or Fat32. 

Fat32 can be read and written to from both Windows and Ubuntu.
Ext3 can be read and written from both Windows and Ubuntu, if you install the EXT3 driver on Windows. So this is up to you. I like EXT3 best. 

I was told to use EXT3 as well.  I have FAT32 partitions on my old drive, but since I am removing that one, I will have a clean slate and was recommended to use EXT3 which will automatically see Windows files, but not the other way around.  So I need the driver then as you mentioned.

> 3) After creating that partition, start the install and go through all the questions asked.
When you get to the partitioning part, pick the "manual" solution.

(this makes sense when you are actually doing it)
Pick your 500gb disk from there.
Pick Create new partition and make it 1gb.
Then a dialog will show up where you pick filesystem. Pick SWAP here and click create.

Ok, so you definitely need that swap file, correct?  I saw they were saying to almost go twice as much as the current RAM on the computer.  My machine has 1.5 gig, so I should set up a 3 gig swap then correct?

> Next you want a partition for Ubuntu. Create a partition for the rest of the space on the disc. Then in the dialog pick EXT3 filesystem. And under "mountpoint" type in: /
And click create.

Don't I also need to create a /home partition for shared files and also for the personal information?  That was something I read in regards to make things easier in terms of version upgrades.

> Then you are done! 
Proceed with the install and you should have a dualboot option.

When done, you could configure Grub (the bootloader) to so that you can boot from your USB, even though BIOS does not allow it. When you get this long, make a new thread here on the forums and we can help you with that.

Good luck :)

Sounds great.  I am hoping it goes as smoothly as it sounds.

Thanx,

Geo

---

### Post by jukingeo on 2008-05-22
Hello all,

UPDATE: I finally managed to burn myself an iso image tonight!  So now I am up to date with version 8.04.  In fact I am running it now with the live CD.  Tomorrow I am going to upgrade my 'b' hard drive.

So far so good!

Geo

---

### Post by aktiwers on 2008-05-23
Great - let us know if you have more questions :)

---

### Post by kansasnoob on 2008-05-23
re: sound, My daughters PC has a Soundblaster card and I had to first install the Medibuntu repository and then "alsa-firmware" from synaptic.

---

### Post by jukingeo on 2008-05-23
> **aktiwers said:**
> Great - let us know if you have more questions :)

UPDATE:

Ok, guys, there is where I am now. 

I have installed the new 500gig drive in place of the 20gig drive I had there. It took a bit of setting up because this is a SATA drive and I am not used to that format.

Anyway, I did get it installed and the drive is able to be seen by the partitioning program in Ubuntu.

So as of now I am read to partition the hard drive and set up a full install of Ubuntu 8.04 on a dual boot with Windows XP.

With a successful install of the hard drive, what would be the next step?

Thanx,

Geo

---

