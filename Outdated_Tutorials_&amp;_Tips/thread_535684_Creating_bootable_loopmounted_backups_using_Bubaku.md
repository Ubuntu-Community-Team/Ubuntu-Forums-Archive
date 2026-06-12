---
title: "Creating bootable loopmounted backups using Bubakup"
date: 2007-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2007-08-26
***Main site, downloads, and a more detailed, screenshot-based guide are at [http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html)***

**Introduction**

Bubakup, the Bootable Ubuntu Backup, is a tool that allows you to create a bootable backup image of your running system. It supports creating uncompressed, bootable loopmounted disk images of the whole or parts of the system, deleting backup disk images, archiving backup disk images using 7-zip, restoring backed-up archived disk images, and LVPM (which is pre-installed in the generated disk images) can be used to restore the backup loopmounted disk image to an actual partition.

**Usage Cases**

The bootable disk images created by Bubakup can be used as an emergency recovery and restoration tool, should your primary system become unbootable. It can also be used as a sandbox environment for testing bleeding-edge and unstable code, in an environment that is the same as though you were using your primary system, without harming your primary system. It can also be used as a general full system and data backup/restoration utility.

**What it does**

A loopmounted disk image of the size selected by the user is created on the partition selected by the user, and the contents of the currently running root partition, excluding directories selected by the user, are copied into it. The loopmounted disk image is then patched and modified with loopmounting patches to allow it to boot. A menu entry is then added to grub allowing for the booting of the loopmounted disk image. The user can then reboot into the bootable backup disk image and restore it to a partition using LVPM, archive the disk image and later restore it, or delete the bootable backup if it is no longer needed.
[B]
Requirements[/B]

This has been tested on Ubuntu 7.04 (Feisty) 32-bit, and Ubuntu 7.10 (Gutsy) 32-bit, though it may also work on other versions. Dependencies include os-prober, p7zip-full, and ntfs-3g, though these are automatically resolved when installing the deb package.

**Credits**

This guide and the Bubakup and LVPM applications were created by me, Geza Kovacs. The currently used loopmounting patches are from the Lupin component of the Wubi Project, though Ubuntu 7.10 (Gutsy)'s built-in loopmounting code will be used once it is released.

**Instructions**

If you prefer a graphical, screenshot-based tutorial, see the main site at [http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html) otherwise, follow the instructions below:

**Installation**

Download the package file (deb) at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) and install it. You will then be able to run Bubakup by clicking Applications -> System Tools -> Bubakup

**Creating a bootable backup**

Start Bubakup, and select the "Create a backup" option.

A dialog will then prompt you to specify a partition to save the backup to; select a partition and click OK.

The next dialog will tell you how much disk space will be needed by your backup, and if you want to exclude any directories from the backup, select the "Exclude more directories" option and specify the directory. Once you have excluded all the directories you would like to, select "Continue On".

The next dialog will then prompt you how large you would like to make the loopmounted bootable backup disk image, in MB. The minimum value should be enough if you are only using it as a backup/restore/rescue system, but if you aim to install additional software or store additional files on the backup image, for sandboxed testing or other purposes, you may want to give it more space (but remember to not go over the amount of free space on your hard drive). Once you have selected a value, click OK to proceed.

The backup process will then begin, and may take a long time (an hour or more), depending on how much data you backed up and your drive performance.

Once the "Backup Complete" notification appears, you can reboot and select the last option in the menu list, "Bubakup", to boot the bootable backup disk image.

**Restoring a bootable backup to a partition**

If you have a spare partition to restore to, or are willing to overwrite one, you can continue on; otherwise, you will need to shrink an existing partition and create a new one. If you don't have a livecd, you can use the Partition Manager tool at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) to resize your partitions (just install the deb package, boot it, and start GParted), or if you have a live CD, you can use GParted.

Once you have a partition to restore to, boot the bootable backup, and start LVPM at Applications -> System Tools -> LVPM, select "Transfer install to a dedicated partition", select the free partition to restore to, wait as it restores, and you can boot into your newly restored system. A more detailed guide is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

**Archiving a bootable backup**

If you archive a bootable backup and remove the original bootable disk images, you will be unable to directly boot it until you restore the backup. The archiving feature is primarily used for the purpose of saving disk space, and should be used only on older backup disk images that you won't have to boot anytime soon. To archive a bootable backup, start Bubakup (from the primary operating system, not the bootable backup), and select the "Archive existing backup option.

A dialog will then prompt you to select the partition in which the bootable backup disk image you wish to archive is stored in. Select the partition and click "OK".

The next dialog will then allow you to specify which directory you want to save the backup image in. Select a directory and click OK.

The next dialog will then ask how much compression to use, on a scale of 1 to 9. The higher the value, the smaller the file will be, though the time it takes to create the backup will drastically increase.

The archiving process will then begin, and the disk image will be compressed using 7-zip. The process may take over an hour, depending on the size of the original bootable backup disk image and the compression setting you selected. Once it is done, a text dialog will appear.
[B]
Restoring a bootable backup disk image.[/B]

Once you restore a bootable backup disk image from an archive, you will be able to once again boot the loopmounted disk image. To restore, first start Bubakup, and select the "Restore a backup from archive"

A file-selection dialog will then allow you to select the archived backup file (7z extension) to restore from. Select the file and click OK.

The next dialog will then allow you to select the partition to which the archived loopmounted backup disk image should be restored to. Select the partition and click OK.

Then wait as the compressed bootable backup disk image is uncompressed into the selected partition/bbk-$date subdirectory, and the grub menu entries are added to allow for booting from the loopmounted backup disk image.

**Deleting bootable backup images, undoing changes, and uninstalling**

Start Bubakup (from the primary operating system, not the bootable backup), and select the "Delete existing backup" option. 

A dialog will then prompt you to select the partition in which the backup is stored; select the partition and click OK

The next dialog will then list the bootable backups stored on the partition; select the backup you want to delete and click "OK"

The backup will then be deleted, and the GRUB menu entry will be removed.

If you want to remove Bubakup itself, just remove the package "bubakup" using Synaptic.

---

### Post by tuxcantfly on 2007-08-27
Subscribing to thread, ignore this post

---

### Post by DemoN3x on 2007-08-28
Nice howto.  I am planning to install another hard drive for my root ubuntu installation.  I think this will do the trick quite nicely :)

---

### Post by tuxcantfly on 2007-08-29
> **DemoN3x said:**
> Nice howto.  I am planning to install another hard drive for my root ubuntu installation.  I think this will do the trick quite nicely :)

Well if all you want to do is copy over a partition, using this would be overkill (it would take 2 steps; backup to disk image, then restore the disk image to a partition); I'd just use the GParted copy partition function to do the job, though of course, this would be useful if you wanted to keep a backup disk image, and testers are always welcome...

---

### Post by DemoN3x on 2007-08-30
I plan to do quite a bit of messing around so would like to keep a backup for when I screw it up ;)

---

### Post by KubuntuKilledMe on 2007-08-30
I have some doubts about the fundamental working of this program, namelly the storage of bootable backup images.

I read that they are stored in a partition. Does that partition require a filesystem and mounting? If not, does a single backup image use up all of the partition? And if so, why are they called images if they are a partition backup onto another partition? I thought "image" was the word you used when the content doesn't match the form, as in storing a partition in a file which will reside in a filesystem over another partition.

Can this program be used live? As in backup the running root partition? That is a step ahead of partimage and very interesting on its own. In my humble opinion, more interesting that the whole "bootable" property of such backup images. How is this step accomplished? Can it be separated from Bubakup?

Thank you for your replies.

---

### Post by KubuntuKilledMe on 2007-08-30
(subscribing - sorry)

---

### Post by tuxcantfly on 2007-08-30
> **KubuntuKilledMe said:**
> I have some doubts about the fundamental working of this program, namelly the storage of bootable backup images.

I read that they are stored in a partition. Does that partition require a filesystem and mounting? If not, does a single backup image use up all of the partition? And if so, why are they called images if they are a partition backup onto another partition? I thought "image" was the word you used when the content doesn't match the form, as in storing a partition in a file which will reside in a filesystem over another partition.

Can this program be used live? As in backup the running root partition? That is a step ahead of partimage and very interesting on its own. In my humble opinion, more interesting that the whole "bootable" property of such backup images. How is this step accomplished? Can it be separated from Bubakup?

Thank you for your replies.

I think you misread the information. They are NOT stored in a partition, but rather in a file in a partition. That's why it's called a "loopmounted partition". I also refer to it as a "disk image" because loopmounted partitions are rather similar to .iso files (CD disk images), the only difference is the filesystem format; iso files are iso9660 format and these loopmounted partitions are ext3 format, but the fact that they are files containing a filesystem within themselves residing as files in another filesystem. So yes, your description "storing a partition in a file which will reside in a filesystem over another partition" is exactly what a loopmounted partition is; this program does NOT need its own partition to store each backup, it stores them in disk images.

The only reason the user is prompted to select a partition to save the backup to (which is what I assume led you to this conclusion) is because the booting mechanism for the disk images requires that the disk images reside in a folder in the top level of a filesystem, so a partition selector is used instead of a folder selector because the user would only have 1 folder on each partition (/bbk$date) to which the disk images can be saved to, so that's used simply to simplify the interface and for usability; however, the partition selected is not formatted or destroyed in any way; the new folder (/bbk$date) is simply created in the root directory of the selected partition and the disk images are stored within the directory.

And yes, the program can be used "live" (backup the running root partition). The step is accomplished by using rsync; if you need the specific commands and steps, just search through the source code at [https://launchpad.net/bubakup](https://launchpad.net/bubakup) for the "rsync" command.

---

### Post by KubuntuKilledMe on 2007-08-30
Thank you for your reply. It really wasn't making sense the way i first interpreted it. In light of it i have a couple more questions:

You mention a "booting mechanism for the disk images requires that the disk images reside in a folder in the top level of a filesystem". What other requirements does the booting mechanism have? Namelly what filesystems are supported for the backup storage partition? NTFS? 

I'm thinking that since i run dual boot with WinXP, using 2 hard drives, i could backup my small Linux root into the windows hard drive (with Bubakup and the new writable ntfs support) and backup the windows drive into the Linux disk (trivial with partimage). With exclusions to eliminate the obvious recursion problem.

Finally, can you backup the running root into itself, assuming enough free space?

---

### Post by tuxcantfly on 2007-08-30
> You mention a "booting mechanism for the disk images requires that the disk images reside in a folder in the top level of a filesystem". What other requirements does the booting mechanism have? Namelly what filesystems are supported for the backup storage partition? NTFS?

NTFS, FAT32, ext3, ext2, reiserfs, xfs, jfs (note that with FAT32 the backup can't be any more than 4 GB due to FAT32 size limitations)
> 
Finally, can you backup the running root into itself, assuming enough free space

yes
> 
I'm thinking that since i run dual boot with WinXP, using 2 hard drives, i could backup my small Linux root into the windows hard drive (with Bubakup and the new writable ntfs support) and backup the windows drive into the Linux disk (trivial with partimage). With exclusions to eliminate the obvious recursion problem.

yes

---

### Post by KubuntuKilledMe on 2007-08-30
Is there a way to restore an archived backup straight to a partition without restoring it to the loopmounted bootable state first?

---

### Post by tuxcantfly on 2007-08-30
> **KubuntuKilledMe said:**
> Is there a way to restore an archived backup straight to a partition without restoring it to the loopmounted bootable state first?

At the moment, no (the archives are simply the folder of the loopmounted bootable disk images compressed with 7z), though it could probably be done manually for now (loopmount the disk image, mount the target filesystem, rsync over, remove loopmounting patches, regenerate initrd), I'll try to get it implemented properly soon.

---

### Post by donald7777 on 2007-08-31
I created the backup, and it added the loopback to grub so i can boot from it. However when i select it the first one does not work. So i go to the second selection and i see the ubuntu splashscreen then it stalls. please any help. Ill post my grub menu.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 	10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black blink-light-green/black

#A splash image for the menu
splashimage=(hd0,3)/boot/grub/splashimages/matrix001.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$GyRO7$nz90opwBcrackZ8RIJ2Ff0/
# password topsecret
password --md5 $1$GyRO7$nz90opwBcrackZ8RIJ2Ff0
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
# kopt=root=UUID=349dc5ef-0e06-4b32-ba0a-45ff4459db7e ro

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
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=791

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=349dc5ef-0e06-4b32-ba0a-45ff4459db7e ro splash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
lock
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=349dc5ef-0e06-4b32-ba0a-45ff4459db7e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title Bubakup-20070830 # This line contains information for Bubakup-20070830
root (hd0,1) # This line contains information for Bubakup-20070830
configfile /bbk20070830/boot/grub/menu.lst # This line contains information for Bubakup-20070830


title Bubakup-20070830 # This line contains information for Bubakup-20070830
root (hd0,5) # This line contains information for Bubakup-20070830
configfile /bbk20070830/boot/grub/menu.lst # This line contains information for Bubakup-20070830


oh the partition the the bukakup is restored to is hda6 so im wondering if this is the problem 


title Bubakup-20070830 # This line contains information for Bubakup-20070830
root **(hd0,1)** # This line contains information for Bubakup-20070830
configfile /bbk20070830/boot/grub/menu.lst # This line contains information for Bubakup-20070830


title Bubakup-20070830 # This line contains information for Bubakup-20070830
root **(hd0,5)** # This line contains information for Bubakup-20070830
configfile /bbk20070830/boot/grub/menu.lst # This line contains information for Bubakup-20070830

---

### Post by tuxcantfly on 2007-08-31
hmm real strange that it created 2 menu entries, and the first one appears to point to the wrong place... (exactly what does data and filesystem does partition 2 of your hard drive contain anyhow, and where is it mounted? that menu entry isn't supposed to be there) the second one is right though (in grub numbering partition first partition is 0)

anyhow, I'd suggest removing the "splash" portion of the menu.lst on the grub configfile at /bbk20070830/boot/grub/menu.lst on /dev/hda6 (it'll be at the end of the kernel /bbk... etc... line), and trying booting it again that'll give some more useful info, if that still doesn't give anything, then also remove the "quiet" portion as well (in the same menu.lst file at  /bbk20070830/boot/grub/menu.lst), and post whatever output it gives...

also could you post  /bbk20070830/boot/grub/menu.lst on /dev/hda6 (mount it first if it isn't mounted yet), it might also be borked...

---

### Post by donald7777 on 2007-09-01
ok ill try that. ill post what happens. thankyou

---

### Post by donald7777 on 2007-09-01
ok here is my bubakup grub menu.lst


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

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
#      password --md5 //
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
# kopt=root=/dev/hda6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## ## End Default Options ##

title Ubuntu
root (hd0,5)
kernel /bbk20070830/boot/vmlinuz-2.6.20-16-generic find=/bbk20070830/boot/vmlinuz-2.6.20-16-generic ro
initrd /bbk20070830/boot/initrd.img-2.6.20-16-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
root (hd0,5)
kernel /bbk20070830/boot/vmlinuz-2.6.20-16-generic find=/bbk20070830/boot/vmlinuz-2.6.20-16-generic ro
initrd /bbk20070830/boot/initrd.img-2.6.20-16-generic
boot

---

### Post by donald7777 on 2007-09-01
ok it stalled out at detecting the usb hub (internal) than it continnued and ended up with this:

       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by tuxcantfly on 2007-09-01
hmm that's strange, the menu.lst looks fine, so it can't be that, are you by any chance using RAID (setups using RAID are really problematic to get working properly with this)? and did you need to use any particular hacks (noapic, noacpi, etc.) to get your original ubuntu install working normally?

anyhow, I'm kind of running out of ideas here, maybe it might have been some issue during the backup generation, maybe just delete your backup using the "delete backup" option, and create a new backup, only when doing so, run bubakup from the command line (gksudo bubakup) rather than from the menu, and post the output it gives on the terminal while generating the backup?

---

### Post by donald7777 on 2007-09-01
ok ill scrap it and remake it. thanks for your help.

---

### Post by skyttan on 2007-09-03
This look interesting! :D

I have always liked live systems you can boot up on more then one computer. Right now I am using PuppyLinux on my 1GB Corsair USB memory (and I'm pretty happy with that btw). If I have understood this right, can I use Bubakup to "copy" my system on a USB hard drive and boot from it on my computer with exactly the same enviroment? (only slower I understand) 
And what's more interesting, is this inplented in Ubuntu 7.10 ?! That would be awesome.... Stabile desktop-effects and "coopy-your-system-to-another-device-and-boot-from-it" ! :D

---

### Post by tuxcantfly on 2007-09-04
> I have always liked live systems you can boot up on more then one computer. Right now I am using PuppyLinux on my 1GB Corsair USB memory (and I'm pretty happy with that btw). If I have understood this right, can I use Bubakup to "copy" my system on a USB hard drive and boot from it on my computer with exactly the same enviroment? (only slower I understand)

Well that certainly wouldn't be too good for your USB drive's lifetime. Though it might work (haven't tried it myself though), I would just do that with a persistent filesystem and a livecd combo; it won't damage your USB drive that much and it'll be slightly faster, see [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

> And what's more interesting, is this inplented in Ubuntu 7.10 ?! 

It worked the last time I tried, yet then again, that was back in the early development stages of Gutsy; something might have broken sinice then

---

### Post by tuxcantfly on 2007-09-12
I've released a new build of bubakup, usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) primarily it fixes a couple of bugs relating to rsync copying in a loop and hanging up. Also, I tested bubakup on Gutsy Tribe5, and it works fine, for anybody who's wondering whether it works or not on Ubuntu 7.10.

---

### Post by tuxcantfly on 2007-10-03
I've found a very good use for Bubakup for anybody who's planning on upgrading to the soon-to-be-released Ubuntu 7.10 via the update-manager from 7.04 and is worried about breakage; simply make a bootable backup of your existing Ubuntu 7.04 system, then let the update manager upgrade your system, and should anything stop working in the new Ubuntu 7.10 install, simply boot the Bubakup option in GRUB and that'll let you access your system as it was prior to the update, and can optionally restore it back to the partition should you decide to return back to Ubuntu 7.04.

---

### Post by ByteDoc on 2007-10-04
Lucky enough I was to find this thread in the search results (searched for "image restore" ... seems to be just the thing I need.

Have a question regarding my system setup:

My partitions:
sda1 - swap
sda2 - root for Ubuntu1
sda3 - root for Ubuntu2
sda5 - home for Ubuntu1
sda6 - home for Ubuntu2
sda7 - shared partition

I created these partitions in order to always have a second partition setup with a second install, and now was looking for a way to easily use them in a way that one root-home-combo is the backup for the other, to keep me safe in case of upgrade woes, or to just simply be able to try out new packages/drivers on a test system.

Now Bubakup seems to be just that, would have saved me from creating the Ubuntu2-partitions as well.

My question is:
Can I create image from Ubuntu1-partitions and restore it to Ubuntu2-partitions, in order to use Bubakup as a kind of a system cloner?
Are there any adjustments necessary because of the different partitions (source and target)?
I assume I would have to adjust my /etc/fstab in which I mount the U2-partitions from my U1, and vice versa - but other than that, does Bubakup (or LVPM, or other parts of it) take care of any other partition differences/dependencies when restoring to a different target partition?

I'm finally having the system running in a way my wife is satisfied with it as well, so I'd like to be able to upgrade to Gutsy without investing too much time - and risk ;)

---

### Post by tuxcantfly on 2007-10-04
> **ByteDoc said:**
> does Bubakup (or LVPM, or other parts of it) take care of any other partition differences/dependencies when restoring to a different target partition?

yes, however, since it recursively copies the / filesystem and subfilesystems (such as a shared /home), if you only want to "clone" the /, when you're asked to exclude directories, you should exclude the directoreis within /home unless you want those to be copied over as well.

---

### Post by ByteDoc on 2007-10-05
Thx for your answer.

So if I don't exclude my /home, which is a mounted partition, it will get included in the image, and on restoring the image it would be copied into the folder /home instead of a mountpoint - I can live with that.

What if I changed my /etc/fstab to the configuration of my target partition system prior to creating the backup image (this image would be specifically created for this target partition) ...
Would that work, or does /etc/fstab get edited/changed during backup/restore process?

---

### Post by dakota34 on 2007-10-05
Hi I was excited to see this thread because Bubakup is exactly what I've been looking for.  Looks like a great tool, however I'm having a problem booting from the image created.  

I've created the backup succesfully, and have an item for the backup in my grub menu, however when I select that image it to boot I get 'Error 23' and something like 'error parsing number' (sorry I'm not at home now, can't duplicate it).

I've tried deleting the backup (through Bubakup) and recreating, with the same result - image gets created with no problem, item appears in boot menu, but I can't boot from it.

Not sure if it's relevant, but I'm dual booting with XP, XP being on hda, Ubuntu on hdb, and partition for Bubackup image on hdd.

Any suggestions would be appreciated.

---

### Post by tuxcantfly on 2007-10-06
> **ByteDoc said:**
> Thx for your answer.

So if I don't exclude my /home, which is a mounted partition, it will get included in the image, and on restoring the image it would be copied into the folder /home instead of a mountpoint - I can live with that.

What if I changed my /etc/fstab to the configuration of my target partition system prior to creating the backup image (this image would be specifically created for this target partition) ...
Would that work, or does /etc/fstab get edited/changed during backup/restore process?

The /etc/fstab file gets changed during the backup/restore process, though you could always just mount the disk image (mount -o loop file.virtual.disk /media/somemountpoint) and copy the file over

---

### Post by ByteDoc on 2007-10-09
Tried to boot from a created backup, gives me "Error 15: File not found".

The file in the backup directory does only contain timestamp (20071009), is that ok?

Any idea why it does not work?
Backup resides in a logical partition, not a primary one - is that important?

ADDED:
contents of the backup directory /bbk20071009/ ...
./bbktimestmp-20071009
./disks/system.virtual.disk

There should be more to this, at least the grub-menu-file listed in the grub-file from my "real" ubuntu.
What is missing here?

---

### Post by tuxcantfly on 2007-10-09
> **ByteDoc said:**
> Tried to boot from a created backup, gives me "Error 15: File not found".

The file in the backup directory does only contain timestamp (20071009), is that ok?

Any idea why it does not work?
Backup resides in a logical partition, not a primary one - is that important?

ADDED:
contents of the backup directory /bbk20071009/ ...
./bbktimestmp-20071009
./disks/system.virtual.disk

There should be more to this, at least the grub-menu-file listed in the grub-file from my "real" ubuntu.
What is missing here?

Strange... I've tested on logical partitions, and it worked fine... anyhow, what you're missing is apparently the entire /boot directory in the backup, so just loopmount your system.virtual.disk (sudo mount -o loop /bbk20071009/disks/system.virtual.disk /media/somemountpoint), then go to /media/somemountpoint and copy the directory /boot to /bbk20071009/boot and replace /bbk20071009/boot/grub/menu.lst with the menu.lst attached (adjust the end part to suit your partitions, in the root (hd0,5) bit) it should then work... If it doesn't, try unmounting the target partition before backing up (or if it wasn't mounted, try having it mounted), it might work then...

---

### Post by Garibaldi3489 on 2007-10-16
Hello,

I'm very excited about bubakup as a server diagnostic/recovery tool. I have successfully made a backup and booted into it from bubakup on my Ubuntu Feisty system. I have used [http://uck.sf.net](http://uck.sf.net) to customize the Feisty live-cd/iunstall cd by installing the bubakup and lvpm packages. I would then like to transfer my archived backup over to this custom live-cd, restore it, and then burn the live-cd (or rather live-dvd now) so that I can boot into it and use the normal ubuntu environment as a diagnostic and also boot into/restore the bubakup image. I have gotten as far as copying the archived backup into the custom live-cd, however when I run bubakup in that environment, it does not give any paths/drives to restore the archive to:
[img]http://img222.imageshack.us/img222/7241/shotks9.png[/img]
My fstab is blank since this is a "live-cd" although I could add a line to it. What can I do to get this to work? If necessary, could you tell me the files/modifications that bubakup makes and I could make them manually, rather than archiving/unarchiving the backup.

Thanks

---

### Post by tuxcantfly on 2007-10-16
> **Garibaldi3489 said:**
> Hello,

I'm very excited about bubakup as a server diagnostic/recovery tool. I have successfully made a backup and booted into it from bubakup on my Ubuntu Feisty system. I have used [http://uck.sf.net](http://uck.sf.net) to customize the Feisty live-cd/iunstall cd by installing the bubakup and lvpm packages. I would then like to transfer my archived backup over to this custom live-cd, restore it, and then burn the live-cd (or rather live-dvd now) so that I can boot into it and use the normal ubuntu environment as a diagnostic and also boot into/restore the bubakup image. I have gotten as far as copying the archived backup into the custom live-cd, however when I run bubakup in that environment, it does not give any paths/drives to restore the archive to:
[img]http://img222.imageshack.us/img222/7241/shotks9.png[/img]
My fstab is blank since this is a "live-cd" although I could add a line to it. What can I do to get this to work? If necessary, could you tell me the files/modifications that bubakup makes and I could make them manually, rather than archiving/unarchiving the backup.

Thanks

So apparently what you want to do is have a liveCD from which you can boot and restore the backup, right? What I'd do is instead of storing the archive file on the backup, just store it there in its uncompressed state; it'll be compressed anyhow by squashfs during the livecd remastering process. If you want the nitty-gritty on which files are changed and how (you'll probably need to do some changes here and there, since you want to have it booting out of a liveCD environment not a hard drive so I can't give you concrete instructions), see the source (links below).

You can see the process by which the backups are restored through the section that begins with "Restore backup" in
[http://codebrowse.launchpad.net/~gezakovacs/bubakup/devel/annotate/geza0kovacs%40gmail.com-20070912070421-dgyvnjb3ipqeswkm?file_id=bubakup-20070824034412-rx8h4rzma6kvnkl1-10](http://codebrowse.launchpad.net/~gezakovacs/bubakup/devel/annotate/geza0kovacs%40gmail.com-20070912070421-dgyvnjb3ipqeswkm?file_id=bubakup-20070824034412-rx8h4rzma6kvnkl1-10)

As for restoring the backup to a hard drive, see [http://codebrowse.launchpad.net/~gezakovacs/lvpm/devel/annotate/geza0kovacs%40gmail.com-20070905202434-l2r4yxcmn08np5hq?file_id=lvpm-20070701182908-k31jsn93s8nh40ls-6](http://codebrowse.launchpad.net/~gezakovacs/lvpm/devel/annotate/geza0kovacs%40gmail.com-20070905202434-l2r4yxcmn08np5hq?file_id=lvpm-20070701182908-k31jsn93s8nh40ls-6)

Also, if that approach is too confusing, another way that might be easier is to just follow the Ubuntu liveCD remastering process at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) and copy-paste over the parts of your install you want into the uncompressed squashfs directory before compressing it (your /home directory and other files you need backed up), that'll get the same goal accomplished; if you want to restore the backup, you can just use the "install" button from the liveCD and it'll restore it to a hard drive.

---

### Post by Pay87 on 2007-10-21
First of all thank you for this great app.
I just have some problems.
These are my partitions:
[IMG]http://img81.imageshack.us/img81/7653/partitionspj6.jpg[/IMG]
I created a backup and excluded as suggested /proc and /sys, why should I exclude them?
Furthermore i excluded /media/backups, /media/dateien and /media/virtuelles.
These are partitions where i store different stuff.
In the  /media/backups folder i store my backups.
When i now try to boot my backup i get a "Error 21".
Is there a way to solve this problem?
If i get it to boot, what happens if i make changes in the backup system, are they saved?
Do I have to format the root partition or does your app do this for me automatically while restoring?
And if my main system crash and i format the root partition is there a way to restore it from booting in the backup system?
I found another bug, too.
In some steps when you press cancle it doesn't cancle and shows you the same step again. :)

---

### Post by tuxcantfly on 2007-10-22
> I created a backup and excluded as suggested /proc and /sys, why should I exclude them?

/proc and /sys aren't actual physical files/folders on your hard drive, they're autogenerated on boot and are stored in RAM (therefore it's unnecessary to back them up)

> When i now try to boot my backup i get a "Error 21".

Edit /boot/grub/menu.lst and /boot/grub/menu-bbksomething.lst and change the "root (hd0,6) to root (hd0,5) on the bubakup entry (it's because you're using a separate /boot partition which I hadn't designed the program for; it's looking in / for the kernel/initrd files)"

> If i get it to boot, what happens if i make changes in the backup system, are they saved?

Yes

> Do I have to format the root partition or does your app do this for me automatically while restoring?

It's done automatically

> And if my main system crash and i format the root partition is there a way to restore it from booting in the backup system?

Assuming your /boot partition is still intact, it will still boot from GRUB, and if GRUB gives you errors, just try using the Super Grub Disk [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) that'll let you select the backup to boot from.

> I found another bug, too.
In some steps when you press cancle it doesn't cancle and shows you the same step again. :)

Sorry, it's a result of using zenity dialogs within while loops (otherwise it would set those variables at null if cancel is pressed); there's no real good workaround other than what I'm using (provide an additional exit option), only real way to fix it would be to use a "proper" GUI library like gtk/qt rather than zenity (which would take quite some time to do).

---

### Post by Pay87 on 2007-10-22
Thank you for this quick and detailed reply! :)

I have a last question:
When I restore the backup will bubakup put the files which are normally stored on my boot and home partition back on the right place and partition?
As you said it wasn't designed for that case, so that is the last point i worry about when i restore a backup which orginally backuped from the different partitions. :)

---

### Post by tuxcantfly on 2007-10-22
> **Pay87 said:**
> Thank you for this quick and detailed reply! :)

I have a last question:
When I restore the backup will bubakup put the files which are normally stored on my boot and home partition back on the right place and partition?
As you said it wasn't designed for that case, so that is the last point i worry about when i restore a backup which orginally backuped from the different partitions. :)

Everything's restored to the same, single partition (/), even if they were in seperate partitions when backed up. The contents of /boot and /home and everything else except that which was excluded will be restored to the partition.

---

### Post by Pay87 on 2007-10-22
Great thank you! ;)
Hopefully you don't stop to develope the software soon.
Didn't found a other graphical solution yet.
Try to make your software more popular! :popcorn:

---

### Post by Pay87 on 2007-10-23
> **tuxcantfly said:**
> 
Edit /boot/grub/menu.lst and /boot/grub/menu-bbksomething.lst and change the "root (hd0,6) to root (hd0,5) on the bubakup entry (it's because you're using a separate /boot partition which I hadn't designed the program for; it's looking in / for the kernel/initrd files)"

I tried to but still doesn't work.
Here my /boot/grub/menu.lst

```


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=18b15dd4-f3a4-4294-9608-a1428b65ec61 ro quiet splash locale=de_DE
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=18b15dd4-f3a4-4294-9608-a1428b65ec61 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



title Bubakup-20071023 # This line contains information for Bubakup-20071023
root (hd1,0) # This line contains information for Bubakup-20071023
configfile /bbk20071023/boot/grub/menu.lst # This line contains information for Bubakup-20071023



```

And here my /media/backup/bkk../boot/grub/menu.lst
```

## ## End Default Options ##

title Ubuntu
root (hd1,0)
kernel /bbk20071023/boot/vmlinuz-2.6.22-14-generic find=/bbk20071023/boot/vmlinuz-2.6.22-14-generic ro quiet splash
initrd /bbk20071023/boot/initrd.img-2.6.22-14-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
root (hd1,0)
kernel /bbk20071023/boot/vmlinuz-2.6.22-14-generic find=/bbk20071023/boot/vmlinuz-2.6.22-14-generic ro quiet splash
initrd /bbk20071023/boot/initrd.img-2.6.22-14-generic
boot

```

This is what Bubakup created..

---

### Post by Odd-rationale on 2007-10-23
Hello! I'm having trouble booting Bubakup.

From the GRUB menu, I select

```
Bubakup-20071023 # This line contains information for Bubakup-20071023
```

But then I get

```
Error 17: Cannot mount selected partition

Press any key to continue...
```

I press any key and it takes me back to the boot menu.

Your help is greatly appreciated!

---

### Post by tuxcantfly on 2007-10-23
> **Pay87 said:**
> I tried to but still doesn't work.
Here my /boot/grub/menu.lst

```


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=18b15dd4-f3a4-4294-9608-a1428b65ec61 ro quiet splash locale=de_DE
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=18b15dd4-f3a4-4294-9608-a1428b65ec61 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



title Bubakup-20071023 # This line contains information for Bubakup-20071023
root (hd1,0) # This line contains information for Bubakup-20071023
configfile /bbk20071023/boot/grub/menu.lst # This line contains information for Bubakup-20071023



```

And here my /media/backup/bkk../boot/grub/menu.lst
```

## ## End Default Options ##

title Ubuntu
root (hd1,0)
kernel /bbk20071023/boot/vmlinuz-2.6.22-14-generic find=/bbk20071023/boot/vmlinuz-2.6.22-14-generic ro quiet splash
initrd /bbk20071023/boot/initrd.img-2.6.22-14-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
root (hd1,0)
kernel /bbk20071023/boot/vmlinuz-2.6.22-14-generic find=/bbk20071023/boot/vmlinuz-2.6.22-14-generic ro quiet splash
initrd /bbk20071023/boot/initrd.img-2.6.22-14-generic
boot

```

This is what Bubakup created..

What's the partition that the backup is stored on? It appears to be looking in /dev/sdb1, change the root option to wherever it is (ex. if it's in /dev/sda4 it should be (hd0,3), etc.

What's the error message, also? Is it the error 17 or something else?

@ Odd-rationale: same thing, try changing the menu.lst as described above

---

### Post by mkstowegnv on 2008-01-04
Hi, thanks for all the work.  I installed kubuntu with Wubi 2 days ago and after a solid day of work had finished customizing it and adding programs.  Then I tried a keyboard shortcut for 'halting' and did some kind of subtle but serious damage.  It now goes most of the way through booting but hangs in an unresponsive (well it 'echoes' - ESC = ^]) console-like state.  By rebooting and hitting escape at the right point I can choose a kernel and proceed which ends in a fully functional command line.  x, kde-init and therefore every gui app will not run (my knowledge of linux is superficial).   The XP host is fine.  

I would love to use bubakup to restore to another loop mounted or real partition hoping this cures whatever my problem is (my goal is K on a real partition).   But I do not know enough to install bubakup from the command line, and how I would use it if X is not running.  To be honest I do not understand your instructions for using it to rescue an unbootable loop mounted system - I am probably misunderstanding something very basic.  Thanks and best wishes, Mark

---

### Post by tuxcantfly on 2008-01-04
> **mkstowegnv said:**
> Hi, thanks for all the work.  I installed kubuntu with Wubi 2 days ago and after a solid day of work had finished customizing it and adding programs.  Then I tried a keyboard shortcut for 'halting' and did some kind of subtle but serious damage.  It now goes most of the way through booting but hangs in an unresponsive (well it 'echoes' - ESC = ^]) console-like state.  By rebooting and hitting escape at the right point I can choose a kernel and proceed which ends in a fully functional command line.  x, kde-init and therefore every gui app will not run (my knowledge of linux is superficial).   The XP host is fine.  

I would love to use bubakup to restore to another loop mounted or real partition hoping this cures whatever my problem is (my goal is K on a real partition).   But I do not know enough to install bubakup from the command line, and how I would use it if X is not running.  To be honest I do not understand your instructions for using it to rescue an unbootable loop mounted system - I am probably misunderstanding something very basic.  Thanks and best wishes, Mark

Sounds like what happened was the typical filesystem corruption issue that occurs rather often on Wubi-generated installs.

See [https://wiki.ubuntu.com/WubiGuide?action=show#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide?action=show#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)  I've updated the instructions, they should hopefully be more clear (I presume these are the instructions you are referring to)

If the part you didn't understand was what to do with the commands, you first boot the Ubuntu desktop CD, and you enter the commands into a terminal (Applications -> Accessories -> Terminal).

If you part you didn't understand was what they each do, these commands create mountpoints and mount the existing NTFS partition to /media/windows:

```
sudo mkdir /media/windows
sudo mkdir /media/wubi
sudo ntfs-3g $(sudo fdisk -l | grep NTFS | head -1 | sed 's/\t/\n/g' | sed 's/ /\n/g' | grep /dev) /media/windows
```

And these check the loopmounted disk image filesystems for errors (for Wubi 7.04).

```
sudo fsck /media/windows/wubi/disks/system.virtual.disk
sudo fsck /media/windows/wubi/disks/home.virtual.disk
```

(For Wubi 7.10)

```
sudo fsck /media/windows/ubuntu/disks/root.disk
sudo fsck /media/windows/ubuntu/disks/home.disk
```

If you execute those commands, it should repair the filesystem corruptions.

Otherwise, if it still doesn't work, then the issue is more than just filesystem corruption, and there could be a variety of different issues. Since this is a relatively fresh install, I'd recommend just backing up whatever you have:

> Then mount the virtual disks, once the filesystems have been checked and repaired. If using Wubi 7.04, use these commands:

```
sudo mount -o loop /media/windows/wubi/disks/system.virtual.disk /media/wubi
sudo mount -o loop /media/windows/wubi/disks/home.virtual.disk /media/wubi/home
```

Otherwise, if using Wubi 7.10, use these commands:

```
sudo mount -o loop /media/windows/ubuntu/disks/root.disk /media/wubi
sudo mount -o loop /media/windows/ubuntu/disks/home.disk /media/wubi/home
```

Now you'll be able to access your wubi filesystem in /media/wubi read-write; your home dir will be in /media/wubi/home, and /media/wubi for the wubi root filesystem. You'll probably need to have root access to modify some files, so to open the filemanger with root privs:

```
gksudo nautilus /media/wubi
```


Then, if all else fails, just back up your files to a USB drive or somewhere using the instructions above, and do a clean re-install, directly to a dedicated partition (this will save you the hassle of transferring to a dedicated partition later on), using UNetbootin instead of Wubi (if your reason for using Wubi in the first place was a lack of a CD, otherwise just use the standard Ubuntu CD install), and restore back the config files you backed up (they're in the /home/username directory, they're hidden files starting with a period, press Ctrl-H in the file manager to show them). [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

And FYI, to install a .deb from the terminal, use "sudo dpkg -i ./file.deb" if you've already downloaded it, or "sudo apt-get install package" if it's in the repositories, though it won't help in this case (the install is broken, transferring it to a dedicated partition won't help fix it)

---

### Post by mkstowegnv on 2008-01-04
Thanks so much for your quick reply.  I have not yet tried to repair with fsck, etc.  I gather that if I can't get it back to a bootable state, I won't be able to use bubakup to rescue what I have.   It is not just the config information I fear losing but the hours I spent eventually getting flash to work on konqueror, jre on firefox and opera, and the surveillance app zoneminder installed (it was so arduous and twisted that I am now sure I can reproduce it all.)

Part of my confusion was that I had leaped to what I now assume is an incorrect assumption (from your mention of its use for rescue in the summary), ie that there is some way to use a running live CD and either use a copy of bubakup installed on that CD or do a fresh install  on the hard drive (using it to back up or copy an unbootable loop mounted system on the main drive).   Thanks again for your help.  Mark

---

### Post by Naraltd on 2008-02-29
Hi thanks for the awesome product.

I am curious if you think it would be of benefit for what I am wanting to do.

Where I work we are not allowed to install anything on our PCs.  So I removed the internal HD, and installed Ubuntu 7.10 on an external usb drive.  I replaced the internal drive and set the boot order to usb then hd.

Now I boot into Ubuntu when I plug in my external drive.  While this is working, the usb drive is just slow.

I would love to take an image of the usb drive and put it on the ntfs partition as a regular file.  Then have a small usb key used only as my boot loader.

I looked at Wubi but I effectively want a stealth install w/o having to drag around an external usb hd.  

Thanks in advance!

---

### Post by tuxcantfly on 2008-03-03
> **Naraltd said:**
> Hi thanks for the awesome product.

I am curious if you think it would be of benefit for what I am wanting to do.

Where I work we are not allowed to install anything on our PCs.  So I removed the internal HD, and installed Ubuntu 7.10 on an external usb drive.  I replaced the internal drive and set the boot order to usb then hd.

Now I boot into Ubuntu when I plug in my external drive.  While this is working, the usb drive is just slow.

I would love to take an image of the usb drive and put it on the ntfs partition as a regular file.  Then have a small usb key used only as my boot loader.

I looked at Wubi but I effectively want a stealth install w/o having to drag around an external usb hd.  

Thanks in advance!

Either this or Wubi should be able to do the job equally well; in both situations you'll end up with a bootable disk image, initrd, and kernel. Since you can't install directly on your PC, do the installation on a different computer, then just transfer over the disk image files, they should work fine. As for the bootloader portion, see here: [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Install_GRUB_for_DOS_boot_code_to_MBR](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Install_GRUB_for_DOS_boot_code_to_MBR) that'll get the grub4dos bootloader (others, like standard GRUB or syslinux, should also work, but GRUB4DOS should be easier to install/use) installed on your external media (again, you'll have to do the bootloader installation on a different computer).

So, in a nutshell, get GRUB4DOS installed on your USB drive, copy over the disk image to c:\wubi\disks, copy the initrd/kernel files (you'll find them within the wubi subdirectory) over to the USB drive for booting, and copy over menu.lst (also in the wubi subdirectory) over to the USB drive, and it will hopefully work. Note that I haven't actually tested this, so your mileage may vary.

---

### Post by evilc on 2008-03-03
Being new to linux I have been looking for a backup/image program incase I stuff up while trying different things and Bubakup is just what I need.

I have installed Bubakup and created a backup using just the default settings, I put the backup on my 2 HD and then rebooted to test it. I selected from grub the Bubakup and Ubuntu splash screen started then froze for about 4 minutes, it the changed to blank screen (old dos style) with Busybox........... (initramfs).
From that point I have no idea what to put in, I typed help but that only gives commands. I have attached my   grub menu in case theres something wrong to see.

---

### Post by uMuppet on 2008-07-17
This program looks almost perfect for what I need.
I have tested it a few times by doing a backup and then booting into it from the grub menu, then doing a restore.  All seems to work fine but I can only do it one.  Once it is restored the old data is lost.  
I wanted to make a "forever restore point" that I can always start from again.   Any ideas?

When booting into the restore files from grub can I put a shortcut on the desktop with predefined options that will do all the restoring for me?  I can't see any command line options for this program.  
Better yet would be choosing the grub option and automatically restoring the partition completely and then booting up as normal.  This way even a monkey can restore a broken system.

Thanks for your help.

---

### Post by bluzit on 2008-07-27
Used this but the backup wouldn't boot. The orange progress bar just kept going back and forth. I got it to reboot into my regular system but the backup is not accessable. It said to not include some files at the beginning and I said ok, maybe something was needed to boot. I am quite new to Ubuntu but I like it a lot.  bluzit:guitar: Oh, and I wanted to thank you very much for the time you invest in your program. Thanks a ton!
 Are we supposed to put the backup in the root partition? I have tried that twice and it won't boot. I give up.

---

### Post by steveparbkk on 2009-03-31
Hi This is a great utility.  I'm particularly interested in creating a sandbox environment for testing changes I want to make to my configuration.

I have two issues, the first is the same as:

> **dakota34 said:**
> 
I've created the backup succesfully, and have an item for the backup in my grub menu, however when I select that image it to boot I get 'Error 23' and something like 'error parsing number' (sorry I'm not at home now, can't duplicate it).

I've tried deleting the backup (through Bubakup) and recreating, with the same result - image gets created with no problem, item appears in boot menu, but I can't boot from it.


I'm using an EeePC 901 with Ebuntu standard on an SD card and backing up to a USB stick.

Initially I thought the issue was the USB stick that I am backing up to and so reformatted it as ext2 without first deleting the initial failed backup in bubakup.  Consequently the first failed backup still shows in the grub menu.  As the backup no longer exists how can I get rid of the non-existent backup from the grub menu?

Also, any ideas why I'm getting 'Error 23'?  I didn't see any response to dakota34 that answered that question.

I really hope this app is still being developed, it's a very useful concept.

Thanks for your help and for the hard work!

---

### Post by Perkins on 2009-05-22
I am running 9.04.  From what I understand of how bubakup works, I'm pretty sure it will function.  Sure enough to test it anyway.  However, my machine has a Dell raid controler, and while the fact that the root partition is /dev/mapper/isw_cdhbgbheeg_Volume01 is properly detected, I only have the options to save the backup onto /dev/sd[ab][123].  

So, since the documentation for this program seems to be sparse to non-existent, I have to ask:

a)  Would it work if I simply created a symbolic link to the mapper device in the /dev directory.  [COLOR="Red"]NO[/COLOR]
b)  Will it actually work with dmraid devices properly, without screwing up my machine?
c)  Are there any updates planned in the near future to help out people like me?

---

### Post by danderson3 on 2011-04-08
what is the status of this, since there has been no activity for so long?
How about loopmounting changes since this was written?

---

### Post by Perkins on 2011-04-09
Unfortunately I am no longer managing that particular machine, so I'm afraid I've been unable to test it.

---

### Post by danderson3 on 2011-04-11
Does bubakup work with 10.10 and 11.4 Ubuntu?

---

