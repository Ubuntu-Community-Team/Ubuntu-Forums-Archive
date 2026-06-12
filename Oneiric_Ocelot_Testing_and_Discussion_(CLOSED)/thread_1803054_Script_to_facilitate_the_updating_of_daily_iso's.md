---
title: "Script to facilitate the updating of daily iso's"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-07-12
I have been working on a script to update either the live daily iso or alternative daily iso and copy them to a flash drive.  Here's the finished product.

```
#!/bin/bash
#Script to run zsync and update ubuntu daily builds
#Author: Evan Anderson (linuxman94) 
#Change ISO/ISOL the settings of your choice
#Change DEV to the device path
#Pass command line option "nodownload" to skip downloading
ISO="oneiric-alternate-amd64.iso"
ISOL="oneiric-desktop-amd64.iso"
ISODIR="$HOME/Daily_ISO"
DEV="/dev/sdb"
#check for folder
if [ -d $ISODIR ]; then
    cd $ISODIR
  else
    mkdir $ISODIR
    cd $ISODIR
fi
#Do a copy only
if [ "$1" = "nodownload" ]; then
     echo -n "Copy already downloaded ISO to flash drive? (y/n): "
     read x
     if [ $x == "y" ]; then
        echo -n "Copy Live or alternative? (l/a): "
        read y
#check if root.  If not, ask for password
        if [[ $EUID -ne 0 ]]; then
          sudo -p "Please enter your password: " whoami 1>/dev/null
        fi
         if [ $y == "l" ]; then
          echo -n "Copying live iso to usb drive..."
          sudo dd if=$ISOL of=$DEV &>/dev/null
         else
          echo "Copying alternative iso to usb drive..."
          sudo dd if=$ISO of=$DEV &>/dev/null
         fi
     else
         echo "Did not request copy. Exiting"
         exit        
     fi
   echo -n "Copy Finished! Reboot now? (y/n): "
   read status
    if [ $status == "y" ]; then
      echo "Rebooting now!"
      sudo reboot
     else echo "Exiting"
    fi
exit
else
#download then ask for copy
echo -n "Download live or alternative iso? (l/a): " 
read b
if [ $b == "l" ]; then
    echo "Downloading latest live iso..."
    zsync http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync &>/dev/null
    else
    echo "Downloading latest alternate iso..."
    zsync http://cdimage.ubuntu.com/daily/current/oneiric-alternate-amd64.iso.zsync &>/dev/null
fi
echo -n "Copy to usb drive? (y/n): "
   read a
#check for root.  If not, ask for password
if [[ $EUID -ne 0 ]]; then
   sudo -p "Please enter your password: " whoami 1>/dev/null
fi
         
if [ $a == "y" ]; then
    echo "Copying to usb drive"
    if [ $b == "l" ]; then
         sudo dd if=$ISOL of=$DEV &>/dev/null
      else
         sudo dd if=$ISO of=$DEV &>/dev/null
    fi
    echo -n "Copy Finished! Reboot now? (y/n): "
    read status
    if [ $status == "y" ]; then
      echo "Rebooting now!"
      sudo reboot
     else echo "Exiting"
    fi
fi
fi
exit

```

Comments/Suggestions are welcome :D

---

### Post by linuxman94 on 2011-07-14
bump.  Anyone have feedback?

---

### Post by ratcheer on 2011-07-14
My feedback is just that it seems way too complicated to perform a simple task.

Tim

---

### Post by ronacc on 2011-07-14
I agree with ratcheer , here is a one line script I use to zsync .
```
zsync http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync
```
I named it zsyncstub and keep it in the dir where the .iso I zsync lives , I just cd to that dir and type ./zsyncstub and it does the update  ( adjust the name of the .iso to yours) then use isotostick or unetbootin or whaterver you prefer to put it on a stick .

---

### Post by castrojo on 2011-07-14
testdrive (in the archive) already does it.

A for effort though!

---

### Post by xebian on 2011-07-14
!zsyn is enough on the terminal

---

### Post by iClouseau88 on 2011-07-15
Hi,

How do I use "testdrive" to test drive an iso?  Is it like the following?

#testdrive <oneiric-alternate-amd64.iso>  [RETURN]

---

### Post by seeker5528 on 2011-07-15
Personally in situations where the machine has a CD/DVD drive to boot from, I would prefer to make a '/boot-isos/' directory in the root of a partition on my flash drive, copy the ISO to the '/boot-isos/' directory, then use [Super Grub2 disk](http://www.supergrubdisk.org/super-grub2-disk/) to boot the ISO.

[img]http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png[/img]

If you are worried about the wear and tear on your flash drive, your computer doesn't recognize flash drives at boot time, etc... it will look for '/boot-isos/' and '/boot/boot-isos/' directories on all of your partitions on your hard drives as well, show you what ISOs it finds and which are loop-bootable.

Later, Seeker

---

