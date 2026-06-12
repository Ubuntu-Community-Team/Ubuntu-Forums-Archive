---
title: "HOWTO: Install Ubuntu Linux without burning a cd"
date: 2005-04-22
forum: Outdated Tutorials &amp; Tips
---

### Post by ed_agamemnon on 2005-04-22
#EDIT: The automatic installer script included with this thread has been removed. The new version is available for Breezy and Dapper here: errr... waiting for the thread to be approved by a moderator... zzzz!

How to install Ubuntu Linux without having to burn the .ISO image to CD.

Why would you want to do this?
1 - you don't have a cd burner.
2 - you can't be bothered to wait for your pressed cd to arrive in the post.
3 - because you can...

-- The howto is mainly a simplification of this ([Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media](http://marc.herbert.free.fr/linux/win2linstall.html)) excelent guide for which i take no credit  --

The hardware i used to sucessfully install Ubuntu without booting a CD:

Dell Inspiron 1100 2.2 Ghz laptop, 20GB hard disk, running Windows XP on a single NTFS partition. No other system has been tested ~ at least, not by me.


Brief overview of the steps:
1 - resize the c: windows partition
2 - get hold of the ubuntu kernel
3 - set up GRUB for NT
4 - install ubuntu :D

easy really! i should stop now, hehe


#1 ~ Resizing the partition
(I used Partition Magic 8.0)

Notes:

The trick is not to create specific Linux partitons, but to resize the Windows one leaving nothing but free 'unallocated' space. The ubuntu installer will be able to install itself to this space and do all the fancy partitioning stuff automatically without frightening us linux n00bs too much :)

In my case i redistributed my 20GB to 15GB for windows and 5GB of 'unallocated space'.

#2 ~ Setting up the kernel

We only need to download two files for the installer to work...

[linux.bin](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux) 
[initrd.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz) 

both of these we could download from [the ubuntu archive](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

place both of these files in C:\boot
- you'll probably have to create this directory yourself

#3 ~ Setting up GRUB for NT (a bootloader that will allow us to choose either the Ubuntu installer or to boot normally into Windows)

The files that we need for GRUB for NT actually contained in the GRUB for DOS package, but that's no problem, so download that:

from here: [http://newdos.yginfo.net/grubdos.htm](http://newdos.yginfo.net/grubdos.htm) 
or here: [http://grub.linuxeden.com/](http://grub.linuxeden.com/) 

The two files that we want are "menu.lst" and "gldr", you can delete the rest. Place "gldr" in the root of the hard disk (probably C:\) and make a new directory inside C:\boot called 'grub' (ie, C:\boot\grub) and put you menu.lst in there.

All we have to do now is edit the menu.lst to give an option to select the Ubuntu installer and to set the boot.ini to load GRUB.

A) ~ Editing menu.lst

open it with notepad and append right at the bottom of the file the following lines:

> 
title Ubuntu Installer (hd0,0)
kernel   (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/initrd.gz



(a lot of the stuff in that file can be cut out, but it's no big deal, we'll leave it for now)

B) ~ editing the boot.ini

The problem here is that this particular file is not only write-protected but also hidden. So to undo all this open a command prompt (Start -> Run -> cmd.exe)

type:
> 
attrib -a -r -s -h c:\boot.ini


now open the boot.ini file with notepad and add this line on at the end:

> 
C:\grldr="Start GRUB"


...

That's it! :D


4 ~ Installing Ubuntu

Now when you reboot you should be presented with a screen offering you the choice to either boot into windows, or to 'Start GRUB'; choose 'Start GRUB' and then on the next menu choose 'Ubuntu Installer'.

The installer will run and download all the parts it needs for a while until you get to the partitioning stage... Ubuntu will ask you to install in on the whole of your drive - which obviously we do no want, so choose manage drives personally (or whatever the label is, i don't remember exactly :s) and then you will be able to tell it to install onto the 'unallocated space' we created earlier with Partition Magic. Ubuntu will then set its own ext3 and swap partitions from this space and continue to download and install itself to the empty half of the drive :)

After this (or maybe it was before?) you'll be prompted with the Ubuntu's own GRUB screen... It should have detected Windows, if so, just agree with it and allow it to install its own GRUB to the boot sector.

That's it!
Fin!

Sorry it's so badly written and all, but i've just done this and was pretty pleased so i thought it was important to share :P

***

Lastly, I have attached all the files needed to set this up in a .zip (EXCEPT FOR inird.gz and linux.bin ~ they're just too big, you'll have to download them yourself to the same folder where you extract this archive to) with this message, inside is a .bat file which can set the whole business up for you :)

IT IS NOT MY FAULT IF IT SCREWS EVERYTHING UP ~ sorry!

The .bat file expects to run on Windows XP (though i don't suppose it'll care what you run it on...) and will do the following:

create c:\boot
create c:\boot\grub
move grldr to c:\
move linux and initrd.gz to c:\boot
insert a pre-edited version of menu.lst into c:\boot\grub
unprotect the boot.ini
append data to the boot.ini
reprotect the boot.ini

effectively, you could extract the files, run the .bat and then reboot, and all's fine :)


One last thing, i take no responsibility for any ill effects caused by either your following of this guide, or by running my .bat file.

-ed.

Useful? Try here too: [http://www.ubuntuforums.org/showthread.php?p=145618#post145618](http://www.ubuntuforums.org/showthread.php?p=145618#post145618) 

EDIT: (24/04/2005) 
#1 - I forgot to type (hd0,0) after 'Unbuntu Installer' in the new c:\boot\grub\menu.lst file sorry! I've fixed the .zip package too.
#2 - Removed all the stuff about renaming linux to linux.bin ~ seems that was all pointless (archive updated accordingly).

(13/06/2005)
#3 - Finally fixed the "title Ubuntu Installer" line - sorry about that... I'll fix the archive soon too; just a little busy right now...

(27/06/2005)
#4 - Added wget.exe (command-line based download program) and set it up to download both the 'initrd.gz' and 'linux' and put them in the right place.

So... Now all you have to do is partition your hard disk, run 'install.bat' and reboot. Though - as always - I take NO responsiblity for whatever happens...

---

### Post by andvaranaut on 2005-04-22
This rocks. Thanks for sharing.

If I have understood well, all the packages are fetched over the network, so that this is effectively a network installer.

Maybe some sort of rudimentary floppy/net installer might be built with this. Something like having a floppy disk image which looked for the linux.bin file in (hd0,0) (which will either be C:\ or / to 99% of people out there). Or a USB keychain boot sector that could fish the .bin from the keychain and do a network install. That would be awesome, specially since the Ubuntu base installation is probably ~400 Mb of packages, which with the broadband links of today would not amount to more than 2-3 hours time.

I have read elsewhere that it is possible to copy the raw ISO image to a HD partition and that the installer would be able to pick it up. This would make it possible to do a 'CD installation' (without having to download data from the net) without actually having to burn the CD. Perhaps the .iso could also be automatically mounted if found on (hd0,0)/. Or be written in a 700 Mb partition to be later used for swap. 

Anyways, seems rather useful for me because it addresses one of the (few! ;)) Ubuntu weaknesses: the fact that the only easy way to install it is booting from CD.
Cheers.

---

### Post by Hardeep on 2005-04-23
Hi-

After clicking on "Start Grub" I do not see the *Ubuntu Installer* in the list of items. Last one I see if for Mandrake iso install. 

Also, I see a screen flash with "find...and something else" before seeing the Install options.

Please help!

---

### Post by ed_agamemnon on 2005-04-23
It sounds like you've not properly configured your menu.lst file (c:\boot\grub\menu.lst).

Have you appeneded this to the bottom of it?

> 
title Ubuntu Installer on (hd0,0)
kernel   (hd0,0)/boot/linux.bin vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/initrd.gz


Try that :)

If you're still stuck, the menu.lst included in the .zip above would work perfectly well...

The flash screen is nothing to worry about, that's just GRUB loading.

-ed.

EDIT: (24/04/2005) added "on (hd0,0)" - should fix everything. oooops; and sorry.

---

### Post by kahping on 2005-04-23
[QUOTE=ed_agamemnon]B) ~ editing the boot.ini

The problem here is that this particular file is not only write-protected but also hidden. So to undo all this open a command prompt (Start -> Run -> cmd.exe)

type:


now open the boot.ini file with notepad and add this line on at the end:



...

That's it! :D
[/QUOTE]

On Windows XP, you can go to System Properties->Advanced and click on Settings in the Startup & Recovery section. the new window that pops up has a Edit button under System Startup that will open boot.ini for you for editing purposes ;-)

kahping

---

### Post by Poppei on 2005-04-26
Hi,

[QUOTE=andvaranaut]
I have read elsewhere that it is possible to copy the raw ISO image to a HD partition and that the installer would be able to pick it up. This would make it possible to do a 'CD installation' (without having to download data from the net) without actually having to burn the CD. Perhaps the .iso could also be automatically mounted if found on (hd0,0)/. Or be written in a 700 Mb partition to be later used for swap.[/QUOTE]

Do you remember where you've read this? I copied the iso onto my laptop (which has no CD drive) over internal network. Now, I want to install it from iso.
On the machine a SuSE distribution is running and GRUB is also installed, but I want to kill SuSE and install Ubuntu. ;-) This description is great, but I cannot really connect to the internet for I only have a WLAN-card (and this one must function)...

OK, thanks!!

CU Poppei

---

### Post by andvaranaut on 2005-04-26
[QUOTE=Poppei]Hi,



Do you remember where you've read this? I copied the iso onto my laptop (which has no CD drive) over internal network. Now, I want to install it from iso.
On the machine a SuSE distribution is running and GRUB is also installed, but I want to kill SuSE and install Ubuntu. ;-) This description is great, but I cannot really connect to the internet for I only have a WLAN-card (and this one must function)...

OK, thanks!!

CU Poppei[/QUOTE]
 It cost me a few head scratches, but here it is:

[http://ubuntuforums.org/showthread.php?p=83151#post83151](http://ubuntuforums.org/showthread.php?p=83151#post83151)

It essentially involves making a raw 700 Mb partition and copying the ISO there (I suspect dd if=ubuntu.iso of=/dev/hdXY would make the trick). If the link above is correct, the installer should give you the option of using the partition as the source for the ISO image.

According to [http://ubuntuforums.org/showthread.php?t=17866](http://ubuntuforums.org/showthread.php?t=17866) there should be a 'detect and mount CD-ROM' option where (I presume) you will be able to specify where you have copied the ISO over.

Please, if it works, by all means post it and write a (not necessarily long) HOWTO in the forums, so that we can have this thread archive. The "how to install without CD drive" question pops up rather often, it seems ;)

Good luck

---

### Post by Poppei on 2005-04-26
Hi,

> **andvaranaut]It cost me a few head scratches, but here it is:
[http://ubuntuforums.org/showthread.php?p=83151#post83151](http://ubuntuforums.org/showthread.php?p=83151#post83151)
[/QUOTE)

Hmm, there is following sentence "When the CDROM drive fails to ignitiate stage 1, it will prompt you with other methods of installations."
I have no drive, so I cannot have this option.  said:**
> 
It essentially involves making a raw 700 Mb partition and copying the ISO there (I suspect dd if=ubuntu.iso of=/dev/hdXY would make the trick).
[/QUOTE)

OK, I did that after this [1] instruction I've found in a newsgroup. I Think this way I will be able to do an HD-Install. But I got a problem with GRUB (I suppose).
In my /boot/grub/menu.lst I have following entry:

[QUOTE)
###Don't change this comment - YaST2 identifier: Original name: linux###
title Kubuntu-Install
    kernel (hd0,3)/gregor/vmlinuz ro root=/dev/hda4
    initrd (hd0,3)/gregor/initrd.gz
[/QUOTE)

OK, my "/boot" is hda1, "swap" is hda2, "/" is hda3 and "/home" is hda4. I decompressed the iso into /home, as described in [1] (I mounted it with loop-option and copied it into /home). So I think hd(0,3) is correct.
The Kernel is booted well, but there's following error-message:

> 
VFS: cannot open root device "hda4" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


What's wrong? I've even deleted the root-entry or set it to hda3, but I still cannot boot. :-(
Any ideas?

[QUOTE=andvaranaut]
Please, if it works, by all means post it and write a (not necessarily long) HOWTO


Sure I will! ;-)

Thanks!

[1] [http://www.google.de/groups?hl=de&lr=&c2coff=1&threadm=3f8404f5%241%40news.fhg.de&rnum=1&prev=/groups%3Fas_umsgid%3D3f8404f5%25241%40news.fhg.de%26lr%3D%26hl%3Dde](http://www.google.de/groups?hl=de&lr=&c2coff=1&threadm=3f8404f5%241%40news.fhg.de&rnum=1&prev=/groups%3Fas_umsgid%3D3f8404f5%25241%40news.fhg.de%26lr%3D%26hl%3Dde)

---

### Post by arcilite on 2005-04-26
Has anyone tried making the raw partition and moving the iso over to it? Then installing from the iso. Now that I think about it I dont belive that would work... how would you "extract" the iso onto a raw partition anyways? I know linux has dd but what about windows?

---

### Post by arcilite on 2005-04-27
Need to fix the menu.list

need to add title before the word ubuntu at the bottom.

works like a charm then ;-)

---

### Post by Staesys on 2005-04-27
*"Has anyone tried making the raw partition and moving the iso over to it? Then installing from the iso. Now that I think about it I dont belive that would work... how would you "extract" the iso onto a raw partition anyways? I know linux has dd but what about windows?"* 

I'm not completely sure this is what you're asking, but ISO BUSTER for windows will give you complete access to the ISO file.

-Paul

---

### Post by Poppei on 2005-04-27
[QUOTE=arcilite]Need to fix the menu.list

need to add title before the word ubuntu at the bottom.

works like a charm then ;-)[/QUOTE]

What?
Sure it has something to do with a wrong entry in menu.list... but I don't know what.
Or is the fact that it is a reiser-fs the problem?

I hope we'll get that! ;-)

PS: I have ONLY SuSE Linux installed on this machine. I have NO Windooze...

---

### Post by arcilite on 2005-04-27
change 
 Ubuntu Installer (hd0,0)

to 
title Ubuntu Installer (hd0,0)

---

### Post by Poppei on 2005-04-28
[QUOTE=arcilite]change 
 Ubuntu Installer (hd0,0)

to 
title Ubuntu Installer (hd0,0)[/QUOTE]

Hmm, as I posted before, my menu.lst entry is:

> ###Don't change this comment - YaST2 identifier: Original name: linux###
title Kubuntu-Install
    kernel (hd0,3)/gregor/vmlinuz ro root=/dev/hda3
    initrd (hd0,3)/gregor/initrd.gz

So everything is OK? The only error is:

>  VFS: cannot open root device "hda4" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

CU Poppei

---

### Post by raviji7 on 2005-04-29
**I think EVERY distro should do what SLAX has done! ! ! !   **

I can literally boot to SLAX from my laptop with **3 dos commands.**

After booting from a dos floppy that automatically loads drivers for my PCMCIA cd-rom drive, generic USB drivers to boot to my USB pen drives and USB CD-ROM drives and drivers to boot to my parallel port microsolutions backpack cd-rom drive.  Then all I do is type THREE SIMPLE COMMANDS to run the .bat file on the SLAX CD or from my USB flash/pen drive.

1) A:\> D:
2) D:\> cd dos
3) D:\DOS> linux.bat

**AND SLAX BOOTS !! ! !**

Why cant ALL Distros place a linux.bat file that lets you boot the Live/Install CD right from DOS using LOADLIN.  The loadlin, linux.bat and config file all just add take up ONLY 35KB.  You can easily add this to ANY
CD no matter how MAXed out it may be.

This is REALLY REALLY REALLY helpful for people you who cannot boot from CD-ROM or USB Pen Drives,  

And one NEVER has to worry about the the kernel getting too big to fit on a floppy 
because ALL you need is ONE boot floppy with DOS and some DOS drivers that gives you access to those non-bootable drives and then you just have to run the LINUX.BAT file - SOOOOO EASY.  

**NO MORE POOR MAN'S INSTALL or using 25 floppies or having EXTRA drivers or doing NET installs ! ! ! ! ! ! !**

---

### Post by Poppei on 2005-04-30
Hi,

thanks for your post, but that doesn't solve my problem. I still try to boot Ubuntu from HD.... my only wish is to have a solid ubuntu system running on my laptop.

CU Poppei

---

### Post by Poppei on 2005-05-01
Hi,

> **arcilite]Need to fix the menu.list

need to add title before the word ubuntu at the bottom.

works like a charm then  said:**
> 

OK, here are some news: I really got that damn kernel to run! I took the initrd an kernel from CD and booted it with grub. I found a little doc on the Ubuntu-CD that described how to boot this:
> 
title  New Install
kernel (hd0,0)/boot/newinstall/vmlinuz **root=/dev/ram0** devfs=mount,dall ramdisk_size=17000
initrd (hd0,0)/boot/newinstall/initrd.gz

Now everything boots, but the installation process isn't able to find a CD drive (but I have no!)... no I don't know how to start the installer. There is a little shell, perhaps this way I can?
Some threads say that after satge1 fails, you can choose between Harddisk install and/or FTP Install and so on... but where is this option?
Something makes me wondering. In the doc from the Ubuntu-CD there's following sentence:

[QUOTE]Copy the following files from the Debian archives to a convenient location on your hard drive

These files are vmlinuz and initrd... but what is this Debian archive? That means that I have to use an other kernel than this of the CD?

Perhaps someone can point me to the right direction...

CU Poppei

---

### Post by Poppei on 2005-05-01
Hi again!

[QUOTE=Poppei]
These files are vmlinuz and initrd... but what is this Debian archive? That means that I have to use an other kernel than this of the CD?
[/QUOTE]

The answer is YES!! I had to use [this Kernel images](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/images/hd-media/)  and mount it as described above...
The installation of Ubuntu was withput any problems, however, I now have a big problem:

The basic system is installed now and the mahine boots for the first time... now I was asked to insert the install media in /cdrom... funny: WHICH CDROM?? I installed it from an iso from HD.

OK, my partitions are:
> hda1 = /
hda2 = swap

The funny thing is, that on my old machine /hda4 was /home, where I put the iso into. So I couldn't format this partition. I tried to set the /home-mountpoint to this partition, but this wasn't possible (I think because it was used). So I chose "do not mount"...
So this partition isn't reachable. I thought I will partition it with qtpart afer installation, I didn't know that I will need it...

**So the problem is: HOW I now can go further?? How do I find my partition?**

1) **How can I mount the "lost" partition?** It isn't listed in /etc/fstab... I thought after I mounted this, I can mount the iso looped into /cdrom
2) Network should work now. **Can I use the CD over network now?** NFS or whatever... where can I set that? Sorry, I don't know, it's my first Debian installation... aptitude works, but it needs the CD...

OK, I hope I'll get it run... then I can write a HOWTO...

CU Poppei

---

### Post by CrustyDOD on 2005-05-19
I have interesting question!

How on earth do you edit boot.ini in Windows 98 if there is no boot.ini file? :) 

Trying to install ubuntu (server) on some old machine where there is a CD-ROM but its not bootable, floppy is hardly working... but lan is working!  :D 

my editing/trying ended here: **B) ~ editing the boot.ini**

Inserted that line (C:\grldr="Start GRUB") into autoexec.bat, msdos.sys and system.sys and nothing happens.. invalid command is the output.. tried running grldr command in ms-dos, unknown command..

I think i just rode into dead end.. help wanted..

---

### Post by JC4P on 2005-05-28
this may be a dumb question but does this mean that if i do all of this, Ubuntu And Windows will co-exist?

---

### Post by dom02 on 2005-05-29
[QUOTE=Hardeep]Hi-

After clicking on "Start Grub" I do not see the *Ubuntu Installer* in the list of items. Last one I see if for Mandrake iso install. 

Also, I see a screen flash with "find...and something else" before seeing the Install options.

Please help![/QUOTE]

I had the same problem.  when I was looking at the other entries in menu I noticed that they all had "title" before them so I added that and it worked fine.
This is what mine looks like:

title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz

---

### Post by dom02 on 2005-05-29
I was able to install linux without any problems this way but now I can't boot up.  It just goes to the grub bootloader that was used to boot up into the installer.  Is there a way to change that bootloader so it can load Ubuntu? Or is there a way to install a new bootloader?  During installation I installed lillo but it isn't loading.

---

### Post by ed_agamemnon on 2005-06-13
> this may be a dumb question but does this mean that if i do all of this, Ubuntu And Windows will co-exist? 

That's right, follow these instructions and you'll have both Windows and Ubuntu Linux...

---

### Post by Nasky on 2005-07-11
Hi

 I've just tried to install Ubuntu by the way you've clearly explained but I have a problem.
 Actually, I'm using Windows and Mandrake on my computer. I would like to take off Mandrake in order to use Ubuntu. The damn problem is that LILO is already launched at the boot. So I have to choose between Windows and Linux. That's why I think that GRUB can't be launched. I've done exactly what you wrote but because of Lilo was already there, I can't start Grub...
Maybe should I uninstall Mandrake (and obviously Lilo will be automatically taken off) before trying start Grub and Ubuntu Installer...

What do you think about this problem? Is Lilo the problem or have I done something wrong in my configuration? I don't think so cuz I've used the zip file. And to be sure that eveyrthing's gonna be alright, I've manually checked the files I have to edit, and there are all ok.

Thanks.

Nas'

---

### Post by Nasky on 2005-07-11
OK... i've just uninstalled LILO thanks to "lilo -U" from Mandrake.
Now, Lilo is not launched anymore but Grub neither.
So Windows starts without asking me anything...
I couldn't install Ubuntu and now I can't use Mandrake. Great :( !!

I don't know if it cares but i'm on Windows 98 and not XP...

Please need ya help !!!

Nas'

---

### Post by UbuWu on 2005-07-11
Instructyions for this can also be found here: [https://wiki.ubuntu.com/InstallUbuntuWithoutRemoveableMedia](https://wiki.ubuntu.com/InstallUbuntuWithoutRemoveableMedia)

---

### Post by markuman on 2005-09-04
hi,

i try to install ubuntu without a cd on a gericom notebook.

but there is no windows - only SuSe.

so i have download the kernel stuff and leave it in /boot

than i have edit the grub menu.lst from suse

```

title Ubuntu Installer (hd0,1) 
kernel (hd0,1)/boot/linux vga=0x314 ramdisk_size=14972 root=/dev/hda2 rw -- 
initrd (hd0,1)/boot/initrd.gz

```

if i want to boot it, grub canceled with "Error 27: Unrecorgnized command"

the hole output:
```

kernel (hd0,1)/boot/linux vga=0x314 ramdisk_size=14972 root=/dev/hda2 rw -- 
[Linux-bzImage, setup=0x1600, size=0x1209f6]
initrd (hd0,1)/boot/initrd.gz
[Linux-initrd @ 0x736a000, 0x475a6b bytes]
color white/blue black/light-gray
default 0
Error 27: Unrecorgnized command
Press any key to continue...

```

i don't know how i can edit it so that it works....

any ideas?

greetings
markus

---

### Post by mr_mop on 2005-09-05
Great stuff, thanks.
I only had DOS 6 on my machine, so had to install to config.sys and not boot.ini, but it still worked!
Quicker to install DOS than Windows too! :)

---

### Post by ultra.nj on 2005-10-08
I'm having a problem with this..everytime I try to start up GRUB, there's an error that says HAL.DLL is corrupt/missing, how can I fix this?

---

### Post by mr_mop on 2005-10-09
Is there a way to modify this so that it does the server install only?

---

### Post by cosonic on 2005-10-09
hi
 after going in to install i get this 

 Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
Error 16 : File not found.


linux file is there..i e in c:/boot  so what file and how to fix it ?
thx

---

### Post by vampire_janus on 2005-12-04
if you need to install from iso please check out this thread
[http://ubuntuforums.org/showthread.php?t=98451](http://ubuntuforums.org/showthread.php?t=98451)
but i did it for breezy though

---

### Post by vampire_janus on 2005-12-04
i just like to link this thread to
[http://ubuntuforums.org/showthread.php?t=98451](http://ubuntuforums.org/showthread.php?t=98451)
which is related and more updated

---

### Post by UbuntuMember on 2005-12-05
[QUOTE=andvaranaut]It cost me a few head scratches, but here it is:

[http://ubuntuforums.org/showthread.php?p=83151#post83151](http://ubuntuforums.org/showthread.php?p=83151#post83151)

It essentially involves making a raw 700 Mb partition and copying the ISO there (I suspect dd if=ubuntu.iso of=/dev/hdXY would make the trick). If the link above is correct, the installer should give you the option of using the partition as the source for the ISO image.

According to [http://ubuntuforums.org/showthread.php?t=17866](http://ubuntuforums.org/showthread.php?t=17866) there should be a 'detect and mount CD-ROM' option where (I presume) you will be able to specify where you have copied the ISO over.

Please, if it works, by all means post it and write a (not necessarily long) HOWTO in the forums, so that we can have this thread archive. The "how to install without CD drive" question pops up rather often, it seems ;)

Good luck[/QUOTE]
It ask me to Mount CD-ROM, but it doesn't ask where I placed the ISO over. =/ 

Anything you can help me with this? 8-[

---

### Post by UbuntuMember on 2005-12-05
Nobody knows? I need help.. :KS

---

### Post by jhhdk on 2005-12-06
Great post !!!

Kind Regards
Jan H. Hansen
Ubuntu user since 2005/12/06~23:30CET

---

### Post by _ivan_ on 2005-12-07
Hi, i have followed the guid from the top to the bottom but when i boot up and press "start grub" i only gett black screen! what am i doing wrong? i hava a sony vaio!

---

### Post by UbuntuMember on 2005-12-22
Still nobody can help me ? I really need help.. =/

---

### Post by john_spiral on 2006-01-01
Hi,

I've gone through the installation procedure on (same as this thread):

[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

After choosing "Install Ubuntu" on my sony vaio laptop it only brings up a blank screen.

Has anyone out there managed to install ubuntu on one of these beasts?

John

---

### Post by john_spiral on 2006-01-02
Hi again,

I've managed to get the Installation from Windows running by using the latest version of grub4dos.

grub_for_dos-0.4.1.zip

I've copied the breezy cd from another machine via a network to my local drive /ubuntu as per the instructions on the below page:

[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows) 

It now keeps indicating that it can't find the CD, but my machine doesn't have one?

getting closer :-)

---

### Post by john_spiral on 2006-01-07
for those out there still following this thread have a look at:

[http://www.ubuntuforums.org/showthread.php?t=111719](http://www.ubuntuforums.org/showthread.php?t=111719)

---

### Post by dilaudid on 2007-01-02
Hi, This worked for me, installing edgy 6.10 on my Thinkpad T23 and T22. I already had gentoo installed on both laptops. One problem I found was that the installation would stall during the "installing base system" and repeatedly failed when trying to install the kernel image:
```
apt-install: WARNING: The following packages cannot be authenticated!
apt-install:   linux-image-2.6.17-10-generic linux-image-generic
apt-install: E:
apt-install: There are problems and -y was used without --force-yes
apt-install:
base-installer: error: exiting on error base-installer/kernel/failed-install
```
I fixed this by constantly pinging the archive mirror during installation, since ping isn't part of the gentoo base installation - I mounted my gentoo  root partition and using /bin/ping archive.ubuntu.com. All packets are lost since the archive doesn't respond to pings, but this seemed to help dns resolve the address.
I think this was because i have a dodgy network connection - elsewhere in the code I see this error
```

base-installer: Err http:/archive.ubuntu.com edgy-security Realease.gpg
base-installer:   Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (110 connection timed out)
```
This suggests to me that for some reason my laptop isn't resolving DNS correctly - it's resolving archive.ubuntu.com to 1.0.0.0.
Anyway if anyone else has this problem, hope this helps. It's been driving me nuts.

---

### Post by maxppp on 2007-02-21
Hi Guys, i followed the instructions and all worked well.

Although i want to use ubuntu in x-windows. So everytime i boot i just get prompted for my username/password, entering gets me to a command prompt. So i type 'startx' which loads a mouse pointer with a fuzzy black/white hatched wallpaper. Thats as far as it gets, any ideas?

Much obliged

EDIT: I managed to get back to the prompt after i left startx and there is a lot of font registration errors?

---

### Post by ACF1 on 2007-02-23
Can I use the method to install Ubuntu on the entire hardrive?  If so, will the final outcome be the same as if I had used the CD to install it?  Thanks.

---

### Post by tuxcantfly on 2007-04-29
here's an easier and better method I made:

[http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)

---

### Post by saurabh kakkar on 2007-06-20
hi
  i have just browsed through ur post its seems good but any of ur link is not working error msg is "page not 
found" well i have ubuntu 7.04 cd from whome i created the iso using alcohol now my cd drive is not working 
i want to know whether i can use this iso for Installing Ubuntu 7.04 also after browsing through the cd i found 
linux.bin 
initrd.gz 
can i use these files (if not plz post the link again as its broken now)
plz fix this link also [ http://newdos.yginfo.net/grubdos.htm]( http://newdos.yginfo.net/grubdos.htm) 

plz also provide alink for ur attached .zip file

---

### Post by tuxcantfly on 2007-08-07
> hi
i have just browsed through ur post its seems good but any of ur link is not working error msg is "page not
found" well i have ubuntu 7.04 cd from whome i created the iso using alcohol now my cd drive is not working
i want to know whether i can use this iso for Installing Ubuntu 7.04 also after browsing through the cd i found
linux.bin
initrd.gz
can i use these files (if not plz post the link again as its broken now)
plz fix this link also [http://newdos.yginfo.net/grubdos.htm](http://newdos.yginfo.net/grubdos.htm)

plz also provide alink for ur attached .zip file

Oh sorry for the broken link, I've moved the downloads and site page for the project, now known as UNetbootin (Ubuntu Netboot-based Installer) to [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by RTFishUL on 2007-08-16
what if I wanted to do a fresh install of ubuntu (already have it on), without a cd

---

### Post by boomcat on 2007-08-17
A simple non-CD installation would be very welcome. My problem with my first install was CD incompatibility between machines. I burned CDs on four different machines until I found one that would work on the target machine. Of the twelve CDs I burned (four physical drives, four software packages, two disk manufacturers) seven were defective in some manner or other. Some had defects noticed by the burning software, some passed THAT but would not boot, some passed and booted but had defects spotted by the Ubuntu opening screen CD checker.

---

### Post by tuxcantfly on 2007-08-23
> what if I wanted to do a fresh install of ubuntu (already have it on), without a cd

Use the UNetbootin Linux version; deb package available for download here: [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

> A simple non-CD installation would be very welcome

See above, UNetbootin will do the job for both Windows and Linux users with just a few clicks, and no scary commands.

---

### Post by Blessed_Coffee on 2007-11-29
Noob question...  :oops: I got the installer to load up, but I can't get it to install.  It continues to try and mount the CD drive.  How do I Download all the necessary files before or after loading the installer? :confused:

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:
[URL="http://www.len.ro/work/tools/life-to...d-i8000-1/view"]
http://www.len.ro/work/tools/life-to...d-i8000-1/view[/URL]

---

### Post by K7522 on 2008-02-06
Guide worked perfectly once I modified a few things.

For the most up to date version at Feb 6, 2008; [Gusty]("http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/").  

To clarify something that confused me, the two files you want to download 'linux.bin' and 'initrd.gz', as per the code below you want to remove '.bin' on the 'linux.bin' file, and leave 'initrd.gz' as is in your C:/boot/ directory.

```

title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz
```

---

### Post by DoctorDanger on 2008-02-27
Any idea why when I select Ubuntu Installer I get this:

> kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

Error 17: file not found

I am 100% certain that I downloaded the linux.bin file for Gutsy, dropped the extension and moved it to C:/boot.

EDIT:
It turns out that my boot partition was at (hd0,0), and my root directory was (hd0,1).

---

### Post by Godismyrock on 2008-05-10
None of those links to the files are working! Please help me! Someone send me them please!

---

### Post by xjosie729 on 2008-06-19
With this method, is it possible to not partition the drive first, and then when installing, use the whole drive?

---

### Post by techdude300 on 2008-07-09
> **Godismyrock said:**
> None of those links to the files are working! Please help me! Someone send me them please!
I can't get the link working either. I hope it gets fixed soon. I have no other option at the moment =(.

---

### Post by Dexterp37 on 2008-07-12
The two links:

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz)

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux)

---

### Post by slyde on 2008-10-28
I have an HP Pavilion that I'd like to try this on, the cdrom no longer reads anything, only question I have is can I use the entire disk instead of a partition, I only have a 10gb and windows etc. is using about 8gb, I'd like to remove xp completely and switch it to ubuntu only. I though about trying usb install but the laptop does not support booting from usb from what I can tell.

---

### Post by sadafrasheed on 2009-01-03
Can you have a look at 

[http://ubuntuforums.org/showthread.php?t=1029569](http://ubuntuforums.org/showthread.php?t=1029569)

and suggest something

---

### Post by slyde on 2009-01-06
I've never seen the partition options not show up, of course I've only needed the alternate disk once or twice. If you aren't too concerned with saving the data already on the drive I would say try something like pressing enter to accept defaults or attempt to blindly select the desired option, I didn't happen to catch if this was a laptop or desktop, if its a desktop I would suggest trying a different video card or display, or if it is a laptop then try an external display if at all possible, I would think if you can see the rest of the installer thought that would rule out the possibility of it being a display option, I would try kubuntu or xubuntu as well to see what happens with either of those. Maybe even try a previous version of the alternate disk, I have never heard of such a thing but I'll see if I can find anything.

---

### Post by aasdfasdfg on 2009-11-19
Has anyone done this recently? It seems like a lot of the posts here are old. My situation: I have the ISO, no CD drive, two hard drives in my computer: one running karmic, one completely empty and formatted to ext4. In the past, I merely copied the important files over from one hard drive to the other to get a new "linux install". This seems incorrect. So, I decided to download the ISO and try to figure something out.
It sounds like I could get this to work by pointing grub to the location of the linux.bin and initrd.gz files and then somehow setting the network install settings so that it pulls the files off of a local repository instead of the internet. Any ideas?
Lastly, I am really disappointed that ubuntu doesn't natively support people trying to install in this manner... I saw a post earlier in this thread giving a rationalization for it, but it was merely a rationalization.

---

### Post by darkksyde on 2009-11-20
Great tutorial, but doesn't wubi just do the same thing expect without effecting the partition tables

---

### Post by bdcanis on 2009-11-22
This is a pretty good tutorial. Except one problem. Im getting an error message when i boot up. I get the grub screen, and i click Ubuntu installer. Then it says "error 17: File not found" What does this mean and how do i fix it. Please help Im dying here ahaha. Thanks, also if i am missing a file could you point me in the direction.. im starting to think the linux.bin file i have isn't the right one.

---

### Post by phy4eveything on 2010-08-31
hay i tried to install ubuntu from my hard disk which already have mandriva but i found a massege like  
[COLOR="Blue"]switching to color from buffer device 80*30
initramfs[/COLOR]

what can i do 
i tried to install it by cd but my mandrive can not mount cd-rom
my bios can not recognize flash drive

---

### Post by sikander3786 on 2010-08-31
> **phy4eveything said:**
> hay i tried to install ubuntu from my hard disk which already have mandriva but i found a massege like  
[COLOR="Blue"]switching to color from buffer device 80*30
initramfs[/COLOR]

what can i do 
i tried to install it by cd but my mandrive can not mount cd-rom
my bios can not recognize flash drive

This one is outdated. Did you notice it is dated 2005. Not sure if it works with the new distros or new versions.

What you want to achieve? Installation wihout CD, USB etc? Better to start a new thread I think.

---

