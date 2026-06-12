---
title: "[SOLVED] remove corrupted package"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by haydemon on 2008-06-25
I recently tried to upgrade to a new Ubuntu distribution after being prompted when I accessed the "add/remove" applications manager. In doing so, the installation failed (don't know why), so I reinstalled the older version from a CD. However, the new corrupted version is still in my hard drive occupying space. I cannot remove, because I don't know how, nor do I dare go through the Package Manager, because I don't know which components are being used by the version I'm currently using (not sure which version it is, because I don't know where to find out). I want to get rid of the corrupted system. Is there a safe way to do it? HELP!!! Thanks.

---

### Post by Eisenwinter on 2008-06-25
Open up terminal, and type sudo fdisk -l.
Post the output in here.

The "corrupted" Ubuntu installation is more than likely on another partition on the disk, which you'll need to format.

---

### Post by Yudraciell on 2008-06-25
if you know the package name you can search it with then Synaptic Package manager (located in System-> Admin)

And find it and mark it for installation

dont mark it for removal or complete removal cause it could be hazardus for your linux's health

---

### Post by haydemon on 2008-06-26
> **Eisenwinter said:**
> Open up terminal, and type sudo fdisk -l.
Post the output in here.

The "corrupted" Ubuntu installation is more than likely on another partition on the disk, which you'll need to format.
What does "fdisk" do? Does it not mean "format disk?" And how do I know which partition is the one that needs reformatting? Sorry. It's not that I don't trust your answer, it's that I am quite NOVICE about this and since it's the work computer, I'd hate to screw things up beyond recovery. Thanks!

---

### Post by drs305 on 2008-06-26
> **haydemon said:**
> What does "fdisk" do? Does it not mean "format disk?" And how do I know which partition is the one that needs reformatting? Sorry. It's not that I don't trust your answer, it's that I am quite NOVICE about this and since it's the work computer, I'd hate to screw things up beyond recovery. Thanks!

It never hurts to ask. ;-)  *fdisk -l* just reports the partition structure of your system. It doesn't write anything to your disks. By the way, the "-l" is a small L, not a 1 (one).

---

### Post by Ryadt on 2008-06-26
hi..
go in synaptic click on custom filters then choose broken, there you can remove all broken packages..
hope this help..

---

### Post by haydemon on 2008-06-26
> **drs305 said:**
> It never hurts to ask. ;-)  *fdisk -l* just reports the partition structure of your system. It doesn't write anything to your disks. By the way, the "-l" is a small L, not a 1 (one).
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6986    56066850    7  HPFS/NTFS
/dev/sda3            6987        7765     6257317+  83  Linux
/dev/sda4            7766        9726    15751732+   5  Extended
/dev/sda5            9607        9726      963868+  82  Linux swap / Solaris
/dev/sda6            8387        9548     9333702   83  Linux
/dev/sda7            9549        9606      465853+  82  Linux swap / Solaris
/dev/sda8   *        7766        8352     4715014+  83  Linux
/dev/sda9            8353        8386      273073+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by haydemon on 2008-06-26
> **Ryadt said:**
> hi..
go in synaptic click on custom filters then choose broken, there you can remove all broken packages..
hope this help..
Hi. If I remove all broken pkgs, is there a danger of removing sections of usable packages? Or would it warn me before removing parts that are currently being used by good pkgs? Thx!

---

### Post by WRDN on 2008-06-26
In the Synaptic Package Manager, when removing packages, it will tell you what will be removed, and what will remain unchanged.
Check for what will be removed, and you could post the list here if you're unsure, so someone could look over it.
Also, if it failed during installation, you could reinstall it, by finding the package (if its corrupted, just use the filter to find broken packages), and selecting to install it again.

---

### Post by haydemon on 2008-06-26
> **WRDN said:**
> In the Synaptic Package Manager, when removing packages, it will tell you what will be removed, and what will remain unchanged.
Check for what will be removed, and you could post the list here if you're unsure, so someone could look over it.
Also, if it failed during installation, you could reinstall it, by finding the package (if its corrupted, just use the filter to find broken packages), and selecting to install it again.

:confused:I went to Package Manager, filtered for broken packages, nothing came back. Clicked on "fix broken packages" just for good measure. Reports "0 broken packages" however. But the corrupted Ubuntu install is still there, because I see the option when rebooting, I can choose it (so it boots up the corrupted system), and I can see how messed up it is. So I go back and choose the "good" (older) version which is still available. It appears both versions are in different partitions. I just want to remove the bad partition.

---

### Post by drs305 on 2008-06-26
> **haydemon said:**
> It appears both versions are in different partitions. I just want to remove the bad partition.

If you post the contents of fstab and menu.lst we can tell you which partition would be safe to delete/reformat:
```
cat /etc/fstab
cat /boot/grub/menu.lst
```

---

### Post by haydemon on 2008-06-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=f0310ca0-8ae5-4527-bd9c-e397a20b36af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
monica@monica-desktop:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# kopt=root=UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fbf2e7e1-b2ba-400b-a7a2-d2db16cee1bd ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Debian GNU/Linux, kernel 2.6.18-6-k7 (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-6-k7 root=/dev/sda3 ro
initrd          /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Debian GNU/Linux, kernel 2.6.18-6-k7 (single-user mode) (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-6-k7 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bf4091a9-1d0c-4541-950e-cd6759ac5ebf ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=bf4091a9-1d0c-4541-950e-cd6759ac5ebf ro single
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 7.10, memtest86+ (on /dev/sda6)
root            (hd0,5)
kernel          /boot/memtest86+.bin
savedefault
boot

---

### Post by drs305 on 2008-06-26
Just so we are certain which is the 'good' system, when you run:

```
uname -r
```
are you seeing: 2.6.22-15-generic

It's important to find out which is the 'good' system since it may not be the latest release.
Additionally, is it the Debian GNU/Linux installation that went bad? 
There is also a listing for an older gutsy install on sda7.

Looking at the information you posted, if that was the complete fstab, you are only mounting /dev/sda8 (ubuntu) and /dev/sda9 (ubuntu swap). If they are running fine and you aren't routinely manually mounting sda's 3,5,6,7 then it is accessing no information from those partitions. 

Obviously you don't want to delete your windows partition (or at least you haven't mentioned this), but unless you are manually mounting them you have old or non-working ubuntu installations on sda's 3,5,6,and 7. *It is possible one of these OLDER installs is the one you want to retain. If not,* these partitions would be safe for you to remove IF YOU DON"T HAVE OTHER DATA stored on them.

As always, back up any important data before you do this; and be certain to ask questions if you have them.

---

### Post by haydemon on 2008-06-26
Yes, I am seeing 2.6.22-15-generic.
There is a Debian GNU/Linux install that I'd also like to get rid of, because I cannot use Debian since I've been unable to fix a screen resolution problem (posted several questions about this, but could never get it resolved--no matter, I'm happy with Ubuntu). I cannot get rid of Windows tho, because it's the office standard (but I'm a rebel, so I choose Linux). The only reason I want to get rid of non-working versions is because I'm afraid they are taking up disk space and I really need to free up some.

When you say "manually mounting sda's" what do you mean, exactly?

---

### Post by lenswipe on 2008-06-26
> **haydemon said:**
> :confused:I went to Package Manager, filtered for broken packages, nothing came back. Clicked on "fix broken packages" just for good measure. Reports "0 broken packages" however. But the corrupted Ubuntu install is still there, because I see the option when rebooting, I can choose it (so it boots up the corrupted system), and I can see how messed up it is. So I go back and choose the "good" (older) version which is still available. It appears both versions are in different partitions. I just want to remove the bad partition.

run gparted (should be available from the System menu if memory serves but im not sure)

This will open up the partition editor and then u can just find the drive/partition with ubuntu on and click format :)

hope this helps!:popcorn:

---

### Post by drs305 on 2008-06-26
> **haydemon said:**
> 
When you say "manually mounting sda's" what do you mean, exactly?

I just wanted to cover all the bases and leave little room for a mistake. Since those partitions weren't mounted by fstab, any files on those partitions would not be accessible or used after a normal boot. However, if you had a custom of mounting said partitions manually (by clicking on a drive icon, for instance) then perhaps you WERE using the data on them.

It sounds like everything is set. You can delete/reformat those unused/old partitions. Just to be sure, when lenswipe states 
> "This will open up the partition editor and then u can just find the drive/partition with ubuntu on and click format"

make sure you are *NOT* messing with the current ubuntu installation.

Also, once everything is back to normal, you might want to run "sudo update-grub" or remove all those extra entries manually from menu.lst . Although I prefer making changes with StartUp-Manager, in this case it would probably take manually deleting all the old entries to get it back to looking like it should.

---

### Post by fidamehran on 2008-06-26
The problem seems grave. I am also interested to know the solution.

---

### Post by haydemon on 2008-06-26
> **drs305 said:**
> I just wanted to cover all the bases and leave little room for a mistake. Since those partitions weren't mounted by fstab, any files on those partitions would not be accessible or used after a normal boot. However, if you had a custom of mounting said partitions manually (by clicking on a drive icon, for instance) then perhaps you WERE using the data on them.

It sounds like everything is set. You can delete/reformat those unused/old partitions. Just to be sure, when lenswipe states 

make sure you are *NOT* messing with the current ubuntu installation.

Also, once everything is back to normal, you might want to run "sudo update-grub" or remove all those extra entries manually from menu.lst . Although I prefer making changes with StartUp-Manager, in this case it would probably take manually deleting all the old entries to get it back to looking like it should.
This may sound like a stupid question, but better safe than sorry. Right now this is what I show in the Partition Manager:
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 6986 56066850 7 HPFS/NTFS
/dev/sda3 6987 7765 6257317+ 83 Linux
/dev/sda4 7766 9726 15751732+ 5 Extended
/dev/sda5 9607 9726 963868+ 82 Linux swap / Solaris
/dev/sda6 8387 9548 9333702 83 Linux
/dev/sda7 9549 9606 465853+ 82 Linux swap / Solaris
/dev/sda8 * 7766 8352 4715014+ 83 Linux
/dev/sda9 8353 8386 273073+ 82 Linux swap / Solaris

SDA 2 and SDA 8 are flagged as "boot". I guess I want to keep these, right? There are different "file systems", such as fat16, ntfs (labeled /media/disk), several ext3 (one labeled debian), and 3 linux-swap. Before I do something horrible, can you tell from this which ones are safe to delete? Thanks! (I hope I don't have to keep bugging you about this :) )

---

### Post by drs305 on 2008-06-26
The partitions I suggested were safe to delete were 3,5,6 and 7. These are all linux partitions, presumably from old installs. You do NOT want to mess with 1,2, 8 and 9. 1 & 2 are windows-related and it appears 8 & 9 are your ubuntu setup. You can't do anything about 4, which sets up your extended partitions.


fidamehran,

Your issue appears to be related to a bad *kernel* installation. Kernels are all installed on the same partition and several can coexist peacefully in the same installation (although only one will be in use). In this instance, it was a bad *installation* on a separate partition. 
Feel free to correct me if I've misinterpreted.

---

### Post by haydemon on 2008-06-26
Thanks to everyone who got involved in resolving this problem. I think I've come up with a solution from all the suggestions received. I will try it tomorrow and post the results. I appreciate everyone's help!

---

### Post by cariboo on 2008-06-26
Have tried in a terminal:

```
sudo apt-get -f install
```

That will probably fix your broken package.

Jim

---

### Post by haydemon on 2008-06-27
> **drs305 said:**
> The partitions I suggested were safe to delete were 3,5,6 and 7. These are all linux partitions, presumably from old installs. You do NOT want to mess with 1,2, 8 and 9. 1 & 2 are windows-related and it appears 8 & 9 are your ubuntu setup. You can't do anything about 4, which sets up your extended partitions.


fidamehran,

Your issue appears to be related to a bad *kernel* installation. Kernels are all installed on the same partition and several can coexist peacefully in the same installation (although only one will be in use). In this instance, it was a bad *installation* on a separate partition. 
Feel free to correct me if I've misinterpreted.
The saga continues... I was able to remove partition 3, but not the other ones. Partitions 5, 6, & 7 required me to remove higher numbered partitions first, which I wasn't going to. So now I have unallocated space that am not able to reuse, because gparted doesn't allow move/resize when I right-click on it. Here is a screen shot of my HD as it stands now.
[IMG]/home/monica/Desktop/Screenshot--dev-sda - GParted.png[/IMG]
(I don't think it came through...)

---

### Post by bumanie on 2008-06-27
The reason you can't delete the other partitions is because they are held within an extended partition. If you were to remove the extended partition, this would also remove the ubuntu partitions held within. However, you should be able to highlight (ie click on the aqua box) the extended partiton and move it to the left. If you have minimal saved data on ubuntu, you should, [IMO, which you can choose to ignore] consider getting rid of the extended partitions and installing ubuntu from scratch and do a manual setup at the partitioning stage and make yourself a / a separate /home and place only swap in an extended partition.

---

### Post by haydemon on 2008-06-27
> **bumanie said:**
> The reason you can't delete the other partitions is because they are held within an extended partition. If you were to remove the extended partition, this would also remove the ubuntu partitions held within. However, you should be able to highlight (ie click on the aqua box) the extended partiton and move it to the left. If you have minimal saved data on ubuntu, you should, [IMO, which you can choose to ignore] consider getting rid of the extended partitions and installing ubuntu from scratch and do a manual setup at the partitioning stage and make yourself a / a separate /home and place only swap in an extended partition.
I have no problem removing the extended partition and re-installing Ubuntu from scratch; however, I don't know how I can remove the partition while I'm still in the Ubuntu environment while doing it! I could reboot from Windows but can't do it from there, becz Windows is useless! Maybe I'm missing something? Thx.

---

### Post by Malac on 2008-06-27
> **haydemon said:**
> I have no problem removing the extended partition and re-installing Ubuntu from scratch; however, I don't know how I can remove the partition while I'm still in the Ubuntu environment while doing it! I could reboot from Windows but can't do it from there, becz Windows is useless! Maybe I'm missing something? Thx.
Boot up from the LiveCD where you can run "Partition Editor" without the installed systems being active.
This can be slow depending on system specs but it will allow full access to the partitions you have as LiveCD runs in RAM. except for swap which you would need to turn off from within "Partition Editor" to delete it, again this slows things down a bit.
 
Hope this helps.
P.S. Turn off all automount options when in the LiveCD if you are changing partitions as it has the annoying habit of remounting everything after every scan.

---

### Post by haydemon on 2008-07-24
OK. After all was said & done, I opted for the clean sweep; had IT completely erase my hard drive, reinstall Windows (because I have to, since like I said before, it's my work computer and it HAS to have WinXP), but allocate a smaller portion of the HD to WinXP, and leave 50% of unallocated space for Linux. I re-installed Ubuntu from a live disk, and voila! All is well now. I just had to go back and reset all my previous settings, etc. Had a bit of trouble with my sound/video settings (figuring out which codecs and plugins to re-install), but now I have music, online streaming audio, commercial DVD playing capabilities, and all my programs work. I also have plenty of room for installing additional software, etc. I'm a happy camper.:)\\:D/

Just wanted to post an update to this saga, and again thank everyone for their feedback and support. Y'all rock!:guitar:

---

