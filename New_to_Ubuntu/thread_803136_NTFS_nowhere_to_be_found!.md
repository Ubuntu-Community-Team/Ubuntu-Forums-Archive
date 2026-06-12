---
title: "NTFS nowhere to be found!"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by driftking on 2008-05-22
Hello ubuntu users,

I've just got my hands on ubuntu yesterday and installed it. Installation took me ages to figure out, partitioning being the problem. 
I have two hard drives, both 80GB, the primary hard drive is for Windows XP so I used the storage/slave for ubuntu. I loaded up the linux LiveCD and used the Parition program available, splitting the storage/slave in half; one half partitioned as ext3 and the other ntfs. 
Ext3 is for linux whilst the ntfs is for storage in Windows. I then proceeded to install ubuntu on the ext3 partition, and split 2GB off the ntfs for swap space. All went well.
The ntfs hard drive didn't appear on ubuntu, becauses linux doesn't read ntfs formats unless you've got the kernel thingy. So I assumed it would appear when I boot up on Windows. And this is where my problem begins.
I loaded up Windows, the ntfs partition isn't there, where could it go? It's not in linux or windows! So I went on to ubuntuforums.org, registered and posted this thread. Hopefully you guys can help me find my lost partition so I can use it as storage for Windows.

Any help will be greatly appreciated,

Eric

---

### Post by iaculallad on 2008-05-22
> **driftking said:**
> Hello ubuntu users,

I've just got my hands on ubuntu yesterday and installed it. Installation took me ages to figure out, partitioning being the problem. 
I have two hard drives, both 80GB, the primary hard drive is for Windows XP so I used the storage/slave for ubuntu. I loaded up the linux LiveCD and used the Parition program available, splitting the storage/slave in half; one half partitioned as ext3 and the other ntfs. 
Ext3 is for linux whilst the ntfs is for storage in Windows. I then proceeded to install ubuntu on the ext3 partition, and split 2GB off the ntfs for swap space. All went well.
The ntfs hard drive didn't appear on ubuntu, becauses linux doesn't read ntfs formats unless you've got the kernel thingy. So I assumed it would appear when I boot up on Windows. And this is where my problem begins.
I loaded up Windows, the ntfs partition isn't there, where could it go? It's not in linux or windows! So I went on to ubuntuforums.org, registered and posted this thread. Hopefully you guys can help me find my lost partition so I can use it as storage for Windows.

Any help will be greatly appreciated,

Eric

It seems like you messed up your partitions. Post the whatever comes out when you issue this command on the terminal. YOu can use the LiveCD to boot, then open your Terminal.

sudo fdisk -l

(That's small L)

---

### Post by Eisenwinter on 2008-05-22
Open up Terminal in linux (Applications -> Accessories -> Terminal)
in there type sudo fdisk -l

Post results here

EDIT: Beaten.

---

### Post by driftking on 2008-05-22
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f105b08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010c010c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4982    40017883+  83  Linux
/dev/sdb2            9722        9964     1951897+  82  Linux swap / Solaris

---

### Post by iaculallad on 2008-05-22
> **driftking said:**
> Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f105b08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010c010c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4982    40017883+  83  Linux
/dev/sdb2            9722        9964     1951897+  82  Linux swap / Solaris

Ok.. good. Now let's try checking your GRUB menu. Try posting whatever comes out when you issue this command.

sudo gedit /boot/grub/menu.lst

Or, could you click on Places->Computer and see if you can see your windoze drive in there.

---

### Post by driftking on 2008-05-22
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
# kopt=root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by driftking on 2008-05-22
There's only the file system partition (which linux is installed) and the Windows main C drive. No ntfs partition!

---

### Post by iaculallad on 2008-05-22
> **driftking said:**
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
# kopt=root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Good for this one too. Try to post the result of:

cat /etc/fstab

---

### Post by driftking on 2008-05-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=bac72e7c-89dd-4f50-a461-27d87ad6b133 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=a69efb31-5df3-4dee-a5e1-171482af71fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by vanadium on 2008-05-22
You have no ntfs partition on the second drive. Instead you have a gap. It might be possible just to create the ntfs partition in the free space. If not, you may need to move the swap.

You must do this using gparted in a live CD session. You can not repartition a drive that is in use.

Boot up the live CD, type Alt+F2 then "gksu gparted" to load gparted. Select the right drive using the drop down in the right corner. I guess  gparted will allow you to create a partition in the free space, even though the entries will not anymore be in disk order. If gparted won let you, you will first need to move your swap partition to the right of your ext3 partition, then create the ntfs in the remaining space.

---

### Post by iaculallad on 2008-05-22
Issue this command on your Terminal:

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

and paste this on the last line

/dev/sda1 /media/windows ntfs-fuse auto,gid=1002,umask=0002 0 0

and try restarting.

---

### Post by driftking on 2008-05-22
Just a quick question while I'm here, I have a usb hard drive, like an actual hard drive, but hooked up with this usb converter thing. When I turn it on, it says 'unable to mount the volume '80 GB STORAGE'. Is it because it's ntfs or...

---

### Post by iaculallad on 2008-05-22
> **driftking said:**
> Just a quick question while I'm here, I have a usb hard drive, like an actual hard drive, but hooked up with this usb converter thing. When I turn it on, it says 'unable to mount the volume '80 GB STORAGE'. Is it because it's ntfs or...

Try looking this useful information on this [page]("http://ubuntuforums.org/showthread.php?t=142481").

---

### Post by driftking on 2008-05-22
Just to confirm before I do anything, when I insert 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

and press enter, it opens a notepad thingy. Do I paste it in there and the bottom?

---

### Post by iaculallad on 2008-05-22
> **driftking said:**
> Just to confirm before I do anything, when I insert 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

and press enter, it opens a notepad thingy. Do I paste it in there and the bottom?

yes, just paste it there and save the file. restart

---

### Post by driftking on 2008-05-22
Okay I just restarted into linux. It still isn't there, or was I meant to boot up in XP?

---

### Post by driftking on 2008-05-22
This popped up, I dunno if it was from my USB hard drive (which turned up in My Computer) or what but:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by driftking on 2008-05-22
Actually I dunno if my last post had anything to do with hard drives. Ooops!

---

### Post by iaculallad on 2008-05-22
If that failed, what if you try what vanadium stated above. Use the gparted which comes with the LiveCD.

---

### Post by driftking on 2008-05-22
Yea, I don't have the LiveCD at the moment, I'll try it when I get my hands on it.

---

### Post by driftking on 2008-05-23
I used the Linux LiveCD, hahaha, it wasn't even partitioned in any format yet! Dopey me. Thanks guys anyway, you've been helpful.

---

### Post by vanadium on 2008-05-23
That's what I told you a few pages ago.

---

### Post by driftking on 2008-05-23
Yea I know, I clicked thanks. But after I partitioned the ntfs my hard drive went crazy and corrupted. I tried formatting using the Windows Cd as boot up, failed. So now I'm using the LiveCd to repartition it, I've split it in half and made the first half ntfs. For the second half I've partitioned it in ext3 for ubuntu and split a bit for linux-swap. So the bars looks something like this [ ntfs ][ ext3 ][ swap ] <--- on the right side like vanadium said. 
Please post before I install in case something isn't right!

---

### Post by driftking on 2008-05-23
Didn't work, my hard drive is now completely corrupted. I can't format it, partition it or install linux. Any suggestions on reviving my hard drive?

---

### Post by SuperNapalm on 2008-05-23
Hmm, my old WinXP Pro install disc could fully format a HDD with NTFS, if you have something similar and can't do that, prehaps your hard drive has died.

But don't take my word for it, I'd wait for some more expert opinions first if i were you :)

---

### Post by hyper_ch on 2008-05-23
On a sidenote:

Use [noparse]```

```[/noparse] tags around the stuff you copy'n'paste from the console or from config files... it makes it a lot easier to read.

---

### Post by vanadium on 2008-05-23
Driftking, it is starting to look like your drive is defect. Can you post once again the output of "sudo fdisk -l" to see how ubuntu sees your drive now?

---

### Post by driftking on 2008-05-23
It seems I was able to partition it using partition magic 8. Now it makes a clicking noise everytime it's active, like the disk inside is scraping against something; probably a defect or it's dieing like many suggested. So Ill post the sudo thing and can you guys tell me a safe or correct way to partition the hard drive for ext3, ntfs and swap area. Or if I should use the hard dricve at all.

---

### Post by driftking on 2008-05-23
Oh yea! You should realise that ubuntu isn't installed anymore (due to stuffed up hard drive) so I'll be posting the sudo thing from the LiveCD, don't know if it'll still be the same.

---

### Post by driftking on 2008-05-23
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f105b08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010c010c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+   7  HPFS/NTFS

---

### Post by driftking on 2008-05-23
Looks like it can detect both, so whats the best way to partition it. Such as primary and logical, I don't know what they mean. Should ext3 be the first partition and linux-swap second, ntfs third?

---

### Post by iaculallad on 2008-05-24
> **driftking said:**
> Looks like it can detect both, so whats the best way to partition it. Such as primary and logical, I don't know what they mean. Should ext3 be the first partition and linux-swap second, ntfs third?

Ext3 is a filesystem and not a partition. If what you're asking now is "format" you're whole drive, then you might as well use the partition manager which comes with the LiveCD. If data loss is not a problem, thinking that you had already backed-up your important datum, then, you have to delete all existing partitions first. You could let the LiveCD do the automatic partitioning for you or should you choose Manual partitioning: You create first your swap partition, create your /, and your /home partitions. That all depends on you, with your HD size, you could create logical drives and format it as NTFS for your data.

---

### Post by driftking on 2008-05-24
Okay, so I'll format the harddrive with the LiveCD, created the swap first as /, then ext3 in primary as /home and the ntfs as logical /?(hehe). 

Ill report back with the results and if my harddrive is still alive.

---

### Post by driftking on 2008-05-24
So I've finished formatting my hard drive. Error first time but successful second time around. Linux is installed and NTFS seems to appear in Windows. 

But, when loading to Windows it had to do a disk check for consistency, then when I opened My Computer it had a red circle with a question mark on it, then it dissapeared. I opened My Computer again and it reappeared. I have doubts about this hard drive, I don't think it'll last long and it won't be long before I announce it's death. Hopefully not soon.

Thanks all for your help,

Eric

---

### Post by iaculallad on 2008-05-25
> **driftking said:**
> So I've finished formatting my hard drive. Error first time but successful second time around. Linux is installed and NTFS seems to appear in Windows. 

But, when loading to Windows it had to do a disk check for consistency, then when I opened My Computer it had a red circle with a question mark on it, then it dissapeared. I opened My Computer again and it reappeared. I have doubts about this hard drive, I don't think it'll last long and it won't be long before I announce it's death. Hopefully not soon.

Thanks all for your help,

Eric

For the red circle question mark on your drive, it would be better to say bye-bye to it than risking-saving your important files/data on it. But still you could use it for experimental purposes. Remember that regret comes last :-)

---

