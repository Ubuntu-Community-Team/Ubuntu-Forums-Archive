---
title: "An Ubuntu Net Install Diskette For Windows ~ No ISO Required"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ed_agamemnon on 2005-04-24
An Ubuntu Net Install Diskette For Windows ~ No ISO Required
(though not necessarily only for windows)

This floppy (a cut-down Windows98SE boot disk [[more boot disks?](http://www.bootdisk.com)]), when booted, will engage the internet install of Ubuntu Linux (Hoary Hedgehog 5.04).

Usage:
Copy all the files included in the attached zip archive to a floppy disk. (It's less than 1MB so there's plenty of space for FDISK or FORMAT or whatever ~ I just wanted to keep this minimal for the moment)
Download the [linux kernel](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux)  and the [ramdriver](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz)  and place them both in the root directory (C:\).
Put the disk in (do remember to check your BIOS is set to boot from the floppy drive) and reboot.

Typical session:
Power on
"Starting Windows 98..." (I did HEX this out but I figured it was proably illegal so I've restored everything)
"Microsoft Windows 98 Startup Menu", offering CD-ROM support or not;
Type 'grub' (no quotes) at the prompt (A:\>) to run (it should autodetect the menu.lst file, if not, start grub with 'grub --config-file=a:\menu.lst' (no quotes))

Limitations:
I still can't figure out how to make GRUB load either the Ubuntu Live CD ISO or the Ubuntu Install ISO. Google hasn't been much help either.
When Ubuntu is already installed to (hd0) GRUB won't load the a:\menu.lst list ~ maybe this is just me being incompetent?

Acknowledgments:
Google :) and 'andvaranaut' ([http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)) 

... Oh yes! Do make sure you've sorted out all your partitioning before you boot this disk! Lastly, if anything goes wrong... I take NO responsibility.

-ed.

---

### Post by willwarner on 2005-07-20
Thank you for this tool! How do I sort out all my partitioning? I'd like to turn one big windows partition into the recommended OS, home, and swap partitions for a linux system... this installer doesn't include a partition tool the way the Ubuntu ISO does?

---

### Post by savage on 2005-07-30
You will have to learn more about partitioning. Specifically you will need to use the tools for partitioning "fdisk" or "cfdisk". Then you will need to learn the "mkfs" command for formatting the partitions. Easiest way is to use a desktop computer with Linux on it, and slave the hard disk drive you are partitioning to this machine. You could also probably do it without linux installed by using a boot cd. Also be aware that in linux IDE hard drives appear as "/dev/hda", "/dev/hdb" instead of "C:\ "or "D:\" would under dos. Read up on the "mount" command if you get confused on how linux recognizes the hard disks. If you are new to linux I suggest "Linux for the rest of us" a book by Mark Rais.

Also this link looks workable: [http://www.reallylinux.com/docs/install.shtml](http://www.reallylinux.com/docs/install.shtml)

The super duper easy way would be to use a Mandrake linux install CD. Their graphical partitioning tool is very easy to use. Just partition the drive then turn off the machine (skip the rest of the install). Of course you could also get Partition Magic which is a commercial app that you could use to do this from within Windows. If you have the time and inclination it's best to use the gpl'd tools.

---

### Post by cargohook19 on 2005-09-02
I tried using your diskette, and it works ... up to a point.  ](*,)

When I get to the place where it tries to detect the network hardware, it fails. I'm trying to install onto an old **Dell Latitude LM (Pentium MMX)**, which has a BIOS that doesn't allow you to boot from CD. It doesn't matter if I use the **wireless card (Linksys WPC11)** or the **ethernet adapter (3Com EtherLink III Lan PC Card [3C589D])**, the error I get is always **No Network Interfaces Detected**.

Both work fine on WinMe.

I'm a relative linux noob, but I suspect there are some files on your net install diskette that either are not present or need to be tweaked in order to instruct the installation process how to find my network adapters. Only I'm too inexperienced to begin to figure out what to do now.... 

Please help!

By the way, thanks for a great tool for those of us trying to salvage old machines!

---

### Post by Ferhat on 2005-10-08
Hi,

That is a very good solution. 

I have an old ASUS A1 laptop without CDRom (out of order). This solution of ed_agamemnon's, has helped me a lot. I would like to write my steps for beginners :

You need
a) W98SE bootdisk from [www.bootdisk.com](www.bootdisk.com) (for FDISK, FORMAT etc.)
b) ed_agamemnon's boot package and the other 2 files he has written.
c) Command line tool for WinRAR (RARX350.EXE -> rar32.EXE) [www.winrar.com](www.winrar.com)

1 ) WinRAR the 2 needed files as you wish and split into 5 disks.
2 ) Add RARX350.EXE to the last one. We will unrar.
3 ) Generate a W98 SE boot disk ([www.bootdisk.com](www.bootdisk.com))
2 ) Boot with it and FDISK the drive. 
3 ) Create 80 MB DOS partition and keep the rest for Linux [ I am doing this for if anything goes wrong, if the setup fails after partitioning we will loose the boot files. So, keeping them in a small partition would save some time.]
4 ) Reboot, format C:
5 ) Copy 5 disks to the C:
6 ) UNRAR package (ex : rar32.exe e <first_filename.rar>)
7 ) Now you come to a stage where you can start doing ed_agamemnon's steps. 
8 ) Reboot the machine with ed_agamemnon's boot disk.
9 ) Write GRUB on the command line
10 ) Enjoy !...

Thanks ed_agamemnon...

---

### Post by MetalMusicAddict on 2005-10-08
I would like to see a very small .iso that acts like the normal installer (partitioning and all) but pulls exactly what it needs from the net. Up-to-date everytime. No more install from disk then dist-upgrade.

---

### Post by Kelpie on 2005-12-06
i know this thread is kinda old but id like to install Xubuntu (doing a server install for Ubuntu) from my slave drive to my master drive, since i am impaitent for the CDs to arrive, but i wont be doing this again when they do.
thing is, i dont want to partition my master drive for another OS, the only OS i have is win98se and thats a very horrid OS to live with, i much rather live with an OS that is more reliable, may have problems but i know they can be fixed, and doesnt slow the system performance down after time even if you maintain it well.
i would thank you very much if you could tell me how to do this as i am not a winXP user i am a Win98SE user, so the steps should be done for Win98SE, thanks!

---

### Post by hakre on 2006-08-29
> **ed_agamemnon said:**
> Usage:
Copy all the files included in the attached zip archive to a floppy disk. (It's less than 1MB so there's plenty of space for FDISK or FORMAT or whatever ~ I just wanted to keep this minimal for the moment)
Download the linux kernel and the ramdriver and place them both in the root directory (C:\).
Put the disk in (do remember to check your BIOS is set to boot from the floppy drive) and reboot.

Well, I tried to figure this out, but the way you describe it, this floppydisk does not boot at all. the floppydisk needs to be bootable first. I'm looking for a way how to do it and if successfull will post it here. If anyone knows (not only theoretically -I do- but who did this with all the above), please post.

/edit:
Now I made the disk bootable first by using the win98 one of bootdisk.com images and then copied all needed files on the disk after deleting the not needed one on it.
Even if you can start grub afterwards, you are not able to boot from CD then, so this does not solve my problem that was to boot from CD. I'm trying another Bootdisk for that right now which looks quite promising. I'll post that later on.

---

### Post by daroots on 2006-09-25
Thx,
I've been looking around for a netinstall for Ubuntu,
I'm used to debian, i wanna test this release...

Regards,


:) :) :) :) :)

---

### Post by SodR on 2007-02-27
I get to the point: "Booting 'Ubuntu Internet Installer on (hd0,0)'"

Then I get this:

"Kernel     (hd0,0)/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

Error 16: File not found

Press any key to continue..."

I guess I have this because of the installer can't locate the linux file on c:\ ? What should that linux file be called? Linux.bin or just linux without a file-extention? Can someone give me a download link since the one above just gives me alot of text (I took save link as the first time...)

Thanks in advance!

---

