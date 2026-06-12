---
title: "Problem connecting to external hard-drives"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-18
Hi all

Just created a dual-boot with XP, on my Dell desktop.  That was the easy bit, (except the graphics card, which I'm working on).
I already have one completely Ubuntu system, but need to access specific files on this PC.

However, I can't get it to see the two external Seagate hard-drives.  They are connected via Firewire (IEEE1394) and they can both be accessed via the Windows partition.

Any advice would be gratefully received.

Thanks.

---

### Post by dhtseany on 2008-09-18
Does your hard drive have a USB option on it? AKA can you use a USB cable as well to plug it in? If so then try USB and see if you have any success. 

Also, what format (FAT32, NTFS, ext3, etc.) are you using on the external?

Peace
Sean

---

### Post by C.S.Cameron on 2008-09-18
Did you look in media for the drives?

---

### Post by Therion on 2008-09-18
Are these SATA hard drives?  

I had to play around with the AHCI setting in my BIOS to get SATA drives playing nice on my dual-boot ('buntu/XP) system.

---

### Post by bobnutfield on 2008-09-18
Open a teminal and type:

> sudo lsmod

Do you have the ieee1394 module loaded?

---

### Post by jrsc109 on 2008-09-18
Hi Bob

I ran your request with the following output:

ieee1394               93752  2 sbp2,ohci1394

Is that correct?  Does that mean I have ieee1394 working.

I've tried with USB, but they're still not recognised.

Thanks

---

### Post by bobnutfield on 2008-09-18
Yes that is the correct module.  I use it for my video camera to capture video.  Your firewire port should be recognized.  You might trying to mount the drive manually (but I will have to admit that I have never mounted a firewire drive).  I am sure the process is the same, but I will have to do a little research to give the exact command.  I will get back to you.  Late here so I may have to bookmark the page and if no one else posts an answer for you first, I will post back tomorrow.

---

### Post by bobnutfield on 2008-09-19
I've gathered a little more information.  If you have not solved the problem yet, try this.  Open a terminal and type:

> cat /proc/scsi/scsi

If you get output correctly, you should see your Firewire hard drive listed.  If so, it will proved the /dev/sdX name given by Ubuntu.  Then it can be mounted manually.  If you want it mounted automatically at boot, we can edit your /etc/fstab file

---

### Post by jrsc109 on 2008-09-19
Hi Bob; the output of the command is

julian@Office:/$ sudo cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: SONY     Model: DVD-ROM DDU1615  Rev: FDS2
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVD+-RW GWA4164B Rev: D108
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3160812AS      Rev: 3.AD
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: TEAC     Model: USB   HS-CF Card Rev: 4.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 01
  Vendor: TEAC     Model: USB   HS-xD/SM   Rev: 4.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 02
  Vendor: TEAC     Model: USB   HS-MS Card Rev: 4.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 03
  Vendor: TEAC     Model: USB   HS-SD Card Rev: 4.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi9 Channel: 00 Id: 00 Lun: 00
  Vendor: Initio   Model: ST3200822A       Rev: 4.07
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi10 Channel: 00 Id: 00 Lun: 00
  Vendor: Initio   Model: ST3200822A       Rev: 4.07
  Type:   Direct-Access                    ANSI  SCSI revision: 00


I've identified the last entry as the firewire connected hard drive, but now I'm stuck.  How do I edit the /etc/fstab file with this information?

Sorry - really coming across as a newbie now!!

Thanks

---

### Post by bobnutfield on 2008-09-20
OK, now that you know the drive is recognized, you can type:

> sudo fdisk -l

Then you should see /dev/sdx (where x is your firewire drive).  I can give you the command to add to your /etc/fstab to mount automatically at each boot, but we need to first confirm that we can mount it manually successfully.  Post the information from fdisk -l.

---

### Post by jrsc109 on 2008-09-21
Response from command:

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf96c5dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       24321   195358401    c  W95 FAT32 (LBA)

Disk /dev/sdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa621df2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       24321   195358401    c  W95 FAT32 (LBA)


Hope that makes sense to you!!!

Thanks

---

### Post by angelsguitar on 2008-09-21
If your HD's are formated in NTFS, try installing ntfs-config from the repositories, either using Synaptic or the terminal.  After that, run the utility, which should appear on the Applications menu under "System Tools", and select all checkmarks that will appear on the following windows.  That utility will edit your fstab automatically so that any HD formated with NTFS that you connect to Ubuntu will be auto mounted.

---

### Post by jrsc109 on 2008-09-23
It looks as though both the HD are FAT32 - please help with how these can be mounted.  Thanks

---

### Post by jrsc109 on 2008-09-23
UPDATE - I have managed to manually mount these drives - so now for the next bit:
1. How do I set them up in the fstab file so that they will automatically mount
2. There are 2 identical hard drives, daisy-chained together and connected via a single firewire port - the fdisk -l command shows the same UID

So near and yet so far.  Please help.  Thanks

---

### Post by jrsc109 on 2008-09-25
I'll make this my last plea for help on this one...

Here's the story.
2 x FAT32 external 200Gb Seagate hard drives.  Daisy-chained together, and connected via a single Firewire cable to the PC.

I can mount them both manually; so I know they can be accessed.

My problem, is how do I set them up in the fstab file so they connect automatically; either on PC boot, or when I switch the hard drives on.

This is the last thing that is preventing me from converting completely to Linux; and it would be a shame not to 'win' this battle.

Thanks again.

---

### Post by egalvan on 2008-09-25
> **jrsc109 said:**
> I'll make this my last plea for help on this one...

Here's the story.
2 x FAT32 external 200Gb Seagate hard drives.  Daisy-chained together, and connected via a single Firewire cable to the PC.

I can mount them both manually; so I know they can be accessed.

My problem, is how do I set them up in the fstab file so they connect automatically; either on PC boot, or when I switch the hard drives on.

This is the last thing that is preventing me from converting completely to Linux; and it would be a shame not to 'win' this battle.

Thanks again.


How do you mount them manually?

I use firewire drives under Ubuntu and always find them under the "Places" tab on the top menu bar.
I Click on them and they mount. No other action needed on my part.

On my "well-abused" machine, it's another matter... I've gotten this machine to the point that it refuses to mount ANY drive other than the boot one. :) but that's MY fault, not Ubuntu or Linux. :)

---

### Post by egalvan on 2008-09-25
> **jrsc109 said:**
> I'll make this my last plea for help on this one...

Here's the story.
2 x **FAT32** external **200Gb** Seagate hard drives

Hmmm, one more question, 

any SPECIFIC reason to format a 200gb drives with FAT32?

The amount of wasted slack has to be tremendous.

ErnestG

---

### Post by jrsc109 on 2008-09-26
> **egalvan said:**
> How do you mount them manually?

I use firewire drives under Ubuntu and always find them under the "Places" tab on the top menu bar.
I Click on them and they mount. No other action needed on my part.

I used the following
julian@Office:~$ sudo mount -t vfat -o umask=0000 /dev/sdf1 /media/fat1
julian@Office:~$ sudo mount -t vfat -o umask=0000 /dev/sdg1 /media/fat2
julian@Office:~$ 

They appear under 'Places' and it seems to do the trick; plus I have read/write access.

FAT32 because that is how it came out of the box - I didn't do any formatting, just plugged it in and off it went.  Originally connected to WinXP.

So, what it the fstab entry for these drives. (or one of them, to get me started)?

Thanks

---

### Post by egalvan on 2008-09-26
> **jrsc109 said:**
> I used the following
julian@Office:~$ sudo mount -t vfat -o umask=0000 /dev/sdf1 /media/fat1
julian@Office:~$ sudo mount -t vfat -o umask=0000 /dev/sdg1 /media/fat2
julian@Office:~$ 

[B]They appear under 'Places' and it seems to do the trick; plus I have read/write access.
[/B]
FAT32 because that is how it came out of the box - I didn't do any formatting, just plugged it in and off it went.  Originally connected to WinXP.

So, what it the fstab entry for these drives. (or one of them, to get me started)?

Thanks

How important is it that they mount automatically?
Is some process depending on it?
I ask because removable drives are not usually automounted...
And it only takes two mouse clicks to access them...

My main fire-wire machine has a borked install, and NOTHING mounts on it, except the boot drive.
I will be re-installing 8.04.1 in a week or two, just need to find a way to migrate data off the drives.
 I will have to use extra long cables to reach inside the case for the drives, and use a laptop to grab my data.

In the mean-time. if you are really stuck with this, you may consider a new post.
After all, your original problem is "solved"... you CAN connect and use your external drives.
Now you need help to AUTOMOUNT them.

You can name your new post "How to auto-mount external drive?"
Include the commands you use to manually mount, and also post the output of 
```
fstab -l
```

in your post.


And finally, i found this thread

[http://ubuntuforums.org/showthread.php?t=785263&highlight=auto-mount+external+drive](http://ubuntuforums.org/showthread.php?t=785263&highlight=auto-mount+external+drive)

look at post #6

change 'sda4' to 'sdf1' or 'sdf1', and ntfs to fat32 (unsure obaout the proper name) and you should be ok, but i ahve no way to test this right now.

any other forum member have any ideas?

ErnestG

P.S.
Look into using 'pmount'. You can find it in Synaptic.
This is a copy of the description...

[B]mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.[/B]

---

### Post by egalvan on 2008-09-26
sorry, double post

---

