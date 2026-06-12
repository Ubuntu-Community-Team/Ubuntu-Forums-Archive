---
title: "Can't get back to my Windows XP"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by serenity_blu on 2008-08-30
Okay, so I decided to try out Linux Ubuntu tonight, but I had no idea what I was getting into. I do not know and I do not LIKE programming. That is exactly what Ubuntu is all about.

So, I want to get back to Windows XP and uninstall Linux Ubuntu. Just one problem. I cannot find any way at all to access that partition. 

I thought maybe going into Setup (F2) or Boot Menu (F12) might help, but alas, NEITHER OF THOSE DOES ANYTHING ANYMORE. No option whether to boot Ubuntu or XP; it just asks me which boot of Ubuntu I want to do.

I got really desperate and tried to just reset my hard drive to factory settings like I had to a few months ago for an unrelated problem. I forget if it's Ctrl-F11 or Alt-F11, that accesses that, but it doesn't matter, because neither of those worked either.

Please give me a detailed walkthrough for how to accomplish this. I'm sure Ubuntu is a fine operating system, BUT I WANT OUT OF IT.

Thank you.

---

### Post by gmxgeek on 2008-08-30
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

follow those instructions to the T, and you will have the option of booting into windows

actually, before you do that, please type this in a terminal and copy and paste the output
```

cat /boot/grub/menu.lst

```

---

### Post by serenity_blu on 2008-08-30
I haven't checked the link yet, but wow, talk about a quick response. I was literally at this moment saying out loud to myself "it's 2 in the morning, I'm not going to get a response till tomorrow" and as it refreshed, hey PRESTO! a response.

Hopefully this works, I'll let ya know after I try. Either way, thanks!




--------------

Oh, okay, it outputted an awful lot, I dunno if it's all relevant:

[I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=39f930de-6313-4362-b64d-36ffaf71ec15 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39f930de-6313-4362-b64d-36ffaf71ec15 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39f930de-6313-4362-b64d-36ffaf71ec15 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/I]

---

### Post by gmxgeek on 2008-08-30
Please post the output first. It might not be necesary to reinstall grub, only edit it

---

### Post by cdtech on 2008-08-30
You'll need to use the "Live CD" to run the program "gparted" to reformat the partition that Ubuntu was install on. Reformat to a file system that Window's can recognize, such as vfat. You'll need your Window's install disc to access the recovery mode and "fixmbr" to re install the MBR for Window's.

---

### Post by gmxgeek on 2008-08-30
Are you trying to completely kill ubuntu, or just have the option of windows or ubuntu?

---

### Post by szymon_g on 2008-08-30
> **serenity_blu said:**
> I do not know and I do not LIKE programming. That is exactly what Ubuntu is all about.

ekhm, wtf :?
may i ask: when you have been (in ubuntu) enforced to write program (or a script)?

---

### Post by serenity_blu on 2008-08-30
I'm trying to completely kill Ubuntu. I want my Windows back. Like I said, I'm not a big fan of programming, and I hate not being able to use my computer the way I want, which is exactly the situation I'm in at the moment.

---

### Post by scotcella on 2008-08-30
sounds like you might have formatted over your XP.

Do you still have the original XP Cd's? You shouldn't have a problem with reinstalling it again. 

Sometimes when your computer fires up you press F2 or F10/12 what ever gets into your bios settings or what ever its called..  you shouldn't press it once.. you should keep pressing it until you see a screen come up. That often helps.

Another thought, when you reinstall XP again you could dual boot with ubuntu for a while and try ubuntu when you have the time and get to know it's inner workingsand so forth. While you are still using your fully function XP OS. No one learnt how to use XP overnight, it's a learning process and Ubuntu is the same.

If you don't have any of your original Cd's, I can't help you with this but I am sure another poster with more advanced knowledgemight be able to help you out.

Good luck! Hope it works in your favour

---

### Post by swoll1980 on 2008-08-30
```
sudo gedit /boot/grub/menu.list
```
you should have a sequence like this in there

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

If you don't add it. Make sure there's no # in front of it also

---

### Post by gmxgeek on 2008-08-30
In that case, follow cdtech's instructions. Get your ubuntu cd, and boot to livecd. Launch qtparted and reformat your ubuntu partition to vfat, ntfs, or fat32, something windows can recognize. Then apply those changes, and reboot. This time get out your windows install or recovery cd, and look for an option that says fix master boot record, or if you can get a command prompt, type in fixmbr.

reboot and windows should be all back.

good luck!

*Note* This WILL completely kill ubuntu.

---

### Post by serenity_blu on 2008-08-30
I wouldn't mind dual-booting with both, but at the moment I can't access XP at all, and that's what has got me on edge. I wouldn't mind learning to use Ubuntu as long as I still had access to my nice, cozy, familiar Windows.

---

### Post by szymon_g on 2008-08-30
maybe i'm blind, but it looks that you have no windows installed on harddisk o_O. to be sure, paste

cat /etc/fstab

and 

df -h

//////
it seems that i'm late ;p

---

### Post by gmxgeek on 2008-08-30
yeah i started to notice that. ubuntu is installed at hd0,0...

you might have overriden windows, which would explain its absence

---

### Post by swoll1980 on 2008-08-30
:(

---

### Post by serenity_blu on 2008-08-30
Gah, I certainly hope I didn't do that. I distinctly remember making the partitions when I installed Ubuntu. It was like 42% of the hard drive for XP and 58% for Ubuntu. 

It wouldn't be a HUGE deal if I did lose my XP. I can always reinstall using all the info you guys have given me. However, re-downloading all my music and (especially) my shows and movies... those take a long time to get. Bah. Oh well, I guess I only have myself to blame for this screwup.

Thanks all of you for such quick responses. I didn't expect to get anything at all till tomorrow at the earliest.

---

### Post by gmxgeek on 2008-08-30
There may be hope yet! Can you post the above requested outputs?

---

### Post by DemonBob on 2008-08-30
Yes please post the output of 


fdisk -l

---

### Post by serenity_blu on 2008-08-30
> **DemonBob said:**
> Yes please post the output of 


fdisk -l

Inputting that gives me absolutely nothing.

---

### Post by gmxgeek on 2008-08-30
```

sudo fdisk -l

```

---

### Post by swoll1980 on 2008-08-30
> **serenity_blu said:**
>  However, re-downloading all my music and (especially) my shows and movies... those take a long time to get.

I don't like to preach, but always do a backup ecspecialy when your new to this kind of stuff, but even if you know what your doing "an ounce of prevention is worth a pound of cure" as my dad always said

---

### Post by DemonBob on 2008-08-30
i'm sorry, try

sudo fdisk -l

---

### Post by serenity_blu on 2008-08-30
> **szymon_g said:**
> maybe i'm blind, but it looks that you have no windows installed on harddisk o_O. to be sure, paste

cat /etc/fstab

and 

df -h

//////
it seems that i'm late ;p

For cat /etc/fstab:

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39f930de-6313-4362-b64d-36ffaf71ec15 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=13a14d05-5fe3-4f94-b9ff-8bebeb0ab4da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
[/I]

And for df -h:

[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             226G  2.3G  212G   2% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   48K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      226G  2.3G  212G   2% /home/joel/.gvfs
/dev/scd0             695M  695M     0 100% /media/cdrom0
[/I]


And for sudo fdisk -l:

[I]Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29638   238067203+  83  Linux
/dev/sda2           29639       30394     6072570    5  Extended
/dev/sda5           29639       30394     6072538+  82  Linux swap / Solaris
[/I]

---

### Post by gmxgeek on 2008-08-30
> **swoll1980 said:**
> I don't like to preach, but always do a backup ecspecialy when your new to this kind of stuff, but even if you know what your doing "an ounce of prevention is worth a pound of cure" as my dad always said

I lost 150 GB worth of videos and music due to stupidity and gfx driver updates about a month ago ^^

---

### Post by gmxgeek on 2008-08-30
> **serenity_blu said:**
> For cat /etc/fstab:

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39f930de-6313-4362-b64d-36ffaf71ec15 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=13a14d05-5fe3-4f94-b9ff-8bebeb0ab4da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
[/I]

And for df -h:

[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             226G  2.3G  212G   2% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   48K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      226G  2.3G  212G   2% /home/joel/.gvfs
/dev/scd0             695M  695M     0 100% /media/cdrom0
[/I]


And for sudo fdisk -l:

[I]Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29638   238067203+  83  Linux
/dev/sda2           29639       30394     6072570    5  Extended
/dev/sda5           29639       30394     6072538+  82  Linux swap / Solaris
[/I]

yeah it's looking like no windows on there

If you really want to just kill ubuntu, then just reinstall xp, and have the installer plough over the partition.
If you might want to keep ubuntu, then install xp to a new partition, and then follow the instructions here:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by serenity_blu on 2008-08-30
> **gmxgeek said:**
> I lost 150 GB worth of videos and music due to stupidity and gfx driver updates about a month ago ^^

Ouch, mine wouldn't be that bad. Maybe 20 GB total. I'd guess around 400-450 songs, a half dozen movies, and like 6 or 7 seasons worth of shows. At least I've watched most of the shows already, but still... bah!

---

### Post by swoll1980 on 2008-08-30
> **serenity_blu said:**
> Ouch, mine wouldn't be that bad. Maybe 20 GB total. I'd guess around 400-450 songs, a half dozen movies, and like 6 or 7 seasons worth of shows. At least I've watched most of the shows already, but still... bah!

That sucks horribly I get mad if a loose one avi file. Sorry this happened to you

---

### Post by matrix880812 on 2008-08-30
get a windows xp install cdrom
boot from it
then select recover from the *****
when you see the prompt c:\windows\
input the command "fixmbr"
then reboot
I guess you can enter windows xp now
then delete the partition on which ubuntu is installed
everything might be OK now... ...
good luck

---

### Post by caljohnsmith on 2008-08-30
Serenity_blu, if you want to try and recover any of your Windows files, a great program to do that is "photorec". Just see the following for how to use it:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

P.S. I wouldn't recommend running "fixmbr", because all that does is reinstall Win XP's boot loader to the MBR; you still won't be able to boot Windows (which is deleted), and you won't be able to boot Ubuntu either.

---

