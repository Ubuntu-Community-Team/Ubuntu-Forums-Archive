---
title: "Installing ubuntu onto totally seperate hard drive"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by zephyrost on 2013-04-12
Hi, i've been using ubuntu a little bit and have just bought a new computer for which i still need to buy a data drive.

  I'm going to put both windows 7 and ubuntu on it but it struck me that it might be a good idea to buy two seperate hard drives, rather than partition a larger one.

  This appeals as i thought it might be a little easier to manage them but i'd like to know if anyone has any experience and ANY advice FOR or AGAINST doing this rather than a single HD (assume i know nothing, in which you'd be pretty much correct)

  Thanks,
    Zephyr

---

### Post by fantab on 2013-04-12
I would say, its an excellent idea to have two HDDs with Windows installed on ONE and Ubuntu on another. I have the same set up.

My suggestions:
* Install Windows on the first HDD (/dev/sda) and preferably on the First Partiton (/dev/sda1). 
* Install Ubuntu on the Second HDD (/dev/sdb). Install Ubuntu Boot-Loader, GRUB on /dev/sdb and NOT on Windows HDD /dev/sda
* Change in the BIOS the HDD order to Boot your Second HDD first. This will then Load the GRUB boot-loader and you can select from the menu which OS you want to boot into.

* When you partition your Second HDD, /dev/sdb make your self at-least TWO (more if you like) 20GB partitions, so that you can have two versions of Ubuntu or have two distros... just in case you need it in future. Plan Ahead.
* Consider NOT having separate "/home' partition but instead go for a plain ext4 linux partiton to save your DATA and you can share this with any number of Distros. The one outright benefit will be that you don't have to worry about DATA loss when you re-install ubuntu. You can just format the 20 GB "/" partition and install your data will be sitting safe on its DATA partiton.

My two cents....
Let us know if you have more doubts...

---

### Post by zephyrost on 2013-04-12
Excellent, thanks for the reply.

  One more question - I'm going to be using a SSD agility drive (probably should have mentioned that, sorry) and the these two drives as data drives, so does this change your advice about partitioning the drives

  Would i instead partition the SSD to put the multiple ubuntu installs on that, or should i save that and just use it for windows (The windows half is mostly for gaming whearas the ubuntu is for work so possibly doesn't need the extra speed?)

  Thanks

---

### Post by fantab on 2013-04-12
> **zephyrost said:**
> Excellent, thanks for the reply.

  One more question - I'm going to be using a SSD agility drive (probably should have mentioned that, sorry) and the these two drives as data drives, so does this change your advice about partitioning the drives

  Would i instead partition the SSD to put the multiple ubuntu installs on that, or should i save that and just use it for windows (The windows half is mostly for gaming whearas the ubuntu is for work so possibly doesn't need the extra speed?)

  Thanks

That would depend on how big the SSD is going to be. If there is enough space on SSD then you can boot both Windows and Ubuntu [20GB "/"] (assuming it will be your MAIN Linux OS) from it. Just install the GRUB on 2nd HDD and like mentioned make the Bios boot it first. 

You can also install Grub on SSD, however if you later choose to remove ubuntu/linux and have only Windows on your machine then you WILL have to 'fix Windows Boot' with Windows Recovery Disc or Installation Disk. I don't have much experience with SSD, so I don't know if there is any catch.

You can have other Linux or ubuntu versions on the dedicated HDD.

---

### Post by Habanero101 on 2013-04-12
I have a 2 PCs running multiple OSes from one hdd each. What fantab says is true, it may be simpler with one OS per hdd, but it's not impossible to put them all on one drive. You just have to be smart about it. Partition your drive appropriately, install all your windows OSes first, starting with the oldest ones then newer, then install your linux distros. To me it doesn't matter if windows gets the first partition, as long as it gets a primary partition or the beginning of an extended partition, to load it's boot loader, it sits happy.

Install linux and it's grub in the same partition.

I have windows xp 32-bit and Ubuntu 12-10 32-bit running on my PC like this and on my laptop, I have:
3 windows - windows xp 32-bit, windows 7 64-bit and windows 8 64-bit - all loaded by windows boot loader
2 linux - Ubuntu 12-10 64-bit and Fedora 18 64-bit - loaded by GRUB2

GRUB2 also loads the windows boot loader by chain loading, so the grub2 boot loader would appear first and show Ubuntu, Fedora and Windows Boot loader;
at this point you can choose what you want to boot into. Windows boot loader would load the windows selection screen to boot into your default windows or choose another installed version.

So far I've been running the PC for over a year and a half without issue and the laptop for about a month, also without issue. 

Note that if you screw up anything, and need to re-install windows for any reason, you'll also need to repair grub.
Also if doing the multiple OS install for the first time (or even not the first time) it is a good idea to image the drives as you are completed with each install stage, so that if you screw anything up, you can just re-install the image and start from there. A good FREE image software you can use, which is windows based is [Macrium Reflect]("http://www.macrium.com/reflectfree.aspx").

---

### Post by pfeiffep on 2013-04-12
For those folks who have a laptop with only one hard drive it is possibly to install Ubuntu to a USB hard drive. Fantab posted some excellent advice:
> [COLOR=#000000]My suggestions:[/COLOR]
[COLOR=#000000]* Install Windows on the first HDD (/dev/sda) and preferably on the First Partiton (/dev/sda1). [/COLOR]
[COLOR=#000000]* Install Ubuntu on the Second HDD (/dev/sdb). Install Ubuntu Boot-Loader, GRUB on /dev/sdb and NOT on Windows HDD /dev/sda[/COLOR]
[COLOR=#000000]* Change in the BIOS the HDD order to Boot your Second HDD first. This will then Load the GRUB boot-loader and you can select from the menu which OS you want to boot into.[/COLOR]
> [COLOR=#000000]* Consider NOT having separate "/home' partition but instead go for a plain ext4 linux partiton to save your DATA and you can share this with any number of Distros. The one outright benefit will be that you don't have to worry about DATA loss when you re-install ubuntu. You can just format the 20 GB "/" partition and install your data will be sitting safe on its DATA partiton.[/COLOR]

There are differing thoughts about a separate home partition - I found this post [educational]("http://askubuntu.com/questions/142695/what-are-the-pros-and-cons-of-having-a-separate-home-partition").
Consider sharing data bidirectionally - remember Windows does not read ext4 partitions. [Read more here]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by kurt18947 on 2013-04-12
I think the separate data partition is an excellent idea.  At least with *nix it's pretty easy to reinstall the O.S.  It's probably the best idea to make the common data partition NTFS formatted with Windows.  There are system level drivers for Windows that will read ext.3 or ext.4 file systems but using Windows to *write* ext.3/4 data seems a dicy proposition.

---

### Post by fantab on 2013-04-12
@pfeiffep: If there is USB drive then you will tell the BIOS to BOOT "USB Devices First" or something like that. That ways if a USB is plugged in BIOS will boot it first, if not the regular HDD will boot.

---

### Post by pfeiffep on 2013-04-12
> [COLOR=#000000]@pfeiffep: If there is USB drive then you will tell the BIOS to BOOT "USB Devices First" or something like that. That ways if a USB is plugged in BIOS will boot it first, if not the regular HDD will boot.[/COLOR]

While that's probably true in most cases it certainly isn't on this ancient Dell Laptop - if I wish to boot directly to USB device F12 needs to be depressed to enter a one time boot option. I'm not using Win anymore on this laptop so I installed grub onto BOTH hard drives; since there's 2 OSes grub presents the option to boot either. When I power up the device with USB plugged in I can successfully boot to either OS.

---

