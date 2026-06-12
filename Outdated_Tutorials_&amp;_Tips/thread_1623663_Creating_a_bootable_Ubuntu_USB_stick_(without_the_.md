---
title: "Creating a bootable Ubuntu USB stick (without the crash)"
date: 2010-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by tkoco on 2010-11-16
I had a need to create a bootable USB stick which I could load Avast Anti-virus software onto. Why? To use the Linux version for checking Windows partitions. Windows based malware cannot hide from a Linux based anti-virus search.
An inherent problem with the pre-existing methods for creating a bootable stick is that the USB stick would crash and burn when you executed an update using the Update Manager in Ubuntu. This method avoids the crash and burn!
For this tutorial, I will presume that you know how to use the CLI - Command Line Interface terminal window. Also, I will presume that you have familarity with some of the CLI tools, like dd, fdisk, sudo, gedit, qemu, dmesg, etc.

PREREQUISITES:

	Working Ubuntu machine, 10.04 LTS or more recent
	QEMU installed
	ISO image of the Ubuntu LiveCD
	USB stick 4G or larger (as of Version 11.04, minimum size is 8G)

First thing you will need to determine is what the device designation is for the USB stick. Typically, Ubuntu will assign the next available drive designation to the USB stick. Open a terminal window (Application -> Accessories -> Terminal) and type in ```
$ dmesg
``` Insert the USB stick and re-run the command. You are looking for something like /dev/sdb or /dev/sdc or /dev/sdd at the end of the listing.
Caution: Leave the USB stick plugged into your Ubuntu box until you are finished. The tutorial will tell you when it is ok to pull the USB stick.

PARTITIONING:

 Before we get started, you will notice that Ubuntu has added the USB stick to the file system. We will need to unlink the USB stick from the file system. **We will be using /dev/sdc for this tutorial.** Modify /dev/sdc to meet your needs. In a terminal window, we do this with: ```
$ sudo umount /dev/sdc1
``` 
Now let's set up the partitioning. In a terminal window, run:
```
$ sudo fdisk /dev/sdc
``` Within fdisk do these:

1) Delete any previous partitions. Create partition 1 as a primary partition. Use the entire stick. The "type" should default to a Linux partition 83.
2) Set bootable flag for partition 1
3) write the partition table and exit

Note: Use the 'm' command to see the menu of options in fdisk.

FORMATTING:

 Format partition 1 as ext4 style with block sizes of 4096. Again in a terminal window: ```
$ sudo mkfs.ext4 -m 1 -b 4096 /dev/sdc1
```

LOADING SOFTWARE:

1) With the USB stick still inserted, start the Ubuntu LiveCD ISO image in QEMU like this:
```
$ sudo qemu -cdrom /<path_to_ISO>/ubuntu-10.04-desktop-i386.iso -hda /dev/sdc1 -boot d -m 1024

```
I stored the iso image on my machine in the ISO directory. So my command would look like this:```
$ sudo qemu -cdrom /home/tko/ISO/ubuntu-10.04-desktop-i386.iso -hda /dev/sdc1 -boot d -m 1024
```

 For this tutorial, we will be using a memory size of 1024. You can use a smaller memory setting like "-m 256" instead of "-m 1024". I recommend that you use the largest memory setting which you can spare.

2) After Ubuntu has booted up within QEMU, tell Ubuntu to Install.
3) During the partitioning portion of the installation, use the "Specify partitions manually" option. Click on "Forward"
4) Highlight /dev/sdc, and click on "Change"
5) Select "ext4" as partition type. Set the mount point as "/" and most importantly, make sure the "format" box is _not selected_ (you have already formatted the partition). 
6) Click "Continue" twice. and then continue as Ubuntu will complain about not having a swap area. You will create a swapfile later on.
7) Let Ubuntu finish installing. Then select "Reboot". When the screen says to remove the CD, close the QEMU window.

FINISHING TOUCH:

 The USB stick should still be inserted, so boot up the Ubuntu USB stick using:```
$ sudo qemu -hda /dev/sdc1 -boot c -m 1024
```

 Once you have the desktop in QEMU, you will need to create a "swapfile" and an entry in the "/etc/fstab" file.

1) Open a terminal window in the QEMU desktop and go to the "/var" directory to create the swapfile:```
$ cd /var
$ sudo dd if=/dev/zero of=swapfile bs=4096 count=65536
$ sudo mkswap ./swapfile
```

2) From the same terminal window, edit the "/etc/fstab" file.```
$ cd /etc
$ sudo gedit fstab

```
3) Add an entry for the swapfile which looks like this:```
/var/swapfile	swap	swap	default		0	0

```
4) Save the file and exit the editor. Start the swap function with:```
$ sudo swapon -a

```
5) Check the memory allocation with:```
$ free
```

   You should see the new swap area in the listing.

You are now finished. From within QEMU, do a normal desktop "shutdown" and pull the USB stick. When you put the stick into a machine capable of booting from USB (and is setup in the BIOS to do so), the machine should boot up into Ubuntu from the USB stick upon power up.

ACID TEST:

With Internet connected and having booted up into Ubuntu using the USB stick, do an update using the "Update Manager". This USB stick version of Ubuntu should be able to complete the task without crashing or corrupting the Ubuntu Linux on the stick.

Good Luck.

After writing this "How To", I discovered a flaw in the logic. The Xorg video driver will become harmonized with the hardware on which you created the USB stick. This situation can be a bit problematic.

THE SOLUTION:

Boot up in the USB stick. Using a terminal window (Application -> Accessories -> Terminal), edit the rc.local file.```
$ sudo gedit /etc/rc.local
``` And add a line above the "exit 0" line like this:```
dpkg-reconfigure -phigh xserver-xorg

exit 0
```
Click on "Save" and close the gedit window. Do not forget to do a proper shutdown and reboot (if needed).

Now as the Ubuntu USB stick boots up, the Xorg xserver is forced to reconfigure itself to any hardware changes and you should have a usable desktop.

NEXT PROBLEM:

While test driving the Ubuntu USB stick, I ran into some machines which would not startup GRUB. After researching the issue, I came across the solution on this Ubuntu page: [https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands]("https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands"). Without rehashing the entire page, the fix is a re-installation of GRUB2. 

SOLUTION:

This solution presumes that the version of Ubuntu is the same for both the working Ubuntu system and the Ubuntu USB stick. **For this tutorial, we will use /dev/sdc as the USB stick device**. Change it to match your situation.
 
*[Side note: as of this writing, my main system is at release 10.04. I was working with release 11.04. To prevent a mismatch in the versions of grub, I booted the system in a LiveCD of 11.04 and followed the instructions below. The USB stick came up as /dev/sdb. I changed all of the 'sdc' to 'sdb' and all went well!]*

Insert the Ubuntu USB stick into your working Ubuntu system. Open a terminal window (like above) and do this:```
$ sudo umount /dev/sdc1
$ sudo mount /dev/sdc1 /mnt
$ sudo grub-install --root-directory=/mnt/ /dev/sdc
$ sudo umount /dev/sdc1

```
After you finish with these commands, close out the terminal window and pull the USB stick. After completing these steps, I was able to boot from the difficult systems.

New Info, Old Problem:

I bought a new USB stick and did all the instructions as outlined. But I could not get the stick to boot. Then I remembered that the MBR needs to be written to sector 0 of the USB stick. So, assuming that the stick is /dev/sdc, do this:
```
$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdc
``` to put the MBR (Master Boot Record) on the stick.


TIP for Ubuntu festivals:

Once you finish creating your USB bootable stick and have verified that it boots up ok, do a bare-metal backup. Insert the finished USB stick and:
```
$ sudo umount /dev/sdc1
$ sudo dd if=/dev/sdc of=Ubuntu.img bs=32768
```
When finished, pull the USB stick and insert a *new* USB stick of the same size. Then do a restore like this: (**please pay attention!**)
```
$ sudo umount /dev/sdc1
$ sudo dd of=/dev/sdc if=Ubuntu.img bs=32768
```
When the system finishes writing the backup to the new USB stick, then pull the USB stick. Verify that it boots up. You will find this method a lot faster than starting from scratch.

---

