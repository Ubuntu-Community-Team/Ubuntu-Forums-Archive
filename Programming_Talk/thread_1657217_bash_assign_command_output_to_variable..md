---
title: "bash assign command output to variable."
date: 2010-12-31
forum: Programming Talk
---

### Post by amsterdamharu on 2010-12-31
I can never seem to get bash, every time I think it will do this it ends up doing that.
Here I try to check output of fdisk -l to see if after an mbr restore the values of partition sizes are what they were when I made the backup. This because my friend uses Windows and will never resize the partitions herself but some program/virus might mess things up.

```
computer user # fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0b1ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            3826        7649    30716280   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            7650       19457    94847729+   5  Extended
/dev/sda5            7650       18071    83714683+  83  Linux
/dev/sda6           19128       19457     2650693+  82  Linux swap / Solaris
/dev/sda7           18072       19127     8482288+  83  Linux

Partition table entries are not in disk order
computer user # fdisk -l | grep -e 'sda1.*1.*3825.*30724281.*7.*HPFS/NTFS'
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS (cool, the first partition seems to be ok)
computer user # mytest=$(fdisk -l | grep -e 'sda1.*1.*3825.*30724281.*7.*HPFS/NTFS')
computer user # echo $mytest
/dev/sda1 2009-12-18-09-10-38.075-VirtualBox-6505.log bin boot.iso cd chinese convert.sh Desktop Documents Downloads Examples Music PDF Pictures Podcasts Public restore tcz temp Templates test.sh Videos workspace 1 3825 30724281 7 HPFS/NTFS
computer user # 
```

It seems that the * in the result line has been replaced by a list of directories in my home folder.
My questions are: why replace the * with a directory list?
How can I check $mytest to have the correct value?
```
mytest=$(fdisk -l | grep -e 'sda1.*1.*3825.*30724281.*7.*HPFS/NTFS')
if [[ $mytest != '' ]]; then

```

---

### Post by Vaphell on 2011-01-01
no idea why, but **set -f** (disable globbing) to the rescue
[http://ss64.com/bash/set.html](http://ss64.com/bash/set.html)

and you can be more specific in your regex and replace .* with \s (covers only spacing chars)

---

### Post by amsterdamharu on 2011-01-01
Thank you Vaphell, I will try set -f. Good point about making the regexp less gready. Both bash and regexp are latin to me (can't wrap my head around it).

It seems to work fine at the moment will post the entire script here later.

---

### Post by v8YKxgHe on 2011-01-01
> **amsterdamharu said:**
> 
It seems that the * in the result line has been replaced by a list of directories in my home folder.
My questions are: why replace the * with a directory list?
How can I check $mytest to have the correct value?
```
mytest=$(fdisk -l | grep -e 'sda1.*1.*3825.*30724281.*7.*HPFS/NTFS')
if [[ $mytest != '' ]]; then

```

Simple, variable expansion and globs. See [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob) - this is why you should always quote your vars.

```
$ foo="bar *"
$ echo $foo
bar dir1 dir2 file1 file2
$ echo "$foo"
bar *
```

---

### Post by amsterdamharu on 2011-01-02
Thank you Alex, that is a great tip. I will try and use that whenever reading a variable.

---

### Post by amsterdamharu on 2011-01-02
```

#!/bin/bash
# Partitioned the hassee Q230B in 4 partitions, 1 is for XP 50GB (can be smaller but have some space to install software), 2 is big ntfs and for data, 3 hidden fat32 for the ghost image 5GB, 4 is for tinycore and grub boot dir ext3 100MB
# installed tinycore on usb (unetbootin putting the iso on usb) 
# change the syslinux.cfg to:
# kernel /isolinux/bzImage
# append initrd=/isolinux/tinycore.gz tce=sda1 restore=sda1 home=sda1 waitusb=10
# boot with the usb and connected to Internet installed the grub-0.97-splash.tcz, grub2.tcz (but thinking the grub2 is not needed), bash.tcz, dosfstools-3.tcz, geany.tcz, grep.tcz and seamonkey.tcz
# Make sure to back up your data on the usb stick (is sdb1 for me) best to mount it and use control panel -> backup restore -> fill in sda1/ for device and choose backup.
# Then opened a terminal and installed grub on the harddisk: with the following commands (note root(hd0,3) is for sda4 where tinycore will be installed (hd0) is the mbr of the first harddisk
# mkdir -p /mnt/sda4/boot/grub
# cp -p /usr/lib/grub/i386-pc/* /mnt/sda4/boot/grub
# grub
# root (hd0,3)
# setup (hd0) 
# quit
# Choose reboot and make sure all changes are saved to sdb1, reboot from usb with tinycore. (sometimes the tgz and gz files are in root sometimes they are in tce)
# Copied the files to hda4 with the following commands: (memdisk can be obtained from syslinux, the dos.img was win 98 image file with ghost on it)
# win 98 image can be obtained from www.bootdisk.com but ghost is not free software and has to be bought. (the ghost dos command version I use)
# to edit the dos.img autoexec.bat and add the ghost and gdisk (to hide partitions) program you can mount it like this: sudo mount -t vfat -o loop dos.img tmp (where tmp is an empty directory)
# make sure when editing autoexec.bat to use crlf (under document set line endings). importain line in autoexec.bat is: "ghost.exe -CLONE,mode=prestore,src=1:3\XP.gho:1,dst=1:1"
#    you can add -sure at the end but do it later because it does everything automatically without user input.
# cp /mnt/sdb1/mydata.tgz /mnt/hda4
# cp -R /mnt/sdb1/tce /mnt/
# cp /mnt/sdb1/boot/bzImage /mnt/hda4/boot
# cp /mnt/sdb1/boot/tinycore.gz /mnt/hda4/boot
# cp /mnt/sdb1/dos.img /mnt/hda4/boot
# cp /mnt/sdb1/memdisk /mnt/hda4/boot
# create a menu.lst in /mnt/hda4/boot/grub with the following content:
#default 0
#timeout 1

#title Windows XP
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

#title tinycore (linux for starting the computer)
#kernel /boot/bzImage
#initrd /boot/tinycore.gz tce=sda4 restore=sda4 home=sda4 waitusb=10

#title Restore Windows (puts a copy of Windows back)
#rootnoverify (hd0,3)
#kernel /boot/memdisk
#initrd /boot/dos.img

# backup sda4 with "cd /mnt/sda4;tar -cvf /mnt/sdb1/tinycore.gz -C ."
# create the files: /home/tc/rebootusb.htm (telling to close window, wait, switch off computer with power button then reboot from usb again, if more than 2 times try boot from harddisk using windows repair)
#        /home/tc/reboothd.htm (telling to close window, wait, shut down with power button, UNPLUG USB (some biosses wont boot the dos.img with memdisk with usb plugged in). start comupter pussing down arrow key and choose repair Windows)
# create this document under /home/tc/ named restorehasseeq230b.sh and make it executable "chmod +x restorehasseeq230b.sh"
# execute the following command to make sure this script is executed on startup: 'echo "sudo xterm -st -e /home/tc/restorehasseeq230b.sh &' > ~/.X.d/restore'
# choose to shut down (make sure all is saved to sda1 maybe choose backup first)
# when rebooting it will try to restore partition, reformat sda3 and sda4 table copy XP.gho from USB to sda3 hidden fat and tinycore.gz extract tinycore.gz to sda4 to make the hd bootable again.
# TODO remove the following 2 lines, they are to cancel the script
echo "Press enter to start or contol + c to cancel";
read hello;

# TODO: here I am using hda values because I am testing it in virtual machine
tinycore_usb="hda1";
tinycore_hd="hdd5";
ghost_location="hdd3";
hd_to_check="hdd";

check_filesystem(){
    an_error=0;
    check_var=$(cmp /mnt/$tinycore_usb/isolinux/mbr/"$hd_to_check"1.bin /mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"1.bin);
    if [[ "$check_var" != '' ]]; then
        an_error=1;
    fi
    check_var=$(cmp /mnt/$tinycore_usb/isolinux/mbr/"$hd_to_check"2.bin /mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"2.bin);
    if [[ "$check_var" != '' ]]; then
        an_error=1;
    fi
# Do not check the hidden fat32, it will be formatted later and will change with the origional file after that
# ext3 will be formatted too but since it contains the boot sector we should check, a format doesn't change the
#         binary value of the boot sector
    check_var=$(cmp /mnt/$tinycore_usb/isolinux/mbr/"$hd_to_check"4.bin /mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"4.bin);
    if [[ "$check_var" != '' ]]; then
        an_error=1;
    fi
}
restore_filesystem(){
    # Copy back the bin files to the harddisk
    # the MBR and partition tables
    mount -t vfat /dev/$tinycore_usb /mnt/$tinycore_usb
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check".bin of=/dev/"$hd_to_check" bs=512 count=1
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"1.bin of=/dev/"$hd_to_check"1 bs=512 count=1
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"2.bin of=/dev/"$hd_to_check"2 bs=512 count=1
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"3.bin of=/dev/"$hd_to_check"3 bs=512 count=1
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"4.bin of=/dev/"$hd_to_check"4 bs=512 count=1
}
mount -t vfat /dev/$tinycore_usb /mnt/$tinycore_usb;
cd /mnt/$tinycore_usb/isolinux/mbr
rm -f *.bin;
bash backup;
check_var=$(cmp /mnt/$tinycore_usb/isolinux/mbr/$hd_to_check.bin /mnt/$tinycore_usb/isolinux/mbr/org/$hd_to_check.bin);
if [[ "$check_var" != '' ]]; then
    # the current mbr is not same as the origional, copy back mbr and reboot.
    dd if=/mnt/$tinycore_usb/isolinux/mbr/org/$hd_to_check.bin of=/dev/$hd_to_check bs=512 count=1;
    echo "Tried to restore the filesystem";
    echo "Please wait, instructions will follow soon";
    seamonkey /home/tc/rebootusb.htm
    reboot -f;
    exit;
fi
# checking the partiton tables bin files with the origionally saved ones
check_filesystem;
if [ $an_error != 0 ]; then
    # some of the  current partition tables are not same as the origional, copy back and reboot
    restore_filesystem;
    echo "Tried to restore the filesystem last step";
    echo "Please wait, instructions will follow soon";
    seamonkey /home/tc/rebootusb.htm
    reboot -f;
    exit;
fi

# format $ghost_location to FAT 32
dd if=/mnt/$tinycore_usb/isolinux/mbr/org/"$hd_to_check"3.bin of=/dev/"$hd_to_check"3 bs=512 count=1
umount /dev/$ghost_location;
mkdosfs -F 32 -n "Q230B" /dev/$ghost_location
mount -t vfat /dev/$ghost_location /mnt/$ghost_location
mount -t vfat /dev/$tinycore_usb /mnt/$tinycore_usb
cp -f /mnt/$tinycore_usb/XP.gho /mnt/$ghost_location
cp -f /mnt/$tinycore_usb/tinycore.gz /mnt/$ghost_location
umount /dev/$tinycore_hd;
mke2fs -T ext3 /dev/$tinycore_hd;
mount /dev/$tinycore_hd /mnt/$tinycore_hd
cd /mnt/$tinycore_hd
tar -xvzf ../$ghost_location/tinycore.gz -C .

echo "Finished repairing the harddisk";
echo "Please wait, instructions will follow soon";
seamonkey /home/tc/reboothd.htm
halt;

```

---

