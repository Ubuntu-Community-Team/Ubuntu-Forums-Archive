---
title: "[SOLVED] Help with grub, installing ubuntu on a seperate hard drive"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by tuffguy45 on 2008-09-11
I have XP installed on a 30gb hard drive on my computer and have an unformated 8gb hard drive that I installed ubuntu on last night. I was assuming that grub would look for XP on my other hard drive but I'm guessing it didn't. So now it just automatically boots into ubuntu whenever I reboot. I know it involves modifying the grub file but I'm not really sure how the syntax works for it, I tried to do this once with fedora and I completely messed up my computer to where it wouldn't even boot either one.

---

### Post by overdrank on 2008-09-11
> **tuffguy45 said:**
> I have XP installed on a 30gb hard drive on my computer and have an unformated 8gb hard drive that I installed ubuntu on last night. I was assuming that grub would look for XP on my other hard drive but I'm guessing it didn't. So now it just automatically boots into ubuntu whenever I reboot. I know it involves modifying the grub file but I'm not really sure how the syntax works for it, I tried to do this once with fedora and I completely messed up my computer to where it wouldn't even boot either one.

Hi and welcome, first of all make a **BACK Up** of the grub menu list :)
This link has some good info on adding windows to the menu list
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by tuffguy45 on 2008-09-11
Thank you, I'm at work so I can't get to my pc at the house right now. However, do I just need to add

title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

to the grub list file and change the hd0 to hd1?

---

### Post by bobnutfield on 2008-09-11
This would probably work for you if both drives are IDE, however, it is possible you might need to add:

> map (hd0,1) (hd1,0)
> map (hd1,0) (hd0,1)

This is sometimes, but not always, required when using two separate drives.
I have a similar setup on my desktop, with Windows and two other Linux distros on one SATA drive and Ubuntu and Debian on a separate IDE drive, but I am able to boot Windows just fine with a similar entry without having to use the map lines.

---

### Post by tuffguy45 on 2008-09-11
Those drives where put in WELL before 2003 so I'm willing to be 99.9% sure that they are IDE. I'll have to wait to get home though, just for my personal edification why do you have to use the map command on sata drives and not IDE?

---

### Post by bobnutfield on 2008-09-11
I am sure some one else will chime in to answer that more technically, but I am assuming it is because they are differnet bus connections.  I personally have never had to use those lines, but I have read a number of posts in various forums where it has been necessary to get Windows to boot.  In any case, you can certainly try your entry and see if it will boot, if not then you can add the map lines.

---

### Post by caljohnsmith on 2008-09-11
> **bobnutfield said:**
> This would probably work for you if both drives are IDE, however, it is possible you might need to add:
```
map (hd0,1) (hd1,0) 
map (hd1,0) (hd0,1) 

```
This is sometimes, but not always, required when using two separate drives.
I have a similar setup on my desktop, with Windows and two other Linux distros on one SATA drive and Ubuntu and Debian on a separate IDE drive, but I am able to boot Windows just fine with a similar entry without having to use the map lines.
Is that possibly a typo, botnutfield? Because I don't believe you can "map" partitions with Grub, i.e. (hd1,0) instead of (hd1); you have to map the drives themselves. If your Windows is on (hd1) instead of (hd0), I believe the correct syntax is:
```
title Windows 
root (hd1,X)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Of course "X" needs to be the Windows partition, so "X" would be 0 if Windows is on the first partition of the 2nd HDD.

---

### Post by gregphil on 2008-09-11
We need a little more information.

Was Windows Xp on the first partion of the active boot disk? (answer = yes)

After you added the new disk, was Windows still on the first partition of the active boot disk?  

When you installed ubuntu, which disk was the active boot disk?

Ubuntu 8.04 will have grub will install itself on the MBR of the first partion of the active boot disk unless you take some special steps.  This is normally what you might want, but it does over-write the NT bootloder, if you install with the BIOS set so the boot disk is still the Windows boot disk.  However in this case Grub will notice the Windows installation and should add an option to the grub menu to select ubuntu or Windows during the text mode boot (startup defaults to ubuntu after a few seconds).

However other things can happen, by intent or by accident.  Did you per chance change the BIOS boot order recently?  Ubuntu has a strange way of re-assigning disk names (like /dev/hda, /dev/sda, /dev/sdb etc) based on which drive is marked as the active boot partion.  Since the BIOS can be used to change the active boot disk, it can lead to the ubuntu disk names changing (and screwing up the grub conf file mappings.

Since Windows needs to boot off the first partion of the active disk the mapping commands mentioned above MAY be needed to remap the windows drive to be the first disk, AND mark it as active.

---

### Post by tuffguy45 on 2008-09-12
I'm assuming since I used the XP utility on the disc to delete off everything and just install it on the 30gb hard disk with no partitioning that it is in the first partition. 

When that first disk was added I was still running ME and it has gone through countless different OS's since then. To answer your question though as far as I know windows location on the 30gb hard disk did not change in any way.

After installing Ubuntu it made the 8gb hard disk the active one instead of the 30gb one, I think. I'm only guessing this because its the only one that boots however Ubuntu does notice that fact that there is another hard disk there and all my windows files are on it.

I have not changed the BIOS boot order recently either... The boot order in the BIOS is still set (as far as I know because I didn't change it but Ubuntu could have changed it since I didn't check) as having the 30gb hard drive as the first hard disk device it boots from (after the cdrom/floppy of course)

---

### Post by caljohnsmith on 2008-09-12
I'm confident we can get your Windows to boot from the Grub menu, but we need some more info to help you. Please boot into Ubuntu, open a terminal, and do the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Post the output of those commands, and we can most likely get your Windows booting without a problem.

---

### Post by bobnutfield on 2008-09-12
> **caljohnsmith said:**
> Is that possibly a typo, botnutfield? Because I don't believe you can "map" partitions with Grub, i.e. (hd1,0) instead of (hd1); you have to map the drives themselves. If your Windows is on (hd1) instead of (hd0), I believe the correct syntax is:
```
title Windows 
root (hd1,X)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Of course "X" needs to be the Windows partition, so "X" would be 0 if Windows is on the first partition of the 2nd HDD.

You are abolutely correct and I should have known better.  I have never had to map my drives to get Windows to boot properly, so I was writing from memory.  Sorry for the bad info.

---

### Post by tuffguy45 on 2008-09-12
```
Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders, total 12594960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b314b30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    11936294     5968116   83  Linux
/dev/sda2        11936295    12594959      329332+   5  Extended
/dev/sda5        11936358    12594959      329301   82  Linux swap / Solaris

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b754b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    66027149    33013543+   7  HPFS/NTFS
sam@room:~$ 
sam@room:~$ 
sam@room:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by caljohnsmith on 2008-09-13
Tuffguy45l, if you can boot OK into Ubuntu, then your BIOS must be set to boot your Ubuntu drive before your Windows drive, because your Ubuntu entries in menu.lst use (hd0), which is the boot drive. To boot Windows from Grub, all you should need to do is add that entry I gave in post #7. Specifically here's how:
```
gksudo gedit /boot/grub/menu.lst &
```
That will pull up your Grub's menu.lst, so at the bottom, just add:
```
title Windows 
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Save, reboot, and you should be able to boot Windows now from Grub. If you run into any problems/errors, let me know. Otherwise let us know how it goes. :)

---

### Post by tuffguy45 on 2008-09-13
It still boots straight into Ubuntu, perhaps I didn't edit the file right? Here is the edited version of my menu.lst file

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b6ae1e0e-afc0-47a0-b5b5-21c4efe4e858 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows 
root 		(hd1,0)
map        	(hd0) (hd1)
map        	(hd1) (hd0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-09-13
In that line near the top of your menu.lst where it says "hiddenmenu", put a pound sign in front of it to comment it out:
```
#hiddenmenu
```
Also, you may want to increase the time that Grub allows you to choose before Grub boots the default OS, if that is OK then change "timeout 3" to:
```
timeout 10
```
Or any value that you want, the value is in seconds. Let me know how it goes.

---

### Post by egalvan on 2008-09-13
Yes, you should comment out that "hiddenmenu" line as the previous poster stated.
You can use the ESC key to see the menu, but that way is easier.

Further, I also un-comment the "pretty colours"

```
# Pretty colours
#color cyan/blue white/blue
```

to

```
# Pretty colours
color cyan/blue white/blue
```

Or add a blinking line, to help see what is selected...(it's what I use, my eyes are old, and need the help :) )

```
# Pretty colours
color cyan/blue blink-white/blue
```

I also raise the delay to 20 seconds... that gives me time to make sure I'm booting what I want (I have a few more options).

Lots more to change about, and that's what so great about the GNU/linux universe: the choices.

---

### Post by tuffguy45 on 2008-09-13
It gives me the window but when I use the "Windows" option it says something to the effect of:

"NTLDR is missing preess CAD to restart"

I've heard of this before, it has something to do with the windows bootloader right?

---

### Post by Bucky Ball on 2008-09-13
[quote=tuffguy45]I've heard of this before, it has something to do with the windows bootloader right?[/quote]

You're more or less tricking windoze into thinking it is on the first physical drive. SATA seems to always wind up before IDE, therefore when you install Ubuntu (which doesn't give a toss), it sets the IDE as last in the chain in my experience (eg sdc instead of what windoze would understand as first, sda or hd0 if you get my drift). Had the same problem with my desktop with IDE for OSs and 3 SATA drives.

---

### Post by tuffguy45 on 2008-09-13
I'm not really sure what you mean after e.g. but I get the part before. So what do I have to do to fix it?

---

### Post by caljohnsmith on 2008-09-13
> **tuffguy45 said:**
> It gives me the window but when I use the "Windows" option it says something to the effect of:

"NTLDR is missing preess CAD to restart"

I've heard of this before, it has something to do with the windows bootloader right?
Yes, the ntldr is a file Windows needs to boot. If you go into your BIOS settings and make your Windows drive the first in the boot order, does Windows boot OK that way? That's important to know before we troubleshoot your problem further.

---

### Post by Bucky Ball on 2008-09-13
eg sdc instead of what windoze would understand as first, sda or hd0 if you get my drift

sdc = Hard drive 3; sda = hard drive 1. Letters = numbers. Get me?

The instructions caljohnsmith gave before should have worked, I'll have another look at mine.

*Update: This is mine adjusted to suit your setup. Don't know if it will make any difference, but may be worth a try:

```
title           Microsoft Windoze
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```Good luck and let us know how you go.

---

### Post by tuffguy45 on 2008-09-13
The way the BIOS has the drives set up is really strange, the linux drive is set to primary master with no slave and the dvd drive is set as the secondary master with the windows drive set as secondary slave with it set to boot both masters. I set it to just boot from the secondary and It still gives me the "NTLDR is missing press CAD to restart" I'm not sure if thats what I was supposed to do to try to boot from my windows drive but I think that did it since the way it was set it always gave me the menu and this time it didn't and just went straight to the error message.

This is a little alarming though since it would appear as if I have no way to get to my windows OS. However, I'll keep going, if it came down to it it wouldn't be the first time I've had to reinstall windows because I couldn't get it to boot.

---

### Post by Bucky Ball on 2008-09-13
You could try this:

[www.supergrubdisk.org](www.supergrubdisk.org)

... download, make a cd and boot from it. Your NTLDR should still be in there, no worries, and if it is supergrubdisk will probably find it. We just can't find it! Probably quite simple. caljohnsmith might have some other ideas.

---

### Post by unutbu on 2008-09-13
Try this:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

---

### Post by tuffguy45 on 2008-09-13
Alright, I'll give it a bit and see if he posts before jumping on making another boot disk. I have a stack about 20 or 30 discs from all the different distros and boot disks I've used. (I've never tried to dual boot like this before)

---

### Post by caljohnsmith on 2008-09-13
> **tuffguy45 said:**
> The way the BIOS has the drives set up is really strange, the linux drive is set to primary master with no slave and the dvd drive is set as the secondary master with the windows drive set as secondary slave with it set to boot both masters. I set it to just boot from the secondary and It still gives me the "NTLDR is missing press CAD to restart" I'm not sure if thats what I was supposed to do to try to boot from my windows drive but I think that did it since the way it was set it always gave me the menu and this time it didn't and just went straight to the error message.
Yes, that most likely means your Windows is the culprit and not Grub. Is there any way you could swap your Windows HDD into another computer just to see if it boots? Or can you swap it into the slot that the Ubuntu drive is in now? (You said before that you were 99% sure they were both IDE). 

Also, in Ubuntu, please mount your Windows drive and post the contents of its root directory so we can see:
```
sudo umount /dev/sdb1  [COLOR="Blue"][don't worry if it gives you an error saying it is not mounted, this is just to make sure][/COLOR]
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```

---

### Post by Bucky Ball on 2008-09-13
> 99% sure they were both IDE

That wouldn't by any chance mean you would need to map the other drive the opposite way? They are not both ending up as hd0? Forgive me if that suggestion is downright crazy! :s

---

### Post by unutbu on 2008-09-13
tuffguy45, sorry for jumping in. Please follow caljohnsmith's advice first. He is taking a more careful approach.

---

### Post by tuffguy45 on 2008-09-13
sam@room:~$ sudo umount /dev/sdb1
[sudo] password for sam: 
umount: /dev/sdb1: not mounted
sam@room:~$ sudo mount /dev/sdb1 /mnt
sam@room:~$ ls -l /mnt
total 981501
drwxrwxrwx 1 root root      4096 2007-09-13 21:14 aircrack-ng-win-0.9.1
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 AUTOEXEC.BAT
drwxrwxrwx 1 root root      4096 2008-09-03 12:21 Config.Msi
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 CONFIG.SYS
drwxrwxrwx 1 root root         0 2007-08-31 20:56 DELL
drwxrwxrwx 1 root root      4096 2007-11-12 22:09 Documents and Settings
-rwxrwxrwx 1 root root 400936960 2008-09-09 23:14 hiberfil.sys
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 IO.SYS
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 MSDOS.SYS
drwxrwxrwx 1 root root         0 2007-09-24 20:48 OpenSA
-rwxrwxrwx 1 root root 603979776 2008-09-09 23:14 pagefile.sys
drwxrwxrwx 1 root root      8192 2008-07-30 23:33 Program Files
drwxrwxrwx 1 root root         0 2007-08-31 21:11 RECYCLER
-rwxrwxrwx 2 root root       268 2007-08-31 21:46 sqmdata00.sqm
-rwxrwxrwx 2 root root       244 2007-08-31 21:46 sqmnoopt00.sqm
drwxrwxrwx 1 root root      4096 2007-08-31 21:07 System Volume Information
drwxrwxrwx 1 root root    114688 2008-09-09 23:15 WINDOWS

---

### Post by caljohnsmith on 2008-09-13
> **tuffguy45 said:**
> sam@room:~$ sudo umount /dev/sdb1
[sudo] password for sam: 
umount: /dev/sdb1: not mounted
sam@room:~$ sudo mount /dev/sdb1 /mnt
sam@room:~$ ls -l /mnt
total 981501
drwxrwxrwx 1 root root      4096 2007-09-13 21:14 aircrack-ng-win-0.9.1
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 AUTOEXEC.BAT
drwxrwxrwx 1 root root      4096 2008-09-03 12:21 Config.Msi
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 CONFIG.SYS
drwxrwxrwx 1 root root         0 2007-08-31 20:56 DELL
drwxrwxrwx 1 root root      4096 2007-11-12 22:09 Documents and Settings
-rwxrwxrwx 1 root root 400936960 2008-09-09 23:14 hiberfil.sys
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 IO.SYS
-rwxrwxrwx 1 root root         0 2007-08-31 20:55 MSDOS.SYS
drwxrwxrwx 1 root root         0 2007-09-24 20:48 OpenSA
-rwxrwxrwx 1 root root 603979776 2008-09-09 23:14 pagefile.sys
drwxrwxrwx 1 root root      8192 2008-07-30 23:33 Program Files
drwxrwxrwx 1 root root         0 2007-08-31 21:11 RECYCLER
-rwxrwxrwx 2 root root       268 2007-08-31 21:46 sqmdata00.sqm
-rwxrwxrwx 2 root root       244 2007-08-31 21:46 sqmnoopt00.sqm
drwxrwxrwx 1 root root      4096 2007-08-31 21:07 System Volume Information
drwxrwxrwx 1 root root    114688 2008-09-09 23:15 WINDOWS
It looks like you are missing all your Windows boot files:
```
boot.ini
ntldr
NTDETECT.COM

```
I'm not sure how that could have happened, but I've attached those boot files to this post; just download them, unzip them, and put them in your Windows directory. To do that, first save the attached file to your desktop, then do the following from the terminal:
```
cd ~/Desktop
tar xvf "Windows boot files.tar.gz"
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /mnt
sudo mv boot.ini /mnt
sudo mv NTDETECT.COM /mnt
sudo mv ntldr /mnt
```
Reboot, and let us know what new errors you get (if any).

---

### Post by caljohnsmith on 2008-09-13
> **Bucky Ball said:**
> That wouldn't by any chance mean you would need to map the other drive the opposite way? They are not both ending up as hd0? Forgive me if that suggestion is downright crazy! :s
Using the "map" syntax with Grub can be used to make the second HDD in the boot order appear like it is the first HDD in the boot order, which is typically necessary to boot Windows. To my knowledge it doesn't make any difference whether both HDDs are IDE; in fact they can be any mixture of IDE and SATA--I believe all that matters to Grub is the boot order. :)

---

### Post by tuffguy45 on 2008-09-13
That did it, thanks everyone for your help. I especially appreciate the commands for terminal its humbling to go from having a pretty good idea about windows to going to absolutely nothing on linux.

I have a final question, I'm installing ubuntu on a laptop for school for programming but its a one hard drive system and I was just going to partition 10gb or so to use for ubuntu.

I've heard emacs and vi are good programming tools can you give me a link to some information on those or at least a link to a board on the forum for someone to ask about some literature for programming on ubuntu? When I was on fedora I just used eclipse...

---

### Post by bobnutfield on 2008-09-13
caljohnsmith,

Excellent.  Great detective work.  This is one to keep.

---

### Post by unutbu on 2008-09-13
tuffguy45, I love emacs. It's great for searching, replacing, recording and repeating key strokes, splitting windows, file management, diff'ing files and whole directories, and giving you access to a shell without leaving the editor. 

It has a somewhat steep learning curve, but if you stick with it, it will serve you well.

To get nice looking ttf fonts to work with emacs, go to Alexandre Vassalotti's page
[http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/](http://peadrop.com/blog/2007/09/17/pretty-emacs-reloaded/)
to install emacs-snapshot. 

Once it is installed, type
```

emacs

```
Then Ctrl-h Ctrl-h t. This will take you to emacs' built-in tutorial. 
If you have any questions, start a new thread, post here to notify me, and I'll try to help.
Enjoy.

---

### Post by gregphil on 2008-09-13
To tufguy45

You might want to look at the editors that come with the operating system these days.  I too spent *many* years using terminal based editors like emacs, but times have changed.  Now GUI editors are everywhere and most are *much* easier to use than vi or emacs.   GUI editors are separate applications and have their own window, instead of requiring a terminal window to run in.  They are much more flexible, you can pick the fonts and colors etc.

If you install ubuntu try "gedit"
If you install kubuntu try "kedit" or the fancier program editor "kate"

If you REALLY want to stick with a terminal based editor I would recommend you use the package manager to install "ne"  (the Nice Editor) which runs in a console window (so it is text based).  It has most of the modern key mappings and features, including a text based pull-down menu across the top of the screen (which must have been a neat trick to program).  Once installed just open a console (terminal) window and type ne.  (Alt-Q quits)

Good Luck.

---

### Post by tuffguy45 on 2008-09-13
I'm having problems getting emacs to install I'm getting a "C compiler cannot create executables" error.

I made a topic on the programming board...

[http://ubuntuforums.org/showthread.php?p=5785420#post5785420](http://ubuntuforums.org/showthread.php?p=5785420#post5785420)

---

