---
title: "Why does Ubuntu installed in USB can’t read this usb storage?"
date: 2015-08-21
forum: New to Ubuntu
---

### Post by t8br2t1 on 2015-08-21
Hi all. I'm new to linux from Korea.
I would say sorry if it is too easy matter.

I installed ubuntu on USB with Universal USB Installer. And it worked. I can run ubuntu on my pc with this USB. But on the ubuntu, it cannot read full storage of this usb.
I bought 64GB usb(sandisk ultra fit). But when I entered in ubuntu, it appears only 3.3gb storage. I tried to transfer file to ubuntu from another harddisk. But it didn&#8217;t work. beacause of short of starage.

When I see this USB on Windows, it appears full 64gb storage.

Why I can&#8217;t see full storage of this usb on ubuntu?
I want to use full storage on ubuntu.

---

### Post by howefield on 2015-08-21
Sounds like you are hitting the file size limitation of the Fat32 file system which means your persistence file can only be about 4GB large at most.

There are ways around it which use a separate ext partition for casper-rw, do a search of the forums for instructions.

---

### Post by yancek on 2015-08-21
> I installed ubuntu on USB with Universal USB Installer

Technically that would not be classed as an install as it is generally the same as using a Live CD either on a CD or DVD.  This means it is a read-only filesystem on which any changes you make to the system or any data you save to it will be lost on reboot.  As pointed out above, you can set up persistence so you can make changes and save data.  Not sure this is possible with UUI so did you in fact, create persistence?

Another option you would have since you have a 64GB drive is to do an actual install to it.

If you have persistence, you can create a larger partition but it won't work with the windows FAT32 filesystem, you need a Linux filesystem.

---

### Post by sudodus on 2015-08-21
Welcome to the Ubuntu Forums :-)

Are you happy to try Ubuntu this way, to run it live or persistent live?

There are other options:

1. *yancek* mentioned that you can make a 'normal installation' to a USB pendrive.

2. You can also try to make a dual boot system with Ubuntu and Windows in the internal drive. If you want to do that, we can help better, when we know more about your computer and how you intend to use it. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and remember to tell us how you intend to use the computer :-)

-o-

See this link and links from it for more details,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by t8br2t1 on 2015-08-21
[SIZE=2][COLOR=#000000][FONT=Arial]Thank you all. I read all your recommendation. Now I see I made live stick, and I mistook live stick for 'normal installation'.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I think I need another usb stick for installing ubuntu on original usb. Am I right? Actual installation was my original intent.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Brand name and model :[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    description: Desktop Computer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    product: B85M-HD3 (To be filled by O.E.M.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    vendor: Gigabyte Technology Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    version: To be filled by O.E.M.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    serial: To be filled by O.E.M.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    capabilities: smbios-2.7 dmi-2.7 vsyscall32[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]CPU : Intel® Pentium(R) CPU G3420 @ 3.20GHz × 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]MemTotal:        8053288 kB[/FONT][/COLOR]

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.9G   86M  3.8G   3% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           787M  1.4M  786M   1% /run
/dev/sdd1        58G  4.9G   53G   9% /cdrom
/dev/loop0      849M  849M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           3.9G  1.2M  3.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   76K  3.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
```

[COLOR=#000000][FONT=Arial]Graphics : Intel® Haswell Desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]And I don't have wifi chip or card.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]I want to make portable ubuntu in usb and use this in anywhere I go, school, home, another guy's house etc. It includes Linux, Mac OS, Window...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I tried install ubuntu in usb instead of installing in hdd in my computer.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Pleas check my understanding :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1. I should use another usb to install ubuntu on my original usb.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2. about file system :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 2-1. If I use FAT32, it will work as live CD[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 2-2. If I use NTFS (actually I did it ago, but my computer cannot read this live stick. only usual Windows was booted)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 2-3. If I seperate usb in FAT32 and ext4 for half, ext4 will be used only in Linux, and FAT32 will used in Windows and only be readable in Linux.[/FONT][/COLOR]
2[COLOR=#000000][FONT=Arial]-4. If I use ext, I can use this usb only in Linux.[/FONT][/COLOR]
[/SIZE]

---

### Post by yancek on 2015-08-21
You need to use either another usb to put the Ubuntu Live CD on from which to install to your 64GB flash drive OR use a DVD.  If the computer doesn't have a DVD drive, then you need the flash drive.

You can use FAT32 for a Live installation.  That is commonly what is used.  You could also use it for a data partition but I don't think that is a good idea due to its limitations.  You need a Linux filesystem on which to install Linux, the default for Ubuntu currently being ext4.  Create a partition of the size you want, 15-25GB.  It depends upon how much software you intned to install later.  When you have completed the install, it is a simple matter to create another partition with the remaining space formatted as ntfs so that it can be used by windows and Linux. 

> [SIZE=2][COLOR=#000000][FONT=Arial]2-3.  If I seperate usb in FAT32 and ext4 for half, ext4 will be used only in  Linux, and FAT32 will used in Windows and only be readable in Linux.[/FONT][/COLOR][/SIZE]

ext4 will only be used in Linux.  There is third party software which you can install on windows which might work to read a Linux filesystem??
FAT32 can be used in windows (it's a windows filesystem) or Linux, read/write.

> [SIZE=2]2[COLOR=#000000][FONT=Arial]-4. If I use ext, I can use this usb only in Linux[/FONT][/COLOR][/SIZE]

No.  You will only be able to use the system partition on which you install Ubuntu from Ubuntu as explained above.
If you install proprietary drivers, particularly for a graphics card, you might have problems with it using it on other machines.

---

### Post by sudodus on 2015-08-21
+1 I agree with yancek's advice.

An alternative to an installed system is a persistent live system as described in these links

[mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10)

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

Some time ago a made a portable ***installed*** system, that works in BIOS as well as UEFI mode. You can use the systems that I made or you can get tips from them and make your own system. Beware that there are problems with 'standard installed systems in UEFI mode', if you move the system between computers.

If you want a pendrive with a live and an installed system, that works in UEFI and BIOS mode, you can try 
[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506).

---

### Post by t8br2t1 on 2015-08-22
Thank you Howefield, yancek, sudodus. For all you, finally I realize what was problem. I will follow your instruction. 
get another dendrive for live, and install ubuntu on intended 64gb flash drive in FAT32.
Then try it on PCs around me. 
If I face problem you mentioned, I will try portable installed system that you made.
Thank you for instruction.

---

