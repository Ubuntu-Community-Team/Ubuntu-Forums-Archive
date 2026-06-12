---
title: "[SOLVED] Cannot boot Windows after Ubuntu Install"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Ralph L on 2008-08-16
I think I fell into what looks to me like a rather nasty trap in the hardy install.  I downloaded the hardy install, burned a dvd+rw, booted hardy from the dvd, and got to the point of "Prepare Disk Space".  I had previously repartitioned the disk running GParted from a cd.  Disk was partitioned with:

sda1  Windows
sda2  extended
sda3  Ubuntu
sda4  Ubuntu
sda5  swap
sda6  Ubuntu
sda7  Shared_Data

Windows was on the disk first.  Installed Ubuntu on sda3 and sda4 and everything ran fine.  When preparing the Windows partition during the sda6 install I selected ntfs, no formatting, and set a mount point of /windows (from the menu).  In my previous install I had not set this option, but I hoped that setting it would create a mount point for Windows and I would not have to do it manually (later) as I did on the first Ubuntu installs.  Seemed obvious to me that this is what it would do.

Well, it did set the mount point in /media as I expected, and I could view my Windows files.  However, on the select operating system page during the boot sequence, there was no longer a Windows OS to boot!!  The name was changed to "Ubuntu" (sda1).  When I tried to boot sda1, it immediately hung with a message about not be able to boot.  So now I can't boot Windows.  However, when I look at /media/windows, I see all the Windows files, so Windows wasn't overwritten.  Also, when I bring GParted (under the OS, not the cd), I see, after /dev/sda1, an orange triangle with an "!" in the middle of it.  I don't know what this means, but it doesn't look good.

Anyway, does anybody have any ideas how I can get my Windows partition back in bootable shape?  Also, for anybody else installing hardy in a second partition on a Windows disk, beware of this trap.

Thanks

Ralph

---

### Post by lswest on 2008-08-16
First thing:

Can you post your /boot/grub/menu.lst, it may be just that the entry is wrong.

Secondly, try running from the XP CD and running "chkdsk /fr" (without the quotes) from the recovery console to fix any possible errors.

---

### Post by caljohnsmith on 2008-08-16
Also please post the output of:
```
sudo fdisk -l
```

---

### Post by zenithdave on 2008-08-16
Ive moaned about the install trap before, im currently on my 7th ubuntu install and 19th ish windows! i had silly amount of partitions on my drive from windows and ubuntu so i booted into windows repair part of the install and used partdisk and deleted them all.

Formatted drive C and ubuntu to have half the drive each and all is well so far.

Partitions are not for feint hearted!

Did anyone realize you can drag a bar on ubuntu partition on startup??? i didn't 

Also don't click start after installing google earth, use the desktop icon :D

---

### Post by Ralph L on 2008-08-16
Will try running chkdsk /fr

Here's the contents of /boot/grub/menu.lst

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
# kopt=root=UUID=06736a93-375e-4e38-a0ec-1e0990528086 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06736a93-375e-4e38-a0ec-1e0990528086 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=06736a93-375e-4e38-a0ec-1e0990528086 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.17-12-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro quiet splash 
initrd		/boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.17-12-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro single 
initrd		/boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.17-10-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=fe09792c-6176-4d2a-af37-c5162c03c25d ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

END OF MENU.LST

Here is the output of sudo fdisk -l

ralph@ralph-laptop:~$ sudo fdisk -l
[sudo] password for ralph: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f301f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3834    30796573+   7  HPFS/NTFS
/dev/sda2            8166       12161    32097870    5  Extended
/dev/sda3            3835        6616    22346415   83  Linux
/dev/sda4            6617        8165    12442342+  83  Linux
/dev/sda5            8166        8299     1076292   82  Linux swap / Solaris
/dev/sda6            8300        9841    12386083+  83  Linux
/dev/sda7            9842       12161    18635368+  83  Linux

Partition table entries are not in disk order
ralph@ralph-laptop:~$ 


END OF SUDO FDISK -L

---

### Post by caljohnsmith on 2008-08-16
I'm sorry, but I could not understand your original post where you tried to describe what you were doing about mounting Windows. I don't know what happened to your Windows partition sda1, but it does not have its boot flag set any more according to fdisk; thus its not a complete surprise it won't boot. Your menu entry for Windows in your Grub's menu.lst appears to be correct since it uses (hd0,0). Can you give any more details of what you did with your Windows partition? 

Also, do you have the following files in root directory of your Windows partition still?
```
boot.ini
NTDETECT.COM
ntldr

```
Those are all necessary to boot Windows.

---

### Post by Ralph L on 2008-08-16
First, I ran chkdsk /pr twice.  First time it found errors and apparently fixed them.  Second time it got no errors.  However, I still can't boot windows.

To screw up windows I did the following:
1.  Booted from the hardy install dvd I made.  Selected "without change to your computer".
2.  Clicked on the "install" icon.
3.  When I came to the "Prepare Disk Space" window, I selected "manual".  That brought up a "Prepare partitions" window with all the partitions listed.
4.  I clicked on sda1 (windows), then clicked on "Edit Partition".  That brought up the "Edit a partiton" window.
5.  I went to the "Use as:" pull down box and selected ntfs.
6.  Then went to the "Mount point:" pull down box and selected "/windows". I did NOT check the "Format" box.  Then clicked ok.
7.  I then completed the install on sda6.
8.  Restarted and saw that my Windows partition was changed to Ubuntu.
9.  Tried to boot from the partition labelled sda1 and got "Error 17: Cannot Mount selected partition"  "Press any key to continue".  This takes it back to the OS selection screen.

---

### Post by nicedude on 2008-08-16
1. Booted from the hardy install dvd I made. Selected "without change to your computer". # this means you chose to run it live and not make changes good move


2. Clicked on the "install" icon. # here the don't make changes goes out the window since you selected install - good move if you know what your doing


3. When I came to the "Prepare Disk Space" window, I selected "manual". That brought up a "Prepare partitions" window with all the partitions listed. # also a good move, manual is how I do it as well


4. I clicked on sda1 (windows), then clicked on "Edit Partition". That brought up the "Edit a partiton" window. # oops why on earth would you do this unless it was to resize it smaller to make space, but if so that is all you should do here with this partition


5. I went to the "Use as:" pull down box and selected ntfs. # oops this was not needed for anything and is the begining of your downfall


6. Then went to the "Mount point:" pull down box and selected "/windows". Then clicked ok. # oh no we changed windows mount point for no reason, not a good idea.


7. I then completed the install on sda6. # probably fine but sda6 is a long way from sda2 what partitions are in the middle ?

8. Restarted and saw that my Windows partition was changed to Ubuntu. # have no idea on this but with what you did already anything is possible

9. Tried to boot from the partition labelled sda1 and got "Error 17: Cannot Mount selected partition" "Press any key to continue". This takes it back to the OS selection screen. # no wonder you changed its mount point when you shouldn't have changed anything with sda2 and instead grub would have referenced it in menu.lst and it would have booted all its own. But as I read this you might have reformated the sda2 partition with NTFS and a mount point of /Windows which would give you the situation you have now.

Sorry but you are stuck, you could try using testdisk and seeing if you can reclaim your old partition intact but I see a XP reinstall in your future unfortunatly.


Sorry to bear bad news but don't mess with windows partitions ( outside of resizing them ) when installing linux and this won't happen again.

Hope this helps you figure this out

---

### Post by Ralph L on 2008-08-16
Why is the option 'Mount point: /windows" there?  I assumed it was to let me create a mount point for my windows partition so I could access it from Ubuntu.  It didn't reformat the windows partition as shown by the fact that I can still read all the windows files from Ubuntu--with that mount point that I shouldn't have tried to use.

Seems like a nasty little trap for noobies like me.

But thank you for your efforts.  I was afraid it was unrecoverable, but I thought I would ask.

As always I appreciate the quick response.

Ralph

---

### Post by nicedude on 2008-08-16
Man you should read up before doing things as in Linux if you choose to manage your own stuff ( like manual partitioning ) it assumes you know what you are doing and anything is possible ( as in you can break stuff real quick if you dont know what you are doing ). To make a dual boot setup you don't have to change anything about your Windows partition ( in fact changing anything is going to be disasterous ) to get it to work, as GRUB would have seen the partition and set the startup command for it all up for you. Sorry to be the bearer of bad news but if "testdisk" which is the program I mentioned earlier can't fix this then you will have to reinstall XP as you redid its partition. Also since you went from sda2 ( XP ) to sda6 ( Ubuntu ) that tells me you also had some other successful or unsuccessful installs in between.

---

### Post by lswest on 2008-08-17
can you post down the exact error message when you try to boot windows?

According to that error we may be able to copy the necessary file/files from the install CD.

missing boot.ini file: [http://www.computerhope.com/issues/ch000648.htm](http://www.computerhope.com/issues/ch000648.htm)

NTLDR file missing: [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

Hope that helps!

I also agree with nicedude, do not use the install to set up any extra configuration (in other words, set up the install partitions, then install, nothing more).  It's not much of a hardship to set up a mountpoint for a windows hdd, Ubuntu usually does it automatically for me (thanks to HAL, the hardware abstraction layer, and nautilus settings).  If it doesn't do so, you can do it using ntfs-config or using the terminal commands ```
sudo mkdir /media/mountpoint
gksudo gedit /etc/fstab
``` and then adding the lines ```
#windows drive
/dev/sda1 /media/windows ntfs-3g defaults 0 0
```

This will (in the future) help minimize problems.

I disagree with nicedude (regarding the re-install of XP) however, since replacing the boot.ini file and the ntldr ones using the above links might fix it (again, no guarantees, but it's a possibility), if it does not, then it does seem like you'll have to re-install XP)

---

### Post by nicedude on 2008-08-17
To anyone trying to help this guy, it is apparent to me by reading all the things he did that he reformated his XP partition while installing Ubuntu using the manual disk partitioner with a mount point of /windows and NTFS for the format. I don't know what his chances are for a recovery of this but I would assume slim at best and "testdisk" is the only program I am aware of in linux that might be able to do something but I doubt it. A data recovery boot cd could let him get some of his data from that overwritten partition back but now we are diving into computer forensics and you must have the tools to do this at hand. I would start right over and DBAN the whole disk and do it up nice and clean, but I have XP & Vista install disks ( and could make more if I want:-) ) and he very well might only have what the PC manufacturer gave him and thereby is sunk ( that burns me up to no end that you buy a new PC and they can't even afford to give you a DVD of the install and instead steal 10GB of your hard disk for a recovery partition - cheapskates ). So if anyone knows how he could undo reformating his NTFS XP partition with a live CD then please speak-up as I would like to hear as well ( always trying to learn stuff )

Sorry to this person that your install went this wrong, I have no idea why the /windows is a mount point option in the partitioner ( could someone say what that is used for as I just don't know ).

nicedude

---

### Post by caljohnsmith on 2008-08-17
> **nicedude said:**
> To anyone trying to help this guy, it is apparent to me by reading all the things he did that [COLOR="Blue"]he reformated his XP partition while installing Ubuntu[/color] using the manual disk partitioner with a mount point of /windows and NTFS for the format.
Are you sure that he actually reformatted the Win XP partition? Ralph said in his first post that during the installation process:
> **Ralph L said:**
> When preparing the Windows partition during the sda6 install I selected ntfs, [COLOR="Blue"]no formatting[/COLOR], and set a mount point of /windows (from the menu).
Also in a subsequent post, Ralph emphasizes that during the install process he:
> **Ralph L said:**
> Then went to the "Mount point:" pull down box and selected "/windows". [COLOR="Blue"]I did NOT check the "Format" box.[/COLOR] Then clicked ok.
And from his original post, Ralph said that after the installation process:
> **Ralph L said:**
> 
Well, it did set the mount point in /media as I expected, [COLOR="Blue"]and I could view my Windows files.
[/COLOR]
So correct me if I'm mistaken, but it seems to me that if he can still see his Windows files, his Windows partition must be at least partially intact. He may not necessarily have to try and recover with testdisk. If he is still able to mount his XP partition as he did above, he could recover his important files, and maybe we can even help him repair his XP partition.

---

### Post by egalvan on 2008-08-17
> **nicedude said:**
> it is apparent to me by reading all the things he did that he reformated his XP partition while installing ... using manual disk partitioner with a mount point of /windows and NTFS for the format.

Except that the OP stated

> 
When preparing the Windows partition during...install I selected ntfs, ***no formatting,*** and set a mount point of /windows (from the menu).

OP further states
> However, when I look at /media/windows, I see all the Windows files, so Windows wasn't overwritten

So it seems his files are still there.

Further,  fdisk shows the window partition does not have the boot flag set.

This sounds more like a mis-configured boot-loader and/or mbr


> **nicedude said:**
> I would start right over and DBAN the whole disk and do it up nice and clean,
nicedude

yep DBAN is nice, but very powerful. It WILL BLANK YOUR DRIVES.
I use it all the time to get them "nice and factory-fresh".
But use caution. There is no un-DBAN option.
:popcorn:

---

### Post by kansasnoob on 2008-08-17
If the OP is still reading one thing they could do, assuming they can boot successfully into Ubuntu (which I think is the case) is install either ntfs-config (safer and simpler) or ntfsprogs (better capabilities but much more "fiddly") and then access the ntfs partition(s) and see if any of their info is still intact.

Just a thought:confused:

I've been amazed at how much data I've been able to recover just by using an Ubuntu Live CD.

---

### Post by egalvan on 2008-08-17
This site has a tremendous amount of information...


Illustrated Dual Boot Site


[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


:popcorn:

---

### Post by nicedude on 2008-08-17
You may be very well right and I might have miss read his steps he took, but I can say that when he was trying to just have dual boot and ended up with an fdisk output like this

sda1 Windows
sda2 extended
sda3 Ubuntu
sda4 Ubuntu
sda5 swap
sda6 Ubuntu
sda7 Shared_Data

that something else took place, like multiple failed installs etc. as how would you end up with 3 EXT3 partitions from a dual boot setup? I have only seen this when someone has tried several times to install etc. Or knows what they are doing and have multiple linux installs :-)

If you are right then why couldn't he just change the mount point back and then grub would take care of the rest as it is no doubt still intact in the MBR and remainder on his Ubuntu partition that boots in /boot/grub and should still just chainload the proper partition ( sda1 ) and therefore boot? Am I wrong? If not then what is a default Windows XP partition supposed to have set as the mount point ( nothing? )? If someone knows he could just live boot and use partitioner to change that mount point and maybe have windows again.

Sorry again but I didn't see where he said he didn't check format. I thought it said he checked format.

---

### Post by kansasnoob on 2008-08-17
> **nicedude said:**
> You may be very well right and I might have miss read his steps he took, but I can say that when he was trying to just have dual boot and ended up with an fdisk output like this

sda1 Windows
sda2 extended
sda3 Ubuntu
sda4 Ubuntu
sda5 swap
sda6 Ubuntu
sda7 Shared_Data

that something else took place, like multiple failed installs etc. as how would you end up with 3 EXT3 partitions from a dual boot setup? I have only seen this when someone has tried several times to install etc. Or knows what they are doing and have multiple linux installs :-)

If you are right then why couldn't he just change the mount point back and then grub would take care of the rest as it is no doubt still intact in the MBR and remainder on his Ubuntu partition that boots in /boot/grub and should still just chainload the proper partition ( sda1 ) and therefore boot? Am I wrong? If not then what is a default Windows XP partition supposed to have set as the mount point ( nothing? )? If someone knows he could just live boot and use partitioner to change that mount point and maybe have windows again.

Sorry again but I didn't see where he said he didn't check format. I thought it said he checked format.

Yep! It's a mess! Starting out I did a lot of that, but I did it with a "test drive" ............. hmmmm, I guess that sounds funny! I actually installed a spare 30 GB hard drive and just started playing around using a win XP CD that always installs to anything (but with the 30 day timer clicking) and played, and played, and played!

What I was saying before was that if you're really new at this whole dual booting thing, just keep it simple! First time out of the chute there is no need to create a separate home partition and all that!

Job #1 is to protect the data and integrity of any pre-existing partitions and operating systems!

---

### Post by nicedude on 2008-08-17
Yes I did the same sort of messed up stuff when first installing Ubuntu as well, but fortunately I did this with extra XP & Vista install disks in my possession and after backing up important documents beforehand to a portable disk. But starting on an old extra hard drive is awesome advice for someone new if they are tech proficient and can swap hard drives etc. as it gives a nice testbed to try out "what does what".

If this person can figure out what to reset the mountpoint of sda1 to, and Windows then boots up. I would at that point say the best bet would be to use a live CD to delete all the other partitions and then reboot with the live install disk and reinstall Ubuntu. You only need make 1 SWAP partition of say 2GB and then 1 more with 15-30GB EXT3 with a mountpoint of "/" without quotes then any other freespace can be partitioned as NTFS or FAT32 for storing data to. This would be much cleaner and works 100% for me.

---

### Post by kansasnoob on 2008-08-17
> **caljohnsmith said:**
> I'm sorry, but I could not understand your original post where you tried to describe what you were doing about mounting Windows. I don't know what happened to your Windows partition sda1, but it does not have its boot flag set any more according to fdisk; thus its not a complete surprise it won't boot. Your menu entry for Windows in your Grub's menu.lst appears to be correct since it uses (hd0,0). Can you give any more details of what you did with your Windows partition? 

Also, do you have the following files in root directory of your Windows partition still?
```
boot.ini
NTDETECT.COM
ntldr

```
Those are all necessary to boot Windows.

I really do think we should give this another look!

My concern is restoring the original OS and it's contents.

It would be easy to erase any Linux mistakes and start over on that end, but this was a huge mistake!

---

### Post by Ralph L on 2008-08-23
I solved this problem accidentally and really don't understand why.  I went back to put some labels on partitions using Gparted.  I labeled the Windows partition "Windows".  Did the apply.  The next time I booted my Windows partition was back with no harm done.  Its all black magic!!!

Ralph

---

### Post by Bucky Ball on 2008-08-23
Hi. You state you have half disk for windoze, half for Ubuntu. Well, but the looks of your menu.lst, you have more than 2 partitions on there - h0,0; h0,3; h0,2. You should only have your latest installed Ubuntu, the recovery and the memtest, then the last kernel before that. (you have the first kernel as .19, the previous kernel - .16. Then you will notice you still have .12 in there and a few other things.

There is more than two partitions on this drive. :)

I would suggest going back to the old drawing board, wipe the lot (or spend hours trying to fix this mess), as the nice nicedude mentions, have a bit of a read, install windoze, then Ubuntu.

You could leave Windows there and just wipe all ubuntu installs (there are a few), but it might be an idea to use this opportunity to learn a bit about what is going on. Also as nicedude mentions, when you load Ubuntu, grub should (should!) take care of itself, you don't have to do anything as it will see windoze (or any other OS you have installed) and set itself up accordingly (all going to plan and if it doesn't go to plan, grub is a lot more fixable than where you are now).

Good luck. :)

Update: notice you fixed this problem by black magic in the time it took me to write this post. One thing: what are you faced with in the grub menu when you boot? How many options? (or kernels, disregarding Windoze that is).

---

### Post by caljohnsmith on 2008-08-23
> **Ralph L said:**
> I solved this problem accidentally and really don't understand why.  I went back to put some labels on partitions using Gparted.  I labeled the Windows partition "Windows".  Did the apply.  The next time I booted my Windows partition was back with no harm done.  Its all black magic!!!

Ralph
I just couldn't believe that a partition label should make any difference, so to prove that to myself, I decided to boot up my gparted Live CD; I erased my Windows partition's label and then rebooted. I was still able to boot Windows just fine from Grub. 

So bottom line is, I agree, that sounds like voodoo to me. :)

---

### Post by Ralph L on 2008-08-24
I want to thank everybody that responded to my problem.  Although black magic fixed it, if I had needed to recover windows your comments would have been helpful.  

People were concerned about the number of partitions I had on my disk.  They were all put there on purpose and they all came up in my OS selection menu during boot (plus a bunch of recovery selections).  My partitioning was:
sda1 Windows
sda2 extended
sda3 Ubuntu
sda4 Ubuntu
sda5 swap
sda6 Ubuntu
sda7 Shared_Data

The reason I have 4 bootable OS's is that: 

I wanted two Ubuntu so I could upgrade one and know that the other one would continue to operate.  I have had problems with upgrading.

I wanted a spare Ubuntu so that I could mess around and try things without screwing up my other two.

I wanted to share my data (/home) between all the partitions so that no matter where I was running I would have the same data.

I wanted Windows for those instances where only Windows will run an application.  I have been trying Wine and Crossover, but there are a lot of Windows apps that neither will run.

Finally, because I was unable to get hibernate to work using swap files rather than swap partitions, I had to add two more swap partitions to the mix.  Good thing its a 100 G drive!!!

Again, thanks for your support

Ralph

---

