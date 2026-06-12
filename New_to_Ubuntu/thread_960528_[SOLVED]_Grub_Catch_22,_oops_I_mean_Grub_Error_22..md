---
title: "[SOLVED] Grub Catch 22, oops I mean Grub Error 22."
date: 2008-10-27
forum: New to Ubuntu
---

### Post by the.scarecrow on 2008-10-27
I have been so pleased with Ubuntu 8.04 i386 that having first installed it on my desktop PC, I then installed it on my old Dell Latitude, all a great success. Next I pursuaded my son to try it on his PC and after a very successful demo using the live CD, we attempted to install it in one of his spare partitions. Thats when it all went wrong.

When we got to the partition manager we selected the required empty NTFS (52GB) partition and deleted it to create the empty space needed for Ubuntu. We first made a 4GB swap partiton and then a 48GB / SW3 partiton. Installation continued as normal until we had to reboot, when it restarted it went straight into windows XP with no sign of GRUB. We changed the boot loader to look at the HDD with Ubuntu on it first but then got the dreaded GRUB error 22.

4GB RAM
80GB Maxtor IDE HDD (Windows XP)
200GB Western Digital IDE HDD (Ubuntu and data storage)
500GB SD SATA HDD (data storage)

Does error 22 mean that Grub can't find the Ubuntu / partition? If so, what is the simplest, safest way to edit Grub and tell it where to look? We can't backup all the data on the 200GB Western Digital IDE HDD we have nowhere to put it. 

Thanks for any help but try to keep it simple step by step because we are complete Ubuntu Newbies.

---

### Post by wolfen69 on 2008-10-27
GRUB Error 22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

i would get a gparted live cd and create the partitions ahead of time and reinstall ubuntu using manual method.

---

### Post by philinux on 2008-10-27
Try this.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by caljohnsmith on 2008-10-27
Since you have more than one drive, probably what happened is Grub was installed to the MBR (Master Boot Record) of the wrong drive. I assume you get the Grub error 22 before seeing the Grub menu, is that true? If it is, first try the following from your Live CD to install Grub to the MBR of your Ubuntu drive, and then you can make sure that BIOS is set to boot it on start up. So open up a terminal (applications > accessories > terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, and if your BIOS is set to boot the Ubuntu drive, you should at least get a Grub menu on start up; but probably booting any of the OS entries will give an error. See if you can get this far, and we can go from there. :)

---

### Post by the.scarecrow on 2008-10-27
Thank you very much for your fast help with this problem.

I have done as you asked in the first stage and this is the results. I would like to check with you what these results are before i continue, to make sure that everything is okay. 

Your suggestion:

```

sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```


The results to these in order are:
```

grub>
      find /boot/grub/stage1
 (hd2,6)

```
-----------------------------------
```


grub>
      find /grub/stage1 

Error 15: File not found
```

You are correct there is no Grub menu that loads up on boot up. To add a small note that may be obvious, the drive that WinXP is on is Master IDE while the Ubuntu is acting as a Primary Slave.

Thank you all so far for the help, please keep em coming.

---

### Post by caljohnsmith on 2008-10-27
OK, that's great, just finish with:
```
sudo grub
grub> root (hd2,6)
grub> setup (hd2)
grub> quit
```
Also, please post:
```
sudo fdisk -lu
```
Can you set your BIOS to boot your Ubuntu drive first on start up, before the Windows drive? That's what is key here, otherwise another not-as-ideal choice is to install Grub to the MBR of your Windows drive so that you can boot both OSes; the disadvantage of that though is if anything happens to either drive (including simply disconnecting one of them), then you won't be able to boot into Ubuntu or Windows.

---

### Post by the.scarecrow on 2008-10-27
Thats great thank you so much for such a fast response again its very kind of you.

After typing in the following commands:

```
sudo grub
grub> root (hd2,6)
grub> setup (hd2)
grub> quit
```

This was the results on my computer:

```
grub> root (hd2,6)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```

If this all sounds good to you i can restart the PC and edit my Boot sequence so the Linux HDD is before the WinXP HDD. Would this mean that Grub should now work and i will be able to pick which OS i will be booting in future as long as the Linux drive is before the WinXP drive in the boot sequence?

---

### Post by caljohnsmith on 2008-10-27
Yes, go ahead and reboot, set your BIOS to boot the Ubuntu drive, and you should hopefully get the Grub menu on start up. Most likely none of the entries will work, so if that is the case, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can get this far, and we can go from there. :)

---

### Post by the.scarecrow on 2008-10-27
Oooops! In reply to the

```
sudo fdisk -lu
```

Results are:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7cf87cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sda2       204796620   976751999   385977690    f  W95 Ext'd (LBA)
/dev/sda5       204796683   430076114   112639716    7  HPFS/NTFS
/dev/sda6       430076178   655355609   112639716    7  HPFS/NTFS
/dev/sda7       655355673   976751999   160698163+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f513f50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xee5e3218

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2              63   204796619   102398278+   f  W95 Ext'd (LBA)
/dev/sdc3       204796620   390716864    92960122+   7  HPFS/NTFS
/dev/sdc5       102398373   204796619    51199123+   7  HPFS/NTFS
/dev/sdc6             189     7807589     3903700+  82  Linux swap / Solaris
/dev/sdc7         7807653   102398309    47295328+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

---

### Post by the.scarecrow on 2008-10-27
> **caljohnsmith said:**
> Yes, go ahead and reboot, set your BIOS to boot the Ubuntu drive, and you should hopefully get the Grub menu on start up. Most likely none of the entries will work, so if that is the case, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can get this far, and we can go from there. :)

So does this mean i should edit the (hdX,Y) to read (hd2,6)?

Sorry but this bits getting a little complicated and if i mess it up .... ill regret it i'm sure.

---

### Post by caljohnsmith on 2008-10-27
Yes, booting issues can sometimes get a little complicated, because on start up, Grub will see the order of devices as the same as the boot order; that means that if you boot your sdc Ubuntu drive first, it will be (hd0) on start up. That means you need to edit Ubuntu's "root (hdX,Y)" line to be "root (hd0,6)". Give it a shot and let me know how it goes.

---

### Post by the.scarecrow on 2008-10-27
I plan to edit the boot order as follows:

DVD Drive
WD HDD = Linux
SATA HDD
Maxtor HDD = Windows
USB and other bits and bobs after

So the WD HDD wont be the first "Drive" as it where in the list, will that still mean the root should be (hd0,6) or as its the second drive it will need to be (hd1,6)?

Very sorry for being such a noob :(

---

### Post by caljohnsmith on 2008-10-27
> **the.scarecrow said:**
> I plan to edit the boot order as follows:

DVD Drive
WD HDD = Linux
SATA HDD
Maxtor HDD = Windows
USB and other bits and bobs after

So the WD HDD wont be the first "Drive" as it where in the list, will that still mean the root should be (hd0,6) or as its the second drive it will need to be (hd1,6)?

Very sorry for being such a noob :(
I don't think having the DVD drive before the WD HDD is going to make the WD HDD (hd1) in Grub's eyes, because I think Grub sees CD/DVD drives as an entirely different device than (hdX). So how about just try editing the Ubuntu entry on start up like I mentioned before, and you can easily try both cases, i.e. (hd0,6) and (hd1,6), and we'll see which one works. :)

---

### Post by the.scarecrow on 2008-10-27
*Gulp* ok im going for it. Ill be back in a few mins.... hopefully :p

---

### Post by the.scarecrow on 2008-10-27
:( No luck it still says:

Grub loading stage1.5.

Grub Loading, please wait

Error 22

---

### Post by caljohnsmith on 2008-10-27
Are you getting that Grub error 22 before seeing something in the upper-left corner of your screen that says "Press ESC to see menu"? 

How about doing the following so I can see which drives have Grub in the MBR:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
Next please post:
```
sudo mount /dev/sdc7 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by the.scarecrow on 2008-10-27
After using:
```

sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

```

Results where:
```

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ 

```
------------------------------------

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ 

```
-------------------------------------

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ 

```





After using:

```
sudo mount /dev/sdc7 /mnt
cat /mnt/boot/grub/menu.lst

```

Results:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc7 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,6)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Hope this all makes sense to you coz boy am i lost :P

---

### Post by the.scarecrow on 2008-10-27
And nope there is nothing other than the Grub Error that is visible on the screen. I have not seen a flash of a menu option before hand :(

---

### Post by caljohnsmith on 2008-10-27
OK, Grub did get installed to the MBR of your sda drive at some point it looks like; we should restore your Windows MBR on that drive, because that Grub error 22 you are getting could be because you are booting the sda drive on start up, even though you don't mean to. So from a terminal again, do:
```
sudo apt-get install syslinux
```
Make sure that package above installs OK before proceeding with:
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1
```
Then reboot, and let me know if you still get the Grub error 22. If you do, at least we will know for sure you are booting the sdc drive first, and we can sort it out from there.

---

### Post by the.scarecrow on 2008-10-27
I did the first stage but as you seemed to make it clear this first stage had to be done correctly ill quickly show you the code so far so you can give me the all clear for part two "sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1" :)
```

ubuntu@ubuntu:~$ sudo apt-get install syslinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mtools
Suggested packages:
  floppyd
The following NEW packages will be installed:
  mtools syslinux
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 557kB of archives.
After this operation, 1253kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy/main mtools 3.9.11-0ubuntu1 [204kB]
Get:2 http://archive.ubuntu.com hardy/main syslinux 2:3.53-1ubuntu2 [353kB]
Fetched 557kB in 2s (262kB/s)    
Selecting previously deselected package mtools.
(Reading database ... 98223 files and directories currently installed.)
Unpacking mtools (from .../mtools_3.9.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package syslinux.
Unpacking syslinux (from .../syslinux_2%3a3.53-1ubuntu2_i386.deb) ...
Setting up mtools (3.9.11-0ubuntu1) ...

Setting up syslinux (2:3.53-1ubuntu2) ...
ubuntu@ubuntu:~$ 

```

Hope its good so far and thanks again for all this help.

---

### Post by caljohnsmith on 2008-10-27
Looks good... Go for it. :)

---

### Post by the.scarecrow on 2008-10-27
Ok done the last stage:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1
```


and this is the results:

```
ubuntu@ubuntu:~$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1
0+1 records in
0+1 records out
410 bytes (410 B) copied, 0.0160179 s, 25.6 kB/s
ubuntu@ubuntu:~$ 

```


Hows it looking now and whats next?

---

### Post by caljohnsmith on 2008-10-27
Looks great, go ahead and reboot and let me know if you still get the Grub error 22.

---

### Post by the.scarecrow on 2008-10-27
Okay :)

hopefully ill be reporting good news in a few mins time *crosses fingers*

---

### Post by the.scarecrow on 2008-10-27
Ok so ermmm, well on the plus side no more error 22 :)

but its been replaced with something new and i don't know if its good or bad.

> NTLDR is Missing

Press Alt+Ctrl+Del to restart

and yep doing that simply restarts the PC.

I have not been able to research this new message yet. I hope you can still help me?

---

### Post by caljohnsmith on 2008-10-27
OK that error is actually really great news; is means you are indeed booting your 500 GB data storage sda drive first on start up like I suspected. Are you sure you are changing the BIOS boot order so that the sdc drive is first to boot? That's the issue here it looks like. If there is no possible way to boot your sdc drive, we could install Grub to the MBR of sda again, but we can do it correctly so that it will point to your sdc drive for its boot files and not give you an error 22. But can you check your BIOS again and see if you can get the sdc drive to boot first?

---

### Post by the.scarecrow on 2008-10-27
Ill try some different Boot Sequences, maybe i am mixing up my 500GB SATA drive with my 200GB IDE drive. Ill give things a go and get back to you in a few mins.

Thank you :)

---

### Post by meierfra. on 2008-10-27
Maybe your bios refuse to boot from the Ubuntu drive since it does not have any boot flag:

In a terminal type

```
sudo cfdisk /dev/sdc
```

select  sdc3.
Then choose "Bootable", "Write" and "Quit" 
(Press "enter" after each choice and answer "yes" when asked)

---

### Post by the.scarecrow on 2008-10-27
aah ok well some interesting things happened. I played with the boost sequence in mind that i thought the SATA was the IDE and the so on. Switching about did no changes apart from one set up where i got the following message:
> Intel(R) Boot agent GE v1.2.50
Copyright (C) 1997-2007, Intel Corporation

Intel (R) Boot Agent PXE Base Code(PXE-2.1 build 086)
Copyright (C) 1997-2007, Intel Corporation

Initializing and establishing link..._

And then after a few seconds boots into windows.

I remember you mentioning editing the MBR and well i really want to avoid doing anything to change my windows as i need to maintain that in a working state.

Thank you so much again for all this help its so kind of you and i hope we are steps away from getting this Linux thing working just right :)

---

### Post by the.scarecrow on 2008-10-27
> **meierfra. said:**
> Maybe your bios refuse to boot from the Ubuntu drive since it does not have any boot flag:

In a terminal type

```
sudo cfdisk /dev/sdc
```

select  sdc3.
Then choose "Bootable", "Write" and "Quit" 
(Press "enter" after each choice and answer "yes" when asked)

Ookie :) Just to let you know first Meierfra what the Boot sequences do to the actual boots.

I would expect the most ideal Boot would be:

TSSTCorp DVD+/-R 
WDC WD2000JB-00G = Expect to be Linux (Jumper set to slave)
MAXTOR STM380215 = Defiantly WinXP (jumper set to Master)
ST3500630AS = Expect to be SATA data storage
IBA GE Slot 00C8

But this set up doesnt even see Grub it just goes into WinXP. I have to swap MAXTOR and ST3500630AS with each other to see Grub at all before or now see the "NTLDR is Missing" message.

What do you make of this? Should i just go ahead with the:

```
sudo cfdisk /dev/sdc
```

or is there something else i need to do first? Will this damage Windows?

---

### Post by meierfra. on 2008-10-27
> TSSTCorp DVD+/-R
WDC WD2000JB-00G = Expect to be Linux (Jumper set to slave)
MAXTOR STM380215 = Defiantly WinXP (jumper set to Master)
ST3500630AS = Expect to be SATA data storage
IBA GE Slot 00C8

That's fine. 
> 
But this set up doesnt even see Grub 
Hopefully setting the boot flag will cure that problem.

> Should i just go ahead with the:

sudo cfdisk /dev/sdc


Yes.

> 
Will this damage Windows? 

Nope. It just changes one byte in the partition table of "/dev/sdc". This will let your bios know, that   "/dev/sdc" is a bootable hard drive.

---

### Post by the.scarecrow on 2008-10-28
Hi guys,

After some sleep i followed the:

```
sudo cfdisk /dev/sdc
```

and so this is the result which doesn't seem to be what was supposed to happen :(

```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions o
                   Press any key to exit cfdisk

```

Hope this is nothing fatal to windows :P

---

### Post by caljohnsmith on 2008-10-28
Interesting about that error; I looked over your sdc partition table just now from your post #9, and I don't see any overlapping partitions or any obvious partition problems that I can find. I don't use cfdisk though, so maybe it is just something with cfdisk. How about instead do this:
```
sudo fdisk /dev/sdc
```
Then type "a" and press enter, "3" and enter, and finally "w" enter. After that post the output of:
```
sudo fdisk -l
```

---

### Post by the.scarecrow on 2008-10-28
Hiya John!

Okay seems some improvement maybe :)

So from entering:

```
sudo fdisk /dev/sdc
```

I got:

```
buntu@ubuntu:~$ sudo fdisk /dev/sdc

The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 
```

Then following your commands:

```
Command (m for help): a
Partition number (1-7): 3

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
ubuntu@ubuntu:~$ 

```

And then the results from:

```
sudo fdisk -l
```

And here are the long results :P

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cf87cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60800   385977690    f  W95 Ext'd (LBA)
/dev/sda5           12749       26771   112639716    7  HPFS/NTFS
/dev/sda6           26772       40794   112639716    7  HPFS/NTFS
/dev/sda7           40795       60800   160698163+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f513f50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee5e3218

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1       12748   102398278+   f  W95 Ext'd (LBA)
/dev/sdc3   *       12749       24321    92960122+   7  HPFS/NTFS
/dev/sdc5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sdc6               1         486     3903700+  82  Linux swap / Solaris
/dev/sdc7             487        6374    47295328+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
```

Hope this all helps? If not maybe you should fly over here to the UK to have a look at this :P Tea and Crumpets on me mate! Maybe not the flight ticket tho...

haha hope to hear from ya soon.

---

### Post by caljohnsmith on 2008-10-28
That's great, sdc3 is now marked as bootable. Go ahead and reboot, and if you don't get the Grub menu or at least a Grub error, then make sure your BIOS is still set to boot the sdc drive before your other drives. Let us know how it goes. :)

---

### Post by the.scarecrow on 2008-10-28
Whoohoo! Nice one! Now Grub loads up and has options to pick an OS :)

Ok we seem to have three types of Linux:

Normal
Safe mode
... something else beginning with M

Then under Other operating systems is Windows XP!

hehe i know its a step in the right direction im sure... only thing is none of the darn OS blinking load :P

this is the error messages when i selected Linux first:

> Error 17: Cannot mount selected partition
Press any key to continue

and that takes us back to the Grub menu to pick an OS so i then of course try my life line Windows XP and well.... that came up with:

> Error 18: Selected Cylinder exceeds maximum supported by BIOS

Then tried Linux Safe Mode and Error 18 also

and that error replaced the error 17 when trying normal Linux again also so it seems Error 17 is only on the first attempt and then its followed by Error 18.

so ermmm whats next :P

---

### Post by caljohnsmith on 2008-10-28
That's great, getting the Grub menu on start up is usually 90% of the battle to get Grub working. :) I'm glad meierfra caught the fact your sdc drive didn't have a partition marked as bootable, because I missed that earlier. So to modify your Grub menu.lst, how about doing:
```
sudo mount /dev/sdc7 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Then find the line that says "# groot=(hd1,6)" or whatever numbers it uses, and change it to:
```
# groot=(hd0,6)
```
Next modify all your Ubuntu entries to use (hd0,6), similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,6)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Next add the following two entries for Windows at the end of the file:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Save, reboot, and let me know what happens. :)

---

### Post by the.scarecrow on 2008-10-28
wooooooow man this is complicated! Can i paste all this to you and you can either highlight the bits that need to be edited or even edit them so i can copy and paste it in and replace what it is now?

in way over my head now :p

```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,6)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by caljohnsmith on 2008-10-28
Well, it's not really *that* complicated, but just copy/paste this menu.lst to replace your other menu.lst:
```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eed7b357-a21c-4bc0-a31a-c7596e1e188b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```

---

### Post by the.scarecrow on 2008-10-28
wow! It works! You fixed it, you made it work!!

Windows still works as well!

I could never thank you enough John. Your the Mother Teresa of Linux forums. Your kindness will not be forgotten :) Linux may have a non (Noob)User friendly partition system and Grub is possibly even worse. But my goodness the community of such kind and caring users makes my hopes that Linux can one day crush Microsoft when Linux opens its doors to the general public seem very possible.

I have high hopes for Linux. I simply hope that the new version of Linux coming out in a few months time is more user friendly and easier to set up. If it is i will do my best to spread the word that Linux is the better operating system out there.

Windows < Linux

massive thank you to everyone again!




so.... how about getting Linux working on my laptop?..... haha just kidding :P
Enough tinkering for one day i think!

Wish you all the best.

---

### Post by caljohnsmith on 2008-10-28
Glad everything is working OK now, at least as far as booting goes. :) I agree with you though, Linux still has many rough edges that it needs to polish before it could really be considered a true alternative to Windows, at least for the masses. But I consider it a great deal compared to shelling out > $200 for Windows, even though I do have Windows too (and I even paid for it). Anyway, cheers and have fun Ubuntu-ing. :)

---

### Post by meierfra. on 2008-10-28
> FATAL ERROR: Bad logical partition 6: enlarged logical partitions o
                   Press any key to exit cfdisk

I'm little  bit worried about this. I never had a problem with cfdisk. (I use it  regularly, since I label my partitions and "fdisk" does not report  the labels) But cfdisk is more picky than fdisk. Fdisk will let you manipulate any kind of partition table,  but cfdisk will not work when the partition table is corrupted in some way.
 
Partition 6 is your swap partition. Would you mind posting the output of

```
free
```

just so that we can see whether swap is being used?

---

### Post by the.scarecrow on 2008-10-31
Ive been using Linux since your help and its been working fine but here is the information you asked for mate:

```
phil@phil-pc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3364696    1298404    2066292          0     165676     663336
-/+ buffers/cache:     469392    2895304
Swap:      3903692          0    3903692
phil@phil-pc:~$ 

```

hope its what you wanted.

---

### Post by meierfra. on 2008-10-31
Everything looks fine. I did some googleing, and it seems that the "fatal error" reported by cfdisk  is  due to a bug in cfdisk. Sorry to bother you, I should have googeled before my last post.

---

### Post by the.scarecrow on 2008-11-01
Well thanks for your concern and support. I've got Ubuntu singing and dancing for me here so I'm well impressed with it.

Cheers
the.scarecrow

---

### Post by goscuter1 on 2011-10-07
> **the.scarecrow said:**
> i got the following message:
> 
Intel (R) Boot Agent PXE Base Code(PXE-2.1 build 086)
Copyright (C) 1997-2007, Intel Corporation

Initializing and establishing link..._                      And then after a few seconds boots into windows.

> **meierfra. said:**
> > FATAL ERROR: Bad logical partition 6: enlarged logical partitions o
                   Press any key to exit cfdisk                      cfdisk will not work when the partition table is corrupted in some way.

> **meierfra. said:**
> it seems that the "fatal error" reported by cfdisk  is  due to a bug in cfdisk.

 Was that the official line from the cfdisk guys? Are they sticking to it...?

I wonder whether it's normal to boot into your OS remotely without realising it. Is that a bug, as well?

---

