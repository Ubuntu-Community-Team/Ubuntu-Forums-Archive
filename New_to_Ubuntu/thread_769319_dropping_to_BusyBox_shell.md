---
title: "dropping to BusyBox shell"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Solrac924 on 2008-04-26
ok, first off, i'm a newbie to Linux...period. i've heard great things about Ubuntu, & i'm awed at Compiz Fusion (thanks to youTube). so i recently got a new PC (old one fried) & was waiting for Hardy Heron to be released. After 22 hours of downloading i finally got it. 
   after a so-called "successful" install, i re-booted, saw GRUB, chose Ubuntu, & after 3 minutes, got nothing but a command line. i've re-booted, re-installed, & am aggravated.
   i keep getting: "check_root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/module/ ls /dev
ALERT /dev/disk/by-uuid/ceddc280... does not exist Dropping to shell"
   i've read many forums & have learned a little since. nufortunely, i gaven't progressed at all. when i enter "cat /proc/cmdline" i see the same UUID string.
   i've tried editing the line in GRUB putting "irqpoll" at the end with no luck. i've also tried "all_generic_ide" & have gotten no further. i tried "sudo update-initramfs -k 2.6.24-16-386 -c" in BusyBox but doesn't work, & can't update it in Terminal while using Live CD. 
   my menu.lst looks like:
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ceddc280-a12f-4a5d-b14e-a8178bdb6bfd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

   as for my setup, i've got an AMD64 X2 & am using a IDE hd (for Ubuntu) & SCSI hd (for Windows).
   please help. :frown:

---

### Post by mick8985 on 2008-04-26
Hmm, tricky one, looks like the kernel loads OK, but it cannot mount your hard drive. Your definately on the right track passing parameters to the kernel through grub. Try passing ide=nodma

---

### Post by Rocket2DMn on 2008-04-26
Try editing your boot line to
```
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=ceddc280-a12f-4a5d-b14e-a8178bdb6bfd ro splash acpi=off noapic
``` (removed quiet and added acpi=off and noapic).
If you find this works, you can edit menu.lst after installing to do it automatically and have it save that as the default (in case updates overwrite menu.lst)

Once you have the system installed:
```
gksudo gedit /boot/grub/menu.lst
```
then make the entry
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=ceddc280-a12f-4a5d-b14e-a8178bdb6bfd ro splash acpi=off noapic
initrd /boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

---

### Post by anewguy on 2008-04-26
There are other recent posts on the forum about this problem also.  They seem to center around a certain controller on the motherboard and either switching a setting to "raid" (even with just 1 drive) or moving a cable.  I'd search the forum, see if these make sense, and if not, come back and we'll see if we can help.

:)

---

### Post by Rocket2DMn on 2008-04-26
My theory is that it may have to do with JMicron support.

---

### Post by Solrac924 on 2008-04-26
alright, thanks guys for the advice! hopefully i can get this resolved today.

---

### Post by Solrac924 on 2008-04-26
ok, still nothing.
i'd hate to make this an all day project, but i'd like to see this running ASAP.
to mick8985 & Rocket2DMn, i give you thanks for trying. 
the "ide=nodma" trick got me nowhere, as well as the "acpi=off noapic". isn't that for ACPI read timeouts? 
to anewguy, i've read several posts in the last 24 hours. did you have a solution to contribute?
is there anything else i can try? anyone?! :(

---

### Post by Rocket2DMn on 2008-04-26
If it's not even getting to loading the system (the errors appear after GRUB), you may want to try reinstalling GRUB using the Super GRUB Disk.  It's possible the UUID on the drive changed when you modified it with the install, so GRUB may be looking in the wrong place for the drive.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
It's a nice little disc to have, it can be a little strange, but I think you can muddle your way through it and try a few different options.  The best option would be to just reinstall GRUB with it for the dual boot system and have it autodetect the installs.

---

### Post by Solrac924 on 2008-04-26
i agree i **need** to do something to have it autodetect the install. when the splash is "quiet" it is shown that "Mounting root file system" is not OK'd.
how can i re-install GRUB? neither 'update' nor 'install' are commands in BusyBox. those commands are disabled when using the LiveCD.
this is getting frustrating. i'll try that SuperGRUB & hope for the best. [-o<

---

### Post by Rocket2DMn on 2008-04-27
> **Solrac924 said:**
> i agree i **need** to do something to have it autodetect the install. when the splash is "quiet" it is shown that "Mounting root file system" is not OK'd.
how can i re-install GRUB? neither 'update' nor 'install' are commands in BusyBox. those commands are disabled when using the LiveCD.
this is getting frustrating. i'll try that SuperGRUB & hope for the best. [-o<

That is what the Super GRUB Disk is for.  You should download it, burn it to a disc, then boot from it on your Ubuntu computer.

---

### Post by mick8985 on 2008-04-27
You could try simply not using uuid's, 

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/hda1 ro splash 
initrd /boot/initrd.img-2.6.24-16-generic
quiet
savedefault

---

### Post by Solrac924 on 2008-04-27
i should've mentioned earlier that i've tried switching a setting to "raid" (i know that's worked for many others) but  i didn't see it anywhere in the CMOS/BIOS.

i've downloaded, burned, & ran from Super GRUB Disk but it didn't help a single bit. GRUB appeared like normal with the usual boot options. When choosing Ubuntu it dropped me to the same ole BusyBox.

i feel these are shots in the dark. aren't there troubleshooting steps where i can list files in particular folders & see what's missing?

i do thank you all & appreciate the support in the last 2 days. i do get the feeling of "Humanity towards others". i'm confident the issue will be resolved. :neutral:

---

### Post by Solrac924 on 2008-04-27
getting back to the orig prob, when i edit to show no splash, it shows "/dev/disk/by-uuid/(long code) does not exist". when booting with liveCD, i use the file manager (Nautilus) & click "File System" -> dev -> disk -> by-uuid & see the file that matches that long code. i'm not sure if this is a problem, but the filesize shows 0 bytes!
now when i go to "File System" -> dev, i see hdb, hdb1, hdb2, & hdb5. all these are also 0 bytes.
is this what's causing the problem? :-k

---

### Post by mick8985 on 2008-04-27
You obviously have created a custom partition table, what is each partition used for, and what file systems have you used for each partition?

---

### Post by Solrac924 on 2008-04-27
no, i didn't create any custom partition table. i just chose my IDE drive during the install. 

i have 2 drives:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86129f14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765       10079    74822737+   7  HPFS/NTFS
/dev/sda3           10080       19457    75328785    c  W95 FAT32 (LBA)

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1abd1abc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6994    56179273+  83  Linux
/dev/hdb2            6995        7297     2433847+   5  Extended
/dev/hdb5            6995        7297     2433816   82  Linux swap / Solaris

for whatever reason, the installer didn't mount the root file system properly. i didn't do anything manually. :(
going back to the filesize, is that normal?

---

### Post by mick8985 on 2008-04-27
Yes thats normal, I don't know the details but basically those are just virtual files that pretend to be a device or filesystem so they have a location in userspace. Have you tried using /dev/hdb1 instead of the uuid like I suggested? (also I didn't realise the default options created 3 partitions seems odd, I am sure the last time I picked defaults it made 2 partitions, but I probably have done that since feisty)

---

### Post by Solrac924 on 2008-04-27
yes, i've tried editing the command line to "root=/dev/hdb1", but nogo. thanks btw. 
in a terminal window, i entered "**sudo fdisk -l**" & "**sudo blkid**" & everything seems to be correct. i tried mounting using "**modprobe ide-generic**" but that "*operation not (is) permitted*". nothing seems to work.
should i try installing Gutsy Gibbon?!

---

### Post by janmartin on 2008-04-27
I had the same BusyBox error message when trying to install 8.04 using the alternate CD.

Try the brute force option: Reinstall. 
Nothing to loose and it worked for me.

Run "check CD integrity" (or something like this) before installing again.

Does it work?

---

### Post by Solrac924 on 2008-04-27
ok, well, i've downloaded Gutsy but the burn was no good. Even the 'Check CD for defects" crashed!? :-?
as for my Heron CD, it shows "Check finished: no errors found". that happens to be the only thing that went right in the last 48 hours, cause the 3rd re-install **still** leads me to BusyBox. ](*,)
this ordeal is not a good first impression, ya think? :roll:

---

### Post by mick8985 on 2008-04-27
I know, this isn't going well for you is it? I always get really gutted when people get their first taste of linux and it is like this, because this really isn't representative of linux in the whole. My first gut suggestion is try Debian. You seem to have picked up alot very quickly so you needn't worry about it being too hard, its very much the same as ubuntu, so much so that almost all the advice you recieve hear at ubuntu forums will be applicable. I fear if you keep on at trying to get around this problem you'll soon grow bored of it and go back to windows and we can't have that ;)

---

### Post by Solrac924 on 2008-04-27
well, i just have to give ya a thanks for that post. i'm not gonna give up. 
yeah, i have learned a lot. i'm not a microsoft fan by **any** means, nor am i a hater, but this Linux Distro seems fun. i've heard a little here & there on digg.com enough to become interested in Ubuntu. from seeing videos of Compiz Fusion & Wine, i was sold on trying it out. i hope to fix this bug real soon. hopefully there's a reader out there with the solution. someday i'd like be a part of helping others out, then spread the word & see it explode like i did with Mozilla "Phoenix" a few years ago. this is something i believe in. 
yeah, i'm a little discouraged, but once i understand this OS better, i'll feel confident with it. i see this is as a learning experience.

---

### Post by mick8985 on 2008-04-27
Yeah I think digg has had a massive effect on linux adoption. 
In a way you learn alot more when things don't work than when they do, If you had everything work fine then you probably wouldn't have learned an awful lot. Anyways I have a little idea that might get it working as a **temporary** solution. I'll post it in the morning too tired now.

---

### Post by Solrac924 on 2008-04-28
ok, just a little report on what i did late last night. i got an idea from something that was said earlier...i tried my own custom partition. on my IDE 60GB drive, i allocated 40GB to /home (ext3), 15GB to / (ext3), & 5GB to swap. i figured the installer wasn't mounting the file system when it partitioned on it's own, but i struck out again. 
i also read that others have gotten it fixed by reverting to a previous kernal. i'm not sure if i can update anything within BusyBox. perhaps i should re-try burning 7.10 again & upgrade to 8.04 unless there's a better idea. :confused:

---

### Post by Genesius on 2008-04-28
Not sure if this'll help, but what the heck. . .

Had similar problems trying to run a LiveCD on my new PC, no options helped at all. Just kept dropping to BusyBox. Finally downloaded the Alternate install CD and that worked fine. Not sure why, but maybe if you reinstall with the alternate CD it'll straighten things out.

Stranger things have happened. . .

---

### Post by Solrac924 on 2008-04-28
ok, day 4. still no real progress, but i was reading around & found something interesting. adding the following boot parameters somehow mounts the filesystem: "noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317". although it gets as far as loading the wallpaper & mousepointer, it locks up from there. no icons, no taskbar, nothing. is this a fix for anyone else?

---

### Post by Solrac924 on 2008-04-29
Ok, last post on thread. i never did get enough help to resolve this bug for Hardy Heron. i did, however, successfully install Gutsy Gibbon & it boots up like a charm. i am happy & can rest a bit. 8)
the graphics are goofy towards the bottom (even after 205 updates) but that'll be reported in another thread later. although i'm a little reluctant, i'll upgrade to Heron someday.;-)

---

### Post by A J on 2008-11-11
Hi,
Would you please explain how did you fix it ??!!

Cause I'm facing same problem in ubuntu 8.10

Thank you

---

### Post by endokendo on 2008-11-15
Hello everyone, I am getting a similar error message as well. I am trying to install Ubuntu 8.10 onto an old desktop PC. Specs: Intel Celeron, speed? not sure, 256 MB RAM, originally had Windows ME loaded onto it. Upon rebooting the computer and having the Ubuntu 8.10 bootable CD in the drive, I get to the start screen and I proceed to Install Ubuntu. After several minutes, I get the following messages:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

I have read on the Ubuntu forums and followed everyone's advice, and I pressed F6 at the start up screen, got rid of the "quiet" line and replaced it with boot=break

Then I waited a few minutes, then did the modprobe piix, then enter, then exit, then enter, and now I have the following error message:

cp: cannot create '/root/var/log/': No such file or directory
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


I am at a lost with this Ubuntu install on this old desktop computer.

Can someone please help me? I have tried installing Xubuntu, Ubuntu 8.04 LTS, adn Ubuntu 8.10 on this computer and I get the same error messages throughout. I have used these exact same disks on other laptop computers and installation was successful.


Thanks to everyone in advance for helping me out!

---

### Post by Ryadt on 2008-11-15
Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)

---

### Post by endokendo on 2008-11-15
Ryadt, thanks for your reply, I will try the link that you sent me.

In the meanwhile, at the start up screen, I followed your instructions:

Hit F6, delete "quiet place" and entered "all_generic_ide" (without the quotes)

I then pressed enter, waited a few minutes, and now I still have the same error message:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


Your thoughts? Thanks again for your help! I will try the link with regards to going into the kernel later on....

---

### Post by Ryadt on 2008-11-15
Have a look at zorael's post in this thread: [http://ubuntuforums.org/showthread.php?t=895273](http://ubuntuforums.org/showthread.php?t=895273)
Try to see if it helps you out.

---

### Post by endokendo on 2008-11-16
Ryadt, thank you for your reply. I have followed the instructions on the link you sent me, tried to do a bootable CD install with Ubuntu 8.10, got the BusyBox error message again, ejected the CD, pressed enter, waited a few minutes, and then I got the BusyBox error message again. I restarted the computer, loaded Windows ME, did the Wubi installer now, it was going well, and then I got the BusyBox error message again. This time there was no bootable Ubuntu CD in the CD-ROM tray.

hmmmmmmm, maybe I just can't install Ubuntu on this old machine?

---

### Post by sloppyc on 2008-12-15
I too am getting the Busybox problem.  I've tried a few of the suggestions here (using F6 at the initial screen from the 8.10 CD, adding "pci-nomsi", "all_generic_ide", replacing the UUID with "/dev/sda1"...), but to no avail.  I'm using the guided partitioning using the whole disk.

MSI motherboard (K266, I believe) with a 1 GHz Athlon CPU.  It ran Vista fine.  It runs 8.04 fine.  But when I try to install (ie. boot from 8.10 CD) or upgrade (installed 8.04, chose to upgrade distro, unable to boot afterwards) to 8.10, no deal.

EDIT:  I should add that I have an IDE drive, not SATA.  I did notice that the HDD LED never lights up on the front of my PC, and when I was booting in failsafe mode it would hang when trying to find the root partition (I can't recall the precise text on that line).  Furthermore I can still choose to boot from the pre-upgrade Kubuntu options just fine.  And when I do, I get KDE4, etc, so aside from the older kernel, am I really missing anything?

---

