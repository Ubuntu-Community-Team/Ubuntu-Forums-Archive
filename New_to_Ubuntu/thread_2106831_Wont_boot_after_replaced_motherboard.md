---
title: "Wont boot after replaced motherboard"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by WileyGaia on 2013-01-20
Hi, I had to replace my motherboard, ram and cpu, now it won't boot (10.04). I am now using Live CD to post this thread. Searched forums, seems I must reinstall grub2? Tried following instructions, but Hard drive wont mount: 
"DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

Other responses from within Live CD session:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f02e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18709   150277120   83  Linux
/dev/sda2           18709       19458     6010881    5  Extended
/dev/sda5           18709       19458     6010880   82  Linux swap / Solaris
```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="d9cbe2ec-a3a1-4929-82af-bbb45c815e0f" TYPE="ext4" 
/dev/sda5: UUID="ed680e89-a7d9-4e66-9590-1ba81ea44485" TYPE="swap" 
```

Gonna post the error I get when booting next (not sure how I am gonna do that, will have to write it down as best I can - its very long and the screen scrolls way past the beginning of the error message, will revert with my best shot.
Please excuse my ignorance I am not a terminal user...

---

### Post by WileyGaia on 2013-01-20
OK, here is the end of the long error message when booting:
```
Killed
mount:mounting /dev on root/dev failed. No such file or directory
mount:mounting /sys on root/sys failed. No such file or directory
mount:mounting /proc on root/proc failed. No such file or directory
Target filesystem doesn't have sbin/init.
No init found. Try passing init=bootarg.

Busybox...blahblah
(initramfs)

```

---

### Post by sudodus on 2013-01-20
Often Ubuntu is portable between computers, which might have been applicable in your case. But there are cases when it is not.

Do you have any proprietary drivers installed (typically for graphics or wifi)?

You could try with some boot options. See this link

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

But the situation is pretty good since you can run a live session from a CD drive. What drive is it?

Can you run from an Ubuntu 10.04 LTS or Ubuntu 12.04 LTS CD/USB drive?

Since Ubuntu 10.04 (desktop) has end of life soon (April 2013), you might as well backup the /home directory and prepare to make a new installation.

In order to give good advice, we need the specs of your refurbished computer, at least

- cpu
- ram
- graphics card/chip

---

### Post by WileyGaia on 2013-01-20
OK
The drive is a Western Digital 160GB Sata drive - think.

I am not a techie, but this is what the invoice says:
MSI H61M S1155 DDR3
4GB DDR3 1333MHZ
INTEL PENTIUM G645 CPUI

Very keen to upgrade to 12.04, but how do I backup my home directory if I cant mount the drive?

---

### Post by grahammechanical on 2013-01-20
This might seem off topic but I have been getting this error message

> Busybox...blahblah
(initramfs)

for every ISO image of Raring Ringtail (13.04) since the first images were available. In my case I had "unable to find a medium containing a live file system."

Further investigation got this. which is what you get.

> Target filesystem doesn't have sbin/init.
No init found. Try passing init=bootarg.

I finally found a way to load the live session. I added

> acpi=off irqpoll

To the boot parameters. It might work for you. It might not. At the Grub menu press E and that will put Grub into Edit mode for that selection. Now look for a line that says quiet splash and insert the additional boot parameters in front.

If you want you can also remove quiet splash and then you will see the messages as the system loads and the point at which it stopped.

I was trying on a Live CD not a hard disk. But, who knows?

Regards.

---

### Post by sudodus on 2013-01-20
> **WileyGaia said:**
> OK
The drive is a Western Digital 160GB Sata drive - think.

I am not a techie, but this is what the invoice says:
MSI H61M S1155 DDR3
4GB DDR3 1333MHZ
INTEL PENTIUM G645 CPUI

Very keen to upgrade to 12.04, but how do I backup my home directory if I cant mount the drive?

I suggest that you try with at least one of the flavours of [KLX]Ubuntu 12.04 (and/or 12.10). It looks like your HDD is recognized by the live system, and should be possible to mount there. What live system is it? Ubuntu or some repair live system? Anyway try to mount it there.

```
sudo mount -t auto /dev/sda1 /mnt
```
and I think you can see the content of the linux partition at the directory ***/mnt***

---

### Post by WileyGaia on 2013-01-20
>  What live system is it? Ubuntu or some repair live system? Anyway try to mount it there.
Live 10.04 CD
I cannot mount the drive.

```
ubuntu@ubuntu:~$ sudo mount -t auto /dev/sda1 /mnt

```
 does not come back with a result, the cursor just flashes
and as previously stated, if i try click on Places\154GB filesystem it says: DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by sudodus on 2013-01-20
I see. Maybe your motherboard is too new for good old Lucid (10.04). I would try with a new version of Ubuntu, for example 12.04 LTS, which has drivers for new hardware.

But there could also be some other problem (for example some hardware or firmware issue). Can you try to connect the HDD to another computer (either directly or via an external casing)?

---

### Post by WileyGaia on 2013-01-20
So, if I install 12.04, (or 10.04 again for that matter) will I lose all the contents of my hard drive?

---

### Post by WileyGaia on 2013-01-20
> **sudodus said:**
>  Can you try to connect the HDD to another computer (either directly or via an external casing)?

I have a windows laptop. How do I connect the HDD to thaat? I do not have an external casing. Or the expertise to attempt that either...!

---

### Post by WileyGaia on 2013-01-20
Incidentally, the live CD will not shut down... (just carries on with the white and orange dots indefinitely...) - have to power down using the physical power button

---

### Post by WileyGaia on 2013-01-20
> **WileyGaia said:**
> Live 10.04 CD
I cannot mount the drive.

```
ubuntu@ubuntu:~$ sudo mount -t auto /dev/sda1 /mnt

```
 does not come back with a result, the cursor just flashes
and as previously stated, if i try click on Places\154GB filesystem it says: DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Ah - here is what it says about that:

```
DBus error org.freedesktop.DBus.Error.NoReply: 
Did not receive a reply. Possible causes include: 
the remote application did not send a reply, 
the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.
```

---

### Post by sudodus on 2013-01-20
1. There is a good alternative to 'power down using the physical power button' in Linux:

While pressing
***alt + SysRq***
continuously

you can press one letter key at a time, maybe one second each
to step down the run-levels and reboot in a controlled manner. This reduces the risk to damage the file system:

***r e i s u b***

'The alt + SysRq reisub method'

2. You might have a problem with a bad file system on the drive, that can be repaired when it is connected to another computer, but it is also possible (or even probable) that the HDD including the file system is good, so that you can retrieve the info, when connected to another computer.

a. You can buy a casing or an adapter for temporary use 'an IDE and SATA to USB adapter' or a 'SATA to USB adapter' if you are sure you have a SATA disk. It costs maybe 20-30 euros (25-35 dollars) and can save your personal data from the /home partition.

b. A good alternative is to find someone who can let you use his/her desktop computer, where it is much easier to connect an extra HDD internally with only the wiring (no adapter is needed). You need to boot into linux to be able to read the ext4 file system, so bring the Ubuntu CD and boot a live session. And bring a SATA cable, there is probably an extra power cable in the computer.

---

### Post by WileyGaia on 2013-01-21
I don't have access to a second desktop computer. I am gonna try find someone who could help, it will def. be a Windows machine though.
Reading more on this, do you think if I install and run "Boot Repair" from the Live CD session, I could fix this problem? [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by WileyGaia on 2013-01-21
> **grahammechanical said:**
> This might seem off topic but I have been getting this error message



I finally found a way to load the live session. I added



To the boot parameters. It might work for you. It might not. At the Grub menu press E and that will put Grub into Edit mode for that selection. Now look for a line that says quiet splash and insert the additional boot parameters in front.

If you want you can also remove quiet splash and then you will see the messages as the system loads and the point at which it stopped.

I was trying on a Live CD not a hard disk. But, who knows?

Regards.

I must sound like an idiot, but what is the "Grub menu"? And where do I find it? I did try push "Del" when it was starting up, and that takes me into the BIOS (I think?) But can't see anything referring to Grub or Quiet Splash...

---

### Post by dwb814 on 2013-01-21
Hi,
You might want to check your BIOS settings for which device is trying to boot. Go to your BIOS -> Boot -> and set your hard drive to the first boot device. Hit F10 and exit. Then see if it boots up.

Hope that helps

---

### Post by WileyGaia on 2013-01-21
> **dwb814 said:**
> Hi,
You might want to check your BIOS settings for which device is trying to boot. Go to your BIOS -> Boot -> and set your hard drive to the first boot device. Hit F10 and exit. Then see if it boots up.

Hope that helps

CD drive is first device
The HDD is the second device (which it uses if I don't put the Live CD in the CD drive), which is when it gives the error

---

### Post by sudodus on 2013-01-21
> **WileyGaia said:**
> I don't have access to a second desktop computer. I am gonna try find someone who could help, it will def. be a Windows machine though.
Reading more on this, do you think if I install and run "Boot Repair" from the Live CD session, I could fix this problem? [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yes Boot-Repair can help you.

See also this link

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by WileyGaia on 2013-01-21
So, still no real solutions to this issue...
Anyone able to at least answer these questions (these seem to be the only 2 feasible solutions:
Should I boot from Boot Repair Live CD to try fix this? If so will I lose my data?
OR
Should I install 12.04 to try fix this? If so will I lose my data?

---

### Post by sudodus on 2013-01-21
First I would try to connect the drive to another computer, and if possible save your personal data.

It is no problem if that other computer is a Windows computer. If you can mount it, there are many ways to continue:

- install drivers for ext file systems into Windows
- boot that computer from a live linux CD or USB drive.

If you can't mount it there, you need to try Boot-Repair or some other repair tool (often on a live CD or USB drive).

It is always risky to use tools, that not only read but also write onto a disk, particularly if it writes to the partition table.

---

### Post by ld114 on 2013-01-21
I think the most obvious conclusion is that your Ubuntu 10.04 installation is incompatible with your new motherboard.

There are two clear options:

1) Get an external USB HDD (always useful for backup) and then boot up a live session with Ubuntu 12.04 DVD. In the live session you should then be able to copy all the data you need from your internal HDD on to the external HDD. Then install Ubuntu 12.04 on your PC and your data will be available on the external HDD.

2) Replace the internal HDD in your PC. I have this piece of kit (hopefully something like it is available in Joburg):

[http://www.amazon.co.uk/gp/product/B001A5SK56/ref=oh_details_o03_s00_i00](http://www.amazon.co.uk/gp/product/B001A5SK56/ref=oh_details_o03_s00_i00)

This enables you to connect up an IDE or SATA HDD (2.5 or 3.5 inch) to your PC as a USB disk. You can then copy your data on to your new disk - which you can have installed 12.04 on.

Hope this is helpful.

---

### Post by arpanaut on 2013-01-21
Neither the Live CD nor boot repair should do anything that will cause loss of data.
Choose "Try" when the cd boots, and this will take you to a live session of the desktop from which you can install boot repair program, then you can run that to produce a report on the status of you disk relative to booting.
Also you could start the Disk Utility and then check the status of your disk, and run a file system check from there.
Did you have any disk encryption set up on your system?
Was the reason for the replacement of your MB system failure? Were you using The disk when this occurred? If so some corruption to the file system may have happened, so a file system check would be necessary.

---

### Post by WileyGaia on 2013-01-28
OK, apologies for delay with response, only got a chance tonight to do something about this - so I took a chance and created a USB Boot Disk Repair flash drive using YUMI, changed the Boor priority on the BIOS settings, went into the Boot Disk repair utility, selected "Recommended Boot Repair", and that took a little while (3-4minutes), restarted machine, which then went into a menu telling me about which version of Grub I wanted (I just let it time out and select the default one), that then looped once, restarted the machine, and then... IT STARTED!!! YEAH! All data/ files on HDD in tact!!!
Thanks to all for the input and helpful suggestions.
And thanks to whoever invented Boot Disk Repair!!!

---

