---
title: "USB write problems"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by r3bol on 2008-11-25
Hi, I'm having some noobish difficulty understanding something that is happening on my Kingston USB drive. If I try to execute this: 
$ sudo zcat boot.img.gz > /dev/sdb 
I get:
$ /dev/sdb Permission Denied. 
But the drive is partitioned as FAT32 W95 (which I thought didn't have ownership issues).
I thought it might be something to do with the type of partition so I tried to change the partition to a linux one, but get the same message. 
I also tried it with the disc mounted and unmounted.
Here is the strange part. If I gained root (sudo su) I could execute the zcat boot.img.gz > /dev/sdb and also cp debian-40r5-i386-netinst.iso and it appears to write to the disc, but for some reason nothing is copied to the USB disk and it fails to boot the install program. 
I can however copy and create files directly onto the USB disc with no problem. So why does is deny me permissions sometimes? Whats going on!?:confused:
Thanks.

Some extra info...
$ lsusb
Bus 004 Device 003: ID 0951:1603 Kingston Technology 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

$ fdisk -l
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd991d991

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2425    19478781    7  HPFS/NTFS
/dev/sda2            2426        4805    19117350   83  Linux
/dev/sda3            4806        4870      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 4141 MB, 4141875200 bytes
255 heads, 63 sectors/track, 503 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000043e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         503     4040316    b  W95 FAT32

---

### Post by echo.whoami on 2008-11-25
i think that you should find where it is mounted . if you

```
ls /media
```

you will see the directory disk. this must be your usb drive.

so now try 

```
sudo zcat boot.img.gz > /media/disk/
```

BUT FIRST make sure tha /media/disk is your usb.

---

### Post by r3bol on 2008-11-25
So here is what I get...



$ ls /media
ALIAS_SEASON_3_DISC_5  cdrom  cdrom0  disk  disk-1  floppy  floppy0  hda1

My USB stick is disk-1



$ ls /media/disk-1
new file  new file~

Yep, here are a test file i made.



$ cd Desktop
$ sudo zcat boot.img.gz > /media/disk-1
bash: /media/disk-1: Is a directory

Note, the USB stick is mounted.



$ sudo zcat boot.img.gz > /media/disk-1
bash: /media/disk-1: Permission denied

Note, the USB stick is unmounted.



$ ls /media/disk-1
ls: cannot access /media/disk-1: No such file or directory 

ls with the USB stick unmounted.

---

### Post by tester321 on 2008-12-24
r3bol:  Did you ever resolve this?

I have the same problem with a 1GB Lexar Jumpdrive.  (Just trying to setup USB-based Debian installer -- have already done it successfully on numerous other USB flash drives)

One interesting thing is that this drive under Windows shows up as a FIXED hard drive -- not removable.  I don't know the impact this may have under Linux, if any.

EDIT:  Just noticed in dmesg:

... [sdb] Write Protect is off

Hmm, not familiar with how to set/unset Write Protect (even though it says OFF)

---

### Post by anewguy on 2008-12-24
I don't have time right now (leaving for a Christmas party), but the problem is probably in the permissions when the USB file system is mounted (won't matter if win95 or what).  There is a small change to the 40-basic-permissions or some such file (I'm on my Windows box now or I'd just walk you through it) where the default for mounting the USB file system is root ownership.  you can change that to 777 to gain access for all users.

Scan the forum for recent (since 8.04 - that's when it changed) posts regarding USB permissions.

I'm sorry I don't have the time right now.  I'll check back later tonight and see if you need help yet.

Gotta go!

Dave :)

---

### Post by kansasnoob on 2008-12-24
You know, I read about these problems with external drives and I'm always puzzled:confused:

By simply installing "pmount" from synaptic I have virtually no trouble whatsoever mounting external drives!

If they're NTFS I also install "ntfsprogs".

Both pmount and ntfsprogs are in synaptic.

I'm lazy and I like to do things the gui way!

---

### Post by anewguy on 2008-12-24
> **kansasnoob said:**
> You know, I read about these problems with external drives and I'm always puzzled:confused:

By simply installing "pmount" from synaptic I have virtually no trouble whatsoever mounting external drives!

If they're NTFS I also install "ntfsprogs".

Both pmount and ntfsprogs are in synaptic.

I'm lazy and I like to do things the gui way!

Yeah, I think in the case of the permissions file, it is taking things like USB sticks, etc., and mounting root.  I'll find that and post back later.  Some people run into this with other USB devices such as cameras.  The problem started when the way /etc/udev/rules.d was reworked with the release of 8.10.  It took a while to find it and to find the syntax had changed.

Dave :)

---

### Post by anewguy on 2008-12-25
Okay, here's one of the places that causes access restricted to root (su or sudo) only:

in /etc/udev/rules.d/40-basic-permissions.rules:

Look for the line that says:
# USB devices (usbfs replacement)

It will be followed by 2 line as follows:

SUBSYSTEM=="usb", ENV(DEVTYPE)=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device"  MODE="0664"

Note that the 2 modes are the permissions - the files/devices are only accessable to root.  If you don't mind your USB devices being open to anyone using your computer, just change those 2 modes to MODE="0777".  If you don't want them open to the world, you can assign users to a new group - say something like usbpeople, then change the 2 system to include group assignment to usbpeople and change the MODEs to the values you want.

To edit this file in the gui:

- open a terminal window

- sudo gedit /etc/udev/rules.d/40-basic-permissions.rules


I think if you just change these 2 MODE statements to 0777 you'll find you can access the devices without being root or su.
I had this problem with some special cameras I have that don't look like a disk drive on the USB bus.  When I moved to 8.04 I found they had changed the syntax to that noted above.

Dave :)

---

### Post by lettfeti on 2008-12-25
chmod 777 /dev/sdb1 when unmounted worked for me. problem was though that i can't boot from it :/

---

### Post by BaconLT on 2009-11-29
I got the "permission denied" message and solved it by becoming the root user, rather than just sudoing the command.

The easiest way to do this is with: 

[FONT="Courier New"]sudo su -[/FONT]

Then do the zcat command. 

BE CAREFUL, as root, you can do A LOT of damage VERY FAST. Be sure to [FONT="Courier New"]exit[/FONT] as soon as you are done.

---

### Post by strom83 on 2010-05-22
Hi!

I've got the same problem.

Using zcat boot.img.gz > /dev/sdb1 I get "permission denied".

I've tried the solution suggested by anewguy but I didn't find any 40-basic-permissions.rules in /etc/udev/rules.d/ there were several other *.rules in it defining behaviour for pci and usb LAN devices and CD-drives etc. However, I didn't find anything about usb-devices in particular.

I've also tried the other suggestion by lettfeti. I used chmod 777 /dev/sdb1 while my usb-drive was unmounted and chmod returned 

"cannot access `/dev/sdb1': No such file or directory".
:confused:

Which is awkward. Is there anyone who knows some explanation or some place where I can find another solution for this problem?

Some info:

OS: Jaunty
Desk: XFCE 4.6
Drive: Feiya Technology Corp. Memory Bar a.k.a INTENSO USB Drive 4GB

If you need any info, please let me know.

Thanks and bye

---

### Post by tomulcak on 2010-10-13
> **BaconLT said:**
> I got the "permission denied" message and solved it by becoming the root user, rather than just sudoing the command.

The easiest way to do this is with: 

[FONT="Courier New"]sudo su -[/FONT]

Then do the zcat command. 

BE CAREFUL, as root, you can do A LOT of damage VERY FAST. Be sure to [FONT="Courier New"]exit[/FONT] as soon as you are done.


That did it ! !  good one!

---

### Post by eriqk on 2010-11-08
I did "sudo su" without the hyphen. Then, it worked.
I also found that on 10.04, there is no /etc/udev/rules.d/40-basic-permissions.rules, so the only way to zcat anything to /dev/sdX is to become root.

---

### Post by YOUWERENTKIDDING on 2011-07-11
now that I ran the zcat on my main harddrive instead of the usb, what choice remains with bringing grub back :confused:
Also, when running the commands on my usb, it did not work to boot and install but I am more so interested in bringing back the functionality of the usb
gparted tells me unrecognized disklabel H: and will not let me reformat, even after formats from windows.

OS down and USB broken

---

### Post by wildmanne39 on 2011-07-11
> **YOUWERENTKIDDING said:**
> now that I ran the zcat on my main harddrive instead of the usb, what choice remains with bringing grub back :confused:
Also, when running the commands on my usb, it did not work to boot and install but I am more so interested in bringing back the functionality of the usb
gparted tells me unrecognized disklabel H: and will not let me reformat, even after formats from windows.

OS down and USB brokenHi, this thread is very old start a new thread with a good title, and describe you problem, so we can help you.

---

### Post by YOUWERENTKIDDING on 2011-07-11
The thread contains relevant information to my post. 
This thread on its own, without my post, lacks any representation of the serious consequences that could come about, it contains instruction that could ruin both an operating system and a usb stick.

There is no discussed functionality in this thread that is obsolete or out of date.

---

