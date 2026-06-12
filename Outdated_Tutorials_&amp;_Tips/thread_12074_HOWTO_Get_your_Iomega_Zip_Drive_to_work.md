---
title: "HOWTO: Get your Iomega Zip Drive to work"
date: 2005-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by pseudonym on 2005-01-21
Going through zip drive hell? Unfortunately these devices don't always work 'out-of-the-box' on some Linux systems, but it's nothing a little manual configuration can't fix. Here's a detailed (and substantially revised) how-to for mounting your zip disks in Ubuntu Warty (for Hoary there are a couple of different steps. If you are using Ubuntu Hoary visit the Hoary Tips & Tricks forum). First off, the basics -

1. Create a mountpoint. The default is /media/zip0. Open up a terminal and type sudo mkdir /media/zip0 . This is the directory which will eventually contain your drive's contents.

2. (optional) Create a symbolic link '/media/zip' - sudo ln -s /media/zip0 /media/zip . Not strictly necessary, but gives your drive a slightly shorter name to be referenced by.

3. Establish your drive's device name. This depends on where it is connected. In Linux, IDE devices are named according to the following pattern-

/dev/hda Primary IDE Controller Master (usually your hard drive)
/dev/hdb Primary IDE Controller Slave
/dev/hdc Secondary IDE Controller Master (usually your CD-ROM)
/dev/hdd Secondary IDE Controller Slave

Look in Computer>System Configuration>Device Manager. Scroll down to your zip drive and click the 'Advanced' tab. Next to 'block.device' should appear your drive's device name. This will most likely be '/dev/hd*4' (where '*' depends on where your drive is connected according to the above scheme). The '4' here is the partition number. For some reason, Iomega disks formatted with the stock FAT16 filesystem use partition number 4. You can reformat them if you wish (see below), although I don't recommend using any filesystem type other than FAT16 or FAT32. Always use partition 4 on the zip disk for any FAT filesystem, however.

5. Once you know the device name, edit /etc/fstab - sudo gedit /etc/fstab . This file controls how all your drives are mounted. You need to add a line which looks like this (my drive is the secondary slave, therefore 'hdd') -

/dev/hdd4 /media/zip0 auto rw,user,noauto,sync 0 0

(you will notice in Device Manager that the filesystem 'policy' for zip drives is 'auto'. Specifying the actual filesystem used usually produces an error on mounting).

6. Refresh /etc/fstab - sudo mount -a . A zip drive icon should now appear in Computer>Disks.

You now need to create a device node for your zip drive in the /dev directory. If you look here you will see a node for device block 'hd*' (your actual zip *drive* , but not for the partition 'hd*4' (unlike your hard drive(s)). This node is needed in order to mount your disk. It's normally the job of the module 'ide_floppy' (your zip drive's Linux device driver) to create it, but this will only get done if there is a zip disk inserted at boot-up, when the kernel loads all the modules (I don't know if this is a bug, but it's just the way it is). You can, of course, insert one each time before switching your computer on, but if you'd rather not there are a few simple steps you can do to get around this -

7. To ensure the 'ide_floppy' module is loaded at boot-up add a line 'ide-floppy' (without quotes) to /etc/modules (if you don't mind inserting a zip disk before booting up, skip to step 10 after rebooting at this point).

8. Tell Ubuntu to create a device node manually during each boot-up by hacking another file - sudo gedit /etc/udev/links.conf . You will need to add a line that looks similar to this -

# Manually create a zip device.
M hdd4 b 22 64

What this line stands for is ' M(ake) hdd4 (a) b(lock device with major number) 22 (and minor number) 64' (your device name, major and minor numbers may differ from mine, of course) . The major and minor numbers for hd*4 are listed under your zip drive's entry in Device Manager (Advanced tab). Once you have the details, insert your line in /etc/udev/links.conf using the syntax above. 

9. Save, exit, and reboot (you will see a message in the 'Loading Modules...' section about a disk not being in a drive. Ignore it. It is of no consequence). Now if you look in /dev you will notice a device node 'hd*4' has magically appeared!

10. Now insert a zip disk and type mount /dev/hd*4 or mount <your mountpoint>. You will likely get an error message, but don't sweat it - Ubuntu is just 'getting used to' the device that you created manually. You may have to run the 'mount' command a couple of times before you succeed. It's messy, but it works. ;)

This how-to will work for ATAPI/IDE zip 100 drives (and probably zip 250). The procedure is slightly different for parallel port, SCSI etc., but there are other threads around which cover those. You will also note that your disks won't automount and open a browser window, even if other removable media is set to do so. I don't know why this is so but solutions to this are more than welcome! :)

REFORMATTING ZIP DISKS -

The following is an excellent guide on how to do this using fdisk -

[http://wls.wwco.com/lqh/iomega.php](http://wls.wwco.com/lqh/iomega.php)

Follow it to the point where you write the new partition table to the disk (option 'w') then quit fdisk (and the above guide). Format it to FAT32 by running sudo mkfs -t vfat /dev/hdd4 , or, if possible, use Windows to do this. Using Linux tools to format disk partitions with Windows filesystems can be a bit buggy sometimes. It should work fine, but Windows will often read the filesystem as FAT rather than FAT32 - your call as to whether this is a problem for you.

You can use Linux filesystems if you want but you are likely to run into problems with the file permissions and be unable to write to your zip disk. Of course, you can try changing them with chmod, but they have a curious habit of returning to their original root user state. It also chops 10MB off the disk's capacity. To avoid these headaches, just use FAT32.

If you do choose Linux formatting, use ext2, and remember to use partition 1, otherwise your disk won't moun99t. Adjust accordingly for all the above instructions.

Hope this helps!

UNMOUNTING YOUR DISK -

If you have problems ejecting your zip disk make sure you are following the correct procedure for doing so. First off, you need to unmount it -

umount <YOUR DEVICE NAME> or <MOUNTPOINT>

Properly unmounting removable media in Linux is necessary to avoid the risk of data loss.

If you find the above still doesn't work, do what's known as a 'lazy' unmount -

umount -l <YOUR DEVICE NAME> or <MOUNTPOINT>

You should now be able to use the 'eject <YOUR DEVICE NAME> or <MOUNTPOINT>' command (or just press the button on your zip drive) and have it do exactly that.

---

### Post by Campitor on 2005-01-22
Hello:

  I followed your instructions to the note, including manually creating the zip device;  now I have a hdd4 in my /dev/ list, I have the following line in fstab:

/dev/hdd4   /media/zip0   auto    rw,user,noauto 0 0

and have rebooted a couple of times.  Each time I try to mount the zip drive I get the following error message:

mount: I could not determine the filesystem type, and none was specified

I've tried changing the fstab entrey from /dev/hdd4 to /dev/hdd and still doesnt work.  In my Disks Folder, I have an entry for "Zip Disk 1" is that one (1) normal?  Do I need to change something in the fstab?  Include vfat as the only filetype?  Please help...

Camp

---

### Post by pseudonym on 2005-01-22
Hi. The 'Zip Disk 1' entry in Computer > Disks is as it should be. Using 'hdd' as the device name won't do anything, as this refers to the block for your device (like 'hda' for your hard disk). You must always have a partition number for the entry to be valid. Have you checked if you have another device block listed in /dev , such as 'hdb'?

Assuming you have your device name correct ('hdd4'), your suggestion of manually specifying the filesystem in /etc/fstab sounds like a good one...

---

### Post by Campitor on 2005-01-26
[QUOTE=pseudonym]Hi. The 'Zip Disk 1' entry in Computer > Disks is as it should be. Using 'hdd' as the device name won't do anything, as this refers to the block for your device (like 'hda' for your hard disk). You must always have a partition number for the entry to be valid. Have you checked if you have another device block listed in /dev , such as 'hdb'?

Assuming you have your device name correct ('hdd4'), your suggestion of manually specifying the filesystem in /etc/fstab sounds like a good one...[/QUOTE]
 Hi:

    I changed my /etc/fstab entry to include only vfat as the filesystem. My Zip drive is close to working perfectly:  it mounts correctly, I can access the files, and I can unmount.  the problem comes when I try to eject the Zip-disk.  For some bizarre reason, my drive will not eject the zip-disk.  If I do a right-click and select "Eject" the drive starts spinning, but will not eject the disk.  If I go into a terminal and type:

eject -v /dev/hdd4

It will let me know that the drive was unmounted, and the eject CD-Rom process ended successfully, but no Zip disk on sight.  Additionally, if I press the botton on the Zip-drive itself, I cant get the disk to eject.  I have to restart the computer in order to get the disk.

Do I have to load any module that will eject the Zip-disK?  Is there anything I can twick or modify in order for eject the disk?  to answer your question, I do have another Hard-drive which was asssinged the hdb1 partition.  

Thanks,  Camp.

---

### Post by Poldi on 2005-01-26
ok.

now who can tell me how this works for a parallelport ZIP-drive?

not that I want to use this regularly, but I have one and some ZIP-discs that hold data that I need. 

thanks and regards,
Carsten

---

### Post by pseudonym on 2005-01-27
[QUOTE=Poldi]ok.

now who can tell me how this works for a parallelport ZIP-drive?

not that I want to use this regularly, but I have one and some ZIP-discs that hold data that I need. 

thanks and regards,
Carsten[/QUOTE]

Hallo,

I haven't got such a drive but I might still be able to help you a little. I've read that the module you need to add to /etc/modules is 'ppa'.  I've also read that parallel port devices (other than printers) have device names which start with 's' (eg. 'sg', 'sd'), and that they always like to use the number 4. Is the drive already connected to your machine? If so, look in your /dev folder for an icon (eg. 'sd4').

Other than that my howto is probably not much use to you, seeing as we're talking about parallel port now and not ATAPI/IDE. Let us know how you go anyway...

---

### Post by whell on 2005-03-14
I've followed these instrucitons, and I'm still having a bit of trouble.  When I go to the computer folder, I have a Zip drive icon.  When I click on it, I get the following message:

mount: I could not determine the filesystem type, and none was specified

Anyone know how I might be able to correct this?

---

### Post by WimVriend on 2005-03-14
[QUOTE=whell]I've followed these instrucitons, and I'm still having a bit of trouble.  When I go to the computer folder, I have a Zip drive icon.  When I click on it, I get the following message:

mount: I could not determine the filesystem type, and none was specified

Anyone know how I might be able to correct this?[/QUOTE]

Hello,
Try "sudo modprobe ppa" (for parallel zipdrive's) in a terminal before you mount the zipdrive.
Try "sudo fdisk -l" in a terminal to see wich device it is, ( /dev/sda1 ?? )
Install "jazip" 
Run jazip, it wil make an mount directory for you. With jazip you can mount and unmount the zipdrive. If that's working put "ppa" als last line in /etc/modules.
Go to /system/preferences/sessions and put jazip in it.
From now on jazip is running everytime you reboot your'e computer, and asking what to do when you have rebooted.
Wim

---

### Post by pseudonym on 2005-03-15
[QUOTE=whell]I've followed these instrucitons, and I'm still having a bit of trouble.  When I go to the computer folder, I have a Zip drive icon.  When I click on it, I get the following message:

mount: I could not determine the filesystem type, and none was specified

Anyone know how I might be able to correct this?[/QUOTE]

Is 'auto' listed as the filesystem type in the fstab entry for your zip drive? If that doesn;t work try manually specifying the fs eg. 'vfat'. I don't know why, but some systmes prefer this instead of 'auto'.

If you are able to mount the drive but still get this message, then don't worry about it. It pops up on my machine sometimes but the drive is still mounted and can be used without problem. One thing I've noticed is that if you mount the zip drive using the mountpoint instead of the device name (especially on the first use during a session) it is less likely to report messages. At least this is the case on my system.

All this sounds pretty unscientific but the good news is that these problems should no longer exist in Ubuntu's next stable release due in early April. I read somewhere here that support for zip devices will b e better implemented then (at least I hope this is true! ;) )

---

### Post by jsgotangco on 2005-03-15
I don't want to troll, but I'm surprised zip drives are still available; the last zip drive i ever used was a 250MB model after that, I switched to flash drives.

---

### Post by whell on 2005-03-15
Yeah, I know I'm old school.  But when the machine you're nursing is a 7 year old Pentium II 400 MHZ machine, you're gonna have some old school hardware.  And, I'm still in the habit of using it.  Works fine for me on what I use it for.  

I'll retry some of these suggestions tonight and see what happens.  Thanks!

---

### Post by pseudonym on 2005-03-18
[QUOTE=jsgotangco]I don't want to troll, but I'm surprised zip drives are still available; the last zip drive i ever used was a 250MB model after that, I switched to flash drives.[/QUOTE]

I use a 128MB flash drive now, too, just for its portability, and thought about junking my zip drive. The reason I still have it? It's cheaper! :) I use it as part of my backup regime- fill up 7 100MB zip disks then burn all that on to a CD, rinse and repeat. Sure, I could do the same using a 1 GB flash drive, but why spend the extra cash when my (admittedly 5-years-old) zip drive is still in perfect working order? ;)

---

### Post by kont.raen on 2005-10-31
[QUOTE=Campitor]Hi:

    I changed my /etc/fstab entry to include only vfat as the filesystem. My Zip drive is close to working perfectly:  it mounts correctly, I can access the files, and I can unmount.  the problem comes when I try to eject the Zip-disk.  For some bizarre reason, my drive will not eject the zip-disk.  If I do a right-click and select "Eject" the drive starts spinning, but will not eject the disk.  If I go into a terminal and type:

eject -v /dev/hdd4

It will let me know that the drive was unmounted, and the eject CD-Rom process ended successfully, but no Zip disk on sight.  Additionally, if I press the botton on the Zip-drive itself, I cant get the disk to eject.  I have to restart the computer in order to get the disk.

Do I have to load any module that will eject the Zip-disK?  Is there anything I can twick or modify in order for eject the disk?  to answer your question, I do have another Hard-drive which was asssinged the hdb1 partition.  

Thanks,  Camp.[/QUOTE]

Hi,

while I cannot offer you a solution to your problem I just want to add my own experiences in that regard : 

There is an old parallel port Zip100 drive attached to my PC and after setting it up (the way it is described in this thread) it works just fine but for one point - ejecting (what a surprise). When I order a disk to be ejected (whether  per right click on the desktop or from the shell) it gets unmounted properly and I can hear the typical "initial" sound the drive makes when ejecting a disk - but that's about it. Nevertheless, differing from your (internal?) drive, the disk comes out when I press the drive's eject button, though.

Might it be, that there is some bug in the sequence for ejecting removable media, that causes zipdrives not to react?

---

### Post by carla on 2006-11-04
> **pseudonym said:**
> ...
# Manually create a zip device.
M hdd4 b 22 64

What this line stands for is ' M(ake) hdd4 (a) b(lock device with major number) 22 (and minor number) 64' (your device name, major and minor numbers may differ from mine, of course) ...

I just wanted to thank you, not only for this fine tutorial, but for your taking the extra time, as quoted above, explaining what we were doing and the why of it all. 8-)

---

### Post by PatrickMay16 on 2006-11-05
Hey guys.
Sorry to bother you all, but, I recently ordered an external iomega zip drive  from ebay (one that plugs in the USB port).

I assume this guide is only for internal ones which don't plug in the USB port.
So I'd like to ask. Will I need this guide, or will it work just like any other USB removable storage does in Ubuntu?

---

### Post by afoglia on 2006-11-05
> **PatrickMay16 said:**
> 
Sorry to bother you all, but, I recently ordered an external iomega zip drive  from ebay (one that plugs in the USB port).

I assume this guide is only for internal ones which don't plug in the USB port.
So I'd like to ask. Will I need this guide, or will it work just like any other USB removable storage does in Ubuntu?

Let's put it this way: When I saw this thread, my first thought was "Why is a HOWTO needed?  My Zip drive just worked."  I was using a USB-powered 250 MB Zip and it worked perfectly with Ubuntu.  Both Breezy and Dapper.  I haven't tested, but I can't see why it wouldn't work with Edgy.

---

### Post by PatrickMay16 on 2006-11-05
> **afoglia said:**
> Let's put it this way: When I saw this thread, my first thought was "Why is a HOWTO needed?  My Zip drive just worked."  I was using a USB-powered 250 MB Zip and it worked perfectly with Ubuntu.  Both Breezy and Dapper.  I haven't tested, but I can't see why it wouldn't work with Edgy.
I get you, man. Thanks.
Another question... I noticed some place selling 200MB zip disks, and another place selling 700MB zip disks. And I see you mentioning specifically 250MB there... so I ask, can zip drives read all different sizes of zip disk, or can you only read 700MB zip disks in special zip drives?
Like, say for example I were to give you a 700MB zip disk. Would you be able to read/write with it in the zip drive that you have?

Sorry if this is a silly question.

---

### Post by thegurr on 2007-11-09
Thanks for this.  I'm an absolute noob and any help is welcome.  I wondered if you could clarify something for me.  I think I've followed everything up to step 8 but am stumped at the Major Minor numbers.  I'm in the device manager looking at me Iomega 250 USB advanced tab and don't know which numbers I'm supposed to be looking at.  Not sure if it makes a difference but I'm using 7.10 gutsy gibon.  Any info would be much appreciated.

---

