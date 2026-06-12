---
title: "HOWTO: Moving/Copying Windows XP to another Partition"
date: 2008-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by habicht on 2008-09-10
The following is mainly based on Michael Dominok's tutorial on how to fork an XP installation with Linux [1] who gives more details than I do here. Details on how to move a partition using Windows can be found in [2].

**_PROBLEM_**

I wanted to copy my entire system, including both a Ubuntu and a Windows XP partition to a new, bigger harddrive and change the order of partitions. I used my old harddrive in an external USB case (/dev/sdb), the new one was installed in my laptop.

**_PROCEDURE_**

There are many tutorials on how to copy a Linux partition (e.g. with live CD Ubuntu or Knoppix). Summary: create partition with fdisk or gparted, copy partition using "dd if=/dev/sdb1 of=/dev/sda2" (sdb1=source, sda2=destination), use "resize2fs /dev/sda2" to adapt the partition to its new size (if target partition is bigger than source), adapt "/boot/grup/menu.lst" on target partition and (re-)install grub properly.

To move a Windows XP installation is a little more work but still easy if you know what to do. My XP partition was to be moved from /dev/sdb1 to /dev/sda2. A prerequisite for the following steps is that the target partition has been created already, e.g. using fdisk or gparted. You can perform the following steps by using the already installed Linux.


**1. Prepare Windows XP**

You NEED to reset Window's information about mounted partitions before you move it! Use "regedit" and delete all entries in 
"HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices". This does not harm Windows since Windows rebuilds these entries on the next startup.

Since I forgot to do this at first, I had to do this as a last step. I exchanged the harddisks again and booted the "old" Windows installation. Here, I did the regestry editing as described above. Then I exchanged the harddisks again and copied the relevant registry file from the old to the new partition, which is C:\Windows\system32\config\system. You might want to do a backup of the old "system" file, just in case.

In case you forgot the above step:

*Method 1 - the Windows way:*
Since I forgot to do this at first, I had to do this as a last step. I exchanged the harddisks again and booted the "old" Windows installation. Here, I did the registry editing as described above. Then I exchanged the harddisks again and copied the relevant registry file from the old to the new partition, which is C:\Windows\system32\config\system. You might want to do a backup of the old "system" file, just in case.

*Method 2 - the Linux way:*
I could not find a way how to modify the registry by using "wine", but you can use "chntpw" (apt-get install chntpw) which is a simple opensource command line registry editor ("?" gives help output):
```
chntpw <PATH-TO-WINDOWS>/system32/config/system
ls
cd MountedDevices
ls
delallv
q
```

I could not find a way how to modify the registry by using "wine".


**2. Copy the Windows Partition**

In [1], ntfsclone is used. Alternatively, you can use gparted. I simply used "dd". This takes a while and doesn't produce any output, so don't wonder:

```
dd if=/dev/sdb1 of=/dev/sda2
```


**3. Modify Windows Boot sectors**

Taken from [1]:
Now, the boot-sectors of the newly cloned XP-partition have to be
modified. The partition(s) in front of the new ones have to be
"skipped". This is done by inserting an offset into the partitions
boot-sector. But first we've got to determine where they start. "fdisk
-ul /dev/hda" shows:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/hda2        40965750    81979694    20506972+   7  HPFS/NTFS
/dev/hda3        81979695   122993639    20506972+   7  HPFS/NTFS
/dev/hda4       122993640   181582694    29294527+   5  Extended
/dev/hda5       122993703   181582694    29294496   83  Linux
```

The interesting values are listed in the "Start"-column but have to be
converted into hexadecimal and rearranged in order. "printf "0x%llx\n"
40965750" printfs 40965750 in hexadecimal format "0x2711676"
"printf "%x" 40965750" would have done, too.
The hexadecimal value "2711676" has to be rearranged further. The digits
have to skewed by pairs following this method: "0xABCDEFGH => GH EF CD AB"
For "2711676" this results in "76167102"
Since we've got 4 pairs to skew but only 7 digits available we simply
add a leading 0. This is as neutral in the hexadecimal system as it is
in the more familiar decimal system.
Now "76167102" has to be inserted into hda2s boot-sector. That's done
with "hexedit /dev/hda2"
Move the cursor to position "0x1c" and type in "76 16 71 02", then
save&quit with "<STRG>-X"

If you copied the source partition to a bigger destination partition, a resizing of the file system is necessary. This is described further down in point 6.


**4. Adapt Boot Manager "grub"**

If the partition number has changed (e.g. you copied from partition number 3 to 2 (counting from 1, independent of the disk), edit /boot/grub/menu.lst and add or set the right partition for the windows installation, which is (h0,1) for /dev/sda2 (disk 0, partition 1), in my case:

```
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```


**5. Adapt Window's BOOT.INI**

What has been done for the grub menu needs to be done for Window's boot loader as well. Mount the new Windows partition (/dev/sda2 in my case) and edit c:\BOOT.INI to use the right partition number which is "partition(1)" in my case (for /dev/hda2, [1] uses partition(2) though):

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP on sda2" /fastdetect
/NoExecute=OptIn
```


**6. Adapting the file system size to the partition (resizing)**

ntfsresize is an opensource tool to resize ntfs partition in Linux. This should NOT be used at this point. Using this tool can render your windows partition unusable. I don't know the exact reason, but when I applied it, a user session was immediately logged out after logging in to windows. Several attempts to solve this problem did not succeed (replacing userinit.exe, checking userinit.exe registry entry, renaming the disk ID with hexedit ("disk has been before"-effect)). I cannot tell whether this only happend because I forced the ntfsresize (-f -b), although ntfsresize gave warnings about bad sectors.

The windows partition should be able to boot by now. The last step is to boot windows and execute:
```
chkdsk /f /r"
```
Windows will tell you that it needs to reboot to execute this step. chkdsk removes all existing ntfs inconsistencies and resizes your file system to the partition size.


**7. Done**


Enjoy! I hope it works for you as nicely as it worked for me.



[1] Michael Dominok: "How to fork a XP-installation", 2005, [www.dominok.net/en/it/en.it.clonexp.html](www.dominok.net/en/it/en.it.clonexp.html)
[2] "Move an entire Windows installation", [http://winhlp.com/node/66](http://winhlp.com/node/66)

---

### Post by Predator106 on 2008-09-10
:Request move to Tutorials/Tips section, it's not meant to be here:

Nice tutorial, however.

---

### Post by cyrylski on 2009-08-06
Worked for me, thank you very much :)

However, I had to skip step 3 as I could not locate line 0x1C in the editor for some reason.

---

### Post by jmbneaf on 2009-10-07
Awesome - just what I needed - works great!!

Be sure to read the directions carefully on step #3.   I got hung up on this and once I did it correctly - no problems!

~J

---

### Post by petermck on 2009-10-25
Hi,
Great tutorial. I encountered the login/logout loop problem you describe in (6), but used the chntpw code in (1) to fix it.
What I did (before seeing this tutorial) was create a new ntfs partition on a different HDD using Partition Editor in Ubuntu 9.04 and then simply dd it across. I modified the Grub menu.1st file accordingly and booted into windows. Everything worked fine, so back in Ubuntu I used Partition Editor to delete the old windows boot partition (C: in windows), resized and moved the other ntfs patition (D: in windows) to tidy things up and re-booted.
This all worked without a hitch. Windows would boot and present a login screen, but when I logged in it would flash that it was applying user settings and then log off. Safe Mode was the same, but using the code for chntpw in (1) fixed it.
Thanks heaps. I would be interested to know if someone could shed some light on why this happens. It seems a bit weird that windows would boot, but because the volume information in the MountedDevices key in regedit is out of date it won't log in.

---

### Post by oramd on 2009-10-25
ya great tips... it works i applied .. i forgot some steps in starting  .but after that that it worked ..thanks for sharing

---

### Post by www.rzr.online.fr on 2009-12-06
Great I'll test it next time I'll move a windows partition, can this be done by moving the files vs the whole partition ?

Also a script/tool that does thoses steps would be helpful too

-- 
[http://rzr.online.fr/q/part](http://rzr.online.fr/q/part)

---

### Post by rijidij on 2010-03-03
Hello. Thanks for this tutorial.
Unfortunately, I have come up against a brick wall and need some help.

I recently upgraded my PC and want to migrate my partitions from my old IDE disk to a 500GB SATA.

I had no problems at all moving my Ubuntu partition, but XP is causing me no end of trouble.
It is a matter of principle (and bull-headedness) to **not** have Windoze in the primary partition. 
It's getting pretty old now and I'd like to get rid of it soon anyway. But unfortunately, for the time being I need it for work.

I created a NTFS partition, using fdisk. Then copied the partition across using dd.
I modified the boot sectors as per step 3, then ran update-grub2.

Step 5 had me stumped for a while. My XP partition is #3 but, because I have an extended partition at #2, I had to set BOOT.INI to (2).

I can now get to the Windows bootloader, but no matter what selection I make, a message on a blue screen flashes up (too briefly to read what it says) then the computer reboots.

Please help, I am almost at my wits end. :confused:


I have attached my fdisk and Bootinfo script output, if that helps..


```
craig@Ximinez:~$ sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24859   199679886   83  Linux
/dev/sda2           24860       25496     5116702+   5  Extended
/dev/sda3   *       25497       30673    41583616+   7  HPFS/NTFS
/dev/sda4           55702       60801    40965750    7  HPFS/NTFS
/dev/sda5           24860       25496     5116671   82  Linux swap / Solaris

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       79312841 sectors, but according to the info from 
                       fdisk, it has 83167232 sectors.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /IO.SYS /MSDOS.SYS

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ad666

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   399,359,834   399,359,772  83 Linux
/dev/sda2         399,359,835   409,593,239    10,233,405   5 Extended
/dev/sda5         399,359,898   409,593,239    10,233,342  82 Linux swap / Solaris
/dev/sda3    *    409,593,240   492,760,472    83,167,233   7 HPFS/NTFS
/dev/sda4         894,836,565   976,768,064    81,931,500   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8d4327d9-e39c-4827-987a-6a5bb1f91393   ext4       Ubuntu                        
/dev/sda3        465C0C6D5C0C5A57                       ntfs       XP                            
/dev/sda4        F6F0B117F0B0DF55                       ntfs       NTFS                          
/dev/sda5        20c67cf5-2515-4db1-80f1-1fcbe2b036c6   swap       swap                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8d4327d9-e39c-4827-987a-6a5bb1f91393 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8d4327d9-e39c-4827-987a-6a5bb1f91393

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=8d4327d9-e39c-4827-987a-6a5bb1f91393 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=8d4327d9-e39c-4827-987a-6a5bb1f91393 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8d4327d9-e39c-4827-987a-6a5bb1f91393 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8d4327d9-e39c-4827-987a-6a5bb1f91393 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		8d4327d9-e39c-4827-987a-6a5bb1f91393
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=white/black
  set color_highlight=light-red/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8d4327d9-e39c-4827-987a-6a5bb1f91393
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 465c0c6d5c0c5a57
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1	/               ext4    errors=remount-ro 0       1
/dev/sda2	none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# ReadyNAS
//readynas/media /media/readynas cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

# Rio Karma DAP
#/dev/disk/by-id/usb-Rio_Rio_Karma_0000000000000000-part2    /media/karma    omfs    fmask=0133,dmask=022,user,noauto    0   0

=================== sda1: Location of files loaded by Grub: ===================


   1.6GB: boot/grub/core.img
   1.6GB: boot/grub/grub.cfg
   3.8GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-17-generic
   1.3GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-17-generic
   1.1GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: initrd.img
    .8GB: initrd.img.old
   1.1GB: vmlinuz
    .6GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```


Thanks,
Craig

---

### Post by bosson on 2010-03-12
Craig, I have the same problem, did you solve yours. The message just after passing the xp boot.ini menu is referring to the windows documentation for more information. 

My setup is perhaps even more odd than yours: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2       15299   122881153+   7  HPFS/NTFS
/dev/sda6   *       15300       28047   102398278+   7  HPFS/NTFS
/dev/sda7           28048       59918   256003776    7  HPFS/NTFS
/dev/sda8           59919       60801     7092666   82  Linux swap / Solaris

where sda6 is the new XP partition. 
Perhaps I need to reorganize the partitions into 1-5 instead of 1,5-8 in order to make XP boot...

---

### Post by rijidij on 2010-03-18
Hi, sorry about the delay in replying, but I've been busy trying to get this to work... ](*,)

Eventually, I did have some success.
I thought the extended partition might have been causing problems, so I re-arranged my disk with primary only, linux-swap at the end.
Here is the new configuration:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24859   199679886   83  Linux
/dev/sda2           24860       35255    83505870    7  HPFS/NTFS
/dev/sda3           35256       60114   199679917+   7  HPFS/NTFS
/dev/sda4           60115       60801     5518327+  82  Linux swap / Solaris
```

I eventually concluded that moving from IDE to SATA was the root cause of my problem.
I could get to Window's boot loader, but no further. I assumed that it didn't have the correct drivers.
So I booted from the XP install CD and did a "repair" install.
i.e. Hit 'enter', not 'R'. Let it discover the existing installation, then select the option to repair it.
This eventually got me to the login screen but of course, due to the hardware changes, I had to re-activate XP.
Unfortunately when I tried to do this online, the network wasn't set up and it kept trying to make a dial-up connection. So I had no option but to do it the old fashioned way - over the phone.

Anyway, for what it's worth, I now have XP running on my new hard drive.
And _not_ in the first partition! \\:D/

---

### Post by yzord on 2010-10-25
Great tutorial - thanks a million!

However, I just had one note re: Step #6. In my case, "chkdsk /f /r" did not resize my data to the actual partition size. However, "ntfsresize" did the trick without any issues.

1) "ntfsresize -i /dev/sda3*" detected both the correct size of the copied data and partition size, and also indicated how much data I would gain from the operation.
2) "ntfsresize -n /dev/sda3*" did a test run which completed succesfully.
3) "ntsfresize /dev/sda3*" worked and indicated that a force chkdsk would be run the next time Windows was booted.
I neither forced the resize nor specified size (-s) as neither option seemed necessary. Went like a dream, and 2 reboots later, my moved XP partition is at the proper size.

* "/dev/sda3" is my XP partition - change this to your partition id.

---

### Post by NBrenner on 2011-01-21
Hello,
 
I have a related issue.  I think this will work but never tried it first time I encountered this issue, but If I have a Windows XP Installation on an HP 8450w EliteBook (for instance) that has a bad boot sector which prevents the system from booting into Windows and I have a completely identical machine that has a fully operational HDD, it boots into Windows XP with out error. Should I simply be able to pull both HDDs out then copy the data from bad HDD onto good HDD using a couple USB adapters and any OS; probably a good idea to use Linux because it will not recognize any files as protected system files,.  Wouldn't I have then done the equivalent of say a Heart transplant in an otherwise healthy patient. 
 
For the life of me I cannot think of why this would not work.  I look forward to any friendly enlightenment that you may have.
 
Thank you,
 
Nathan

---

### Post by rijidij on 2011-01-22
Hi Nathan,

If I were to do this, I would use dd or something like partimage to copy the *partitions*, not files.

HTH
Craig

---

### Post by jaes on 2011-05-14
Hi,

Great tutorial ! 
I'm currently trying this procedure with Windows 7. Sadly there isn't anymore boot.ini to config Windows 7 bootloader but a separated partition containing hive's file.

I thing I have to use windows command bcdboot or bcdedit or even both. But I don't know how :s. Does any of you have ever tried this with Windows 7 ? I may use some help ^^.

---

