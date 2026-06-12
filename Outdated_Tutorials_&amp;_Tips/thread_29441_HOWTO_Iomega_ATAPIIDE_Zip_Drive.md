---
title: "HOWTO: Iomega ATAPI/IDE Zip Drive"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by pseudonym on 2005-04-24
Going through zip drive hell? Unfortunately these devices don't always work 'out-of-the-box' on some Linux systems, but it's nothing a little manual configuration can't fix. Here's a detailed how-to for mounting your zip disks in Ubuntu Hoary (for Warty there are a couple of different steps. If you are using Ubuntu Warty visit the Warty Tips & Tricks forum). First off, the basics -

1. Create a mountpoint. The default is /media/zip0. Open up a terminal and type sudo mkdir /media/zip0 . This is the directory which will eventually contain your drive's contents.

2. (optional) Create a symbolic link '/media/zip' - sudo ln -s /media/zip0 /media/zip . Not strictly necessary, but gives your drive a slightly shorter name to be referenced  by.

3. Establish your drive's device name. This depends on where it is connected. In Linux, IDE devices are named according to the following pattern-

/dev/hda Primary IDE Controller Master (usually your hard drive)
/dev/hdb Primary IDE Controller Slave
/dev/hdc Secondary IDE Controller Master (usually your CD-ROM)
/dev/hdd Secondary IDE Controller Slave

Look in System>System Administration>Device Manager. Scroll down to your zip drive and click the 'Advanced' tab. Next to 'block.device' should appear your drive's device name. This will most likely be '/dev/hd*4' (where '*' depends on where your drive is connected according to the above scheme). The '4' here is the partition number. For some reason, Iomega disks formatted with the stock FAT16 filesystem use partition number 4. You can reformat them if you wish (see below), although I don't recommend using any filesystem type other than FAT16 or FAT32. Always use partition 4 on the zip disk for any FAT filesystem, however.

5. Once you know the device name, edit /etc/fstab - sudo gedit /etc/fstab . This file controls how all your drives are mounted. You need to add a line which looks like this (my drive is the secondary slave, therefore 'hdd') -

/dev/hdd4 /media/zip0 auto rw,user,noauto,sync 0 0

(you will notice in Device Manager that the filesystem 'policy' for zip drives is 'auto'. Specifying the actual filesystem used usually produces an error on mounting).

6. Refresh /etc/fstab - sudo mount -a . A zip drive icon should now appear in Places>Computer.

You now need to create a device node for your zip drive in the /dev directory. If you look here you will see a node for device block 'hd*' (your actual zip *drive*  , but not for the partition 'hd*4' (unlike your hard drive(s)). This is needed in order to mount your disk. It's normally the job of the module 'ide_floppy' (your zip drive's Linux device driver) to create it, but this will only get done if there is a zip disk inserted at boot-up, when the kernel loads all the modules (I don't know if this is a bug, but it's just the way it is). You can, of course, insert one each time before switching your computer on, but if you'd rather not there are a couple of simple steps you can do to get around this. They involve letting Ubuntu know about '/dev/hd*4' by running a couple of system programs-

7. Insert a zip disk and run sudo cfdisk /dev/hdd , press 'q' to quit, then sudo fdisk -l to list all your partition tables. You will hear your disk being detected and 'dev/hd*4' will be listed (you must run *both* of these commands for this to work). Now, if you look in /dev, your longed for device node 'hd*4' will be there! (Once it has been created you won't have to perform this step again until your next reboot).

8. Type 'mount /dev/hd*4' or mount <your mountpoint> and your disk will be mounted according to the fstab entry you made above. You're done! :)

I haven't had any issues following the above steps but if, for some reason, you are unable to create your device node, you can tell Ubuntu to create one manually during each boot-up -

Run sudo gedit /etc/udev/links.conf . Among other things, this file enables you to create system devices manually. To do this for a zip drive, you will need to add a line that looks similar to this -

# Manually create a zip device.
M hdd4 b 22 64

What this line stands for is ' M(ake) hdd4 (a) b(lock device with major number) 22 (and minor number) 64' (your device name, major and minor numbers may differ from mine, of course) . The major and minor numbers for hd*4 are listed under your zip drive's entry in Device Manager (Advanced tab). Once you have the details, insert your line in /etc/udev/links.conf using the syntax above. Save, exit, and reboot.

Now insert a zip disk and type mount /dev/hd*4 or mount <your mountpoint>. You will likely get an error message, but don't sweat it - Ubuntu is just 'getting used to' the device that you created manually. You may have to run the 'mount' command a couple of times before you succeed. It's messy, but it works.

This how-to will work for ATAPI/IDE zip 100 drives (and probably zip 250). The procedure is slightly different for parallel port, SCSI etc., but there are other threads around which cover those. You will also note that your disks won't automount and open a browser window, even if other removable media is set to do so. I don't know why this is so but solutions to this are more than welcome! :) 

REFORMATTING ZIP DISKS -

The following is an excellent guide on how to do this using fdisk -

[http://wls.wwco.com/lqh/iomega.php](http://wls.wwco.com/lqh/iomega.php)

Follow it to the point where you write the new partition table to the disk (option 'w') then quit fdisk (and the above guide). Format it to FAT32 by running sudo mkfs -t vfat /dev/hdd4 , or, if possible, use Windows to do this. Using Linux tools to format disk partitions with Windows filesystems can be a bit buggy sometimes. It should work fine, but Windows will often read the filesystem as FAT rather than FAT32 - your call as to whether this is a problem for you.

You can use Linux filesystems if you want but you are likely to run into problems with the file permissions and be unable to write to your zip disk. Of course, you can try changing them with chmod, but they have a curious habit of returning to their original root user state. It also chops 10MB off the disk's capacity. To avoid these headaches, just use FAT32.

If you do choose Linux formatting, use ext2, and remember to use partition 1, otherwise your disk won't mount. Adjust accordingly for all the above instructions.

Hope this helps! :)

UNMOUNTING YOUR DISK -

If you have problems ejecting your zip disk make sure you are following the correct procedure for doing so. First off, you need to unmount it -

umount <YOUR DEVICE NAME> or <MOUNTPOINT>

Properly unmounting removable media in Linux is necessary to avoid the risk of data loss.

If you find the above still doesn't work, do what's known as a 'lazy' unmount -

umount -l <YOUR DEVICE NAME> or <MOUNTPOINT>

You should now be able to use the 'eject <YOUR DEVICE NAME> or <MOUNTPOINT>' command (or just press the button on your zip drive) and have it do exactly that.

---

### Post by Perfect Storm on 2005-04-24
Mavelous howto!!! Great work! Diffently get my vote.  \\:D/

---

### Post by pseudonym on 2005-04-25
Thanks :) I'd originally done this a while back in the Warty HOWTOS, but thought it's probably a good idea to put it in here as well. There are still a few of us diehard zip drive users out there! :)

---

### Post by ignavia on 2005-04-25
Howabout a parallel drive?

---

### Post by pseudonym on 2005-04-25
[QUOTE=ignavia]Howabout a parallel drive?[/QUOTE]

Sorry, can't help you there. I've never used any parallel port devices apart from a printer, which never gave me any problems. I'm pretty sure other users have posted about this, though. Just do a forum search :)

---

### Post by ignavia on 2005-04-25
Yeah, I could, but my parallel port Zip has been disconnected for quite a long time. I do have some stuff on Zip disks that I may want to retrieve one day, but until then, it's very low priority.

---

### Post by brj on 2005-05-26
for the parallel iomega zip 100 plus you have to load the module 'imm'

1.) create the directory where you want to mount the zip:
sudo mkdir /media/zip

2.) load imm module:
sudo modprobe imm

3.) mount it:
sudo mount /dev/sda4 /media/zip

afaik for the original zip 100 you'll have to use the 'ppa' module

jakob

---

### Post by pseudonym on 2005-05-27
[QUOTE=brj]3.) mount it: sudo mount /dev/sda4 /media/zip[/QUOTE]

/dev/sda4? Does this mean that a parallel port zip drive has to be run under SCSI emulation? Or will IDE do ie. /dev/hdd4?

---

### Post by jnoreiko on 2005-08-05
Are there any plans to add better support for zip drives in Breezy?

---

### Post by kevanf1 on 2005-09-26
May I add a little to the previous advice about installing a parallel Zip Drive.  This is how I have done it avoiding the need to modprobe manually everytime I boot up my Ubuntu/Kubuntu box.

Open up the /etc/modules file in your favourite text editor - I used Kate in Kubuntu - while logged in as either su or root.  I've set up my system to log into root which is not default in Ubuntu/Kubuntu.

for an Iomega 250 parallel drive add the line:

[COLOR="Blue"]imm[/COLOR]

for an older Iomega 100 parallel drive you will need to add the line:

[COLOR="Blue"]ppa[/COLOR]

save and close the file.

You may need to enter your **BIOS** configuration and set the parallel port properties to **SPP**

At this stage you need to create a mount point in order for Ubuntu/Kubuntu to know where to mount your Zip drive :) 

In a terminal (again as su or root) enter 

*mkdir /mnt/zip100.0* (for a Zip 100 drive) or 

*mkdir /mnt/zip250.0* (for a Zip 250 drive).

Now, in your favourite text editor (su or root remember) again, open up your fstab file and, at the end of the file enter the following line for a Zip 100:

/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0

or for a Zip 250:

/dev/sda4 /mnt/zip250.0 vfat noauto,user 0 0

That should be it :cool: however, I have found that sometimes you may need to adjust permissions.

Good luck.

---

### Post by Ernest Pons-Worley on 2006-04-19
Built-in PowerPC Iomega ATAPI/IDE Zip drive (100 MB) would not mount on Breezy Badger. I tried the instructions at the beginning of this thread.

The zip disk mounts for just an instant then disappears from the desk top. No error message is generated. If I type "eject zip0" from the command line I hear the zip disk spin, but then it stops and will not eject.

Mac PowerPC (Old World Beige G3) updgraded to 500MHz G4 processor, RAM is maxed out, two USB PCI cards (4 ports) added. Internal read only and external (USB) read/write CD drives. Internal floppy and Iomega Zip drives. Everything works, except the Zip. (Note: Zip drive works properly under Mac OS 9)

---

### Post by spartan777 on 2006-04-25
[QUOTE=kevanf1]
...Now, in your favourite text editor again, enter the following line for a Zip 100:

/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0

or for a Zip 250:

/dev/sda4 /mnt/zip250.0 vfat noauto,user 0 0

That should be it :cool: however, I have found that sometimes you may need to adjust permissions.

Good luck.[/QUOTE]

where is the "/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0" entered into? what file? excellent advice though.

---

### Post by BrianD18 on 2006-05-20
That was really good - clear and easy for a complete newbie. Many thanks. Tomorrow I'll try and see my USB pen drive!

---

### Post by Astinsan on 2006-05-21
[QUOTE=spartan777]where is the "/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0" entered into? what file? excellent advice though.[/QUOTE]
this would be in the /etc/fstab file. This is where you would do this on linux or bsd systems.

---

### Post by LCasler on 2006-06-12
Thanks very much, Psuedonym!

Your guide worked perfectly for my IDE zip 100, and very easy to follow for a total linux newbie like me. =)

---

### Post by kevanf1 on 2006-07-10
> **spartan777 said:**
> where is the "/dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0" entered into? what file? excellent advice though.

Suitably edited and my apologies are offered for leaving it so long to do so, please forgive this oversight [-o<

---

### Post by ssmithy on 2006-07-10
I am also trying to get my 100MB external parallel zip drive to mount, and I get the following error message:
mount: special device /dev/sda4 does not exist


Here's the thread with some of my results:
[http://www.ubuntuforums.org/showthread.php?t=212311&highlight=zip](http://www.ubuntuforums.org/showthread.php?t=212311&highlight=zip)

Anyone have any ideas?  Thanks in advance!

---

### Post by beast2k on 2006-07-21
Does anyone know of a newer version of this howto for 6.06 ? thanks

---

### Post by foxmulder on 2007-08-05
I tried this guide for Feist Fawn (7.07), but no matter what I do, Ubuntu only will mount my ZIP once and after that it's over and it keeps telling me that /dev/hdd4 is not a valid blockdirve or something.

No matter where I Google, I keep winding up with this article.

I have old hardware with an IDE/ATAPI ZIP100 and I would like to use it!

Can some 'guru' please help with this?

Btw: I tried this program called "jazip" [http://www.scripps.edu/~jsmith/jazip/]("http://www.scripps.edu/~jsmith/jazip/") but that says my IDE isn't a RAW SCSI device...

HELP!

---

### Post by jrev on 2007-09-15
I installed feisty on a computer with a zip100 internal device.

I have an icon in the "my computer" windows.

If I insert a disk into the zip drive the PC freezes stiff : no mouse, no keyboard 

I have put a line into the fstab file without any change in the fault.

---

### Post by Bert Mariën on 2007-10-20
> **ssmithy said:**
> I am also trying to get my 100MB external parallel zip drive to mount, and I get the following error message:
mount: special device /dev/sda4 does not exist


Here's the thread with some of my results:
[http://www.ubuntuforums.org/showthread.php?t=212311&highlight=zip](http://www.ubuntuforums.org/showthread.php?t=212311&highlight=zip)

Anyone have any ideas?  Thanks in advance!

Regarding the Iomega Zip Plus parallel drive, I got it working like this (I am working Gutsy):

Made a mount point 
    /media/zip

Edited 
    /etc/modules
Added  
    imm 

Ran
    $ modprobe imm

Now its the trick to find where to find your disk.

Browse 
    /dev/.udev/names

You will find a directory there, most probably named
    disk\x2fby-label\x2fIOMEGA

When you open that directory, you'll find a file that tells you where to mount your zip drive. In my case the file was 
    \x2fblock\x2fsdb\x2fsdb4
so my zip drive was at 
    sdb4

Edited 
    /etc/fstab
Added 
    /dev/sdb4 /media/zip vfat user,rw,umask=0000,codepage=850 0 0
(codepage 850 is for Belgium)

Rebooted.
Everything worked.

---

### Post by rmcollins on 2007-12-08
> **brj said:**
> for the parallel iomega zip 100 plus you have to load the module 'imm'
><

jakob

Can anyone tell me where to find the 'imm' driver(module).  The web page you are directed to from the mini-howto does not exist.

Thank you.
:confused:

---

### Post by ssmithy on 2007-12-08
It should be in the kernel already.

Have you tried to load it using the modprobe command?

```
sudo modprobe imm
```

---

### Post by towy71 on 2008-02-03
I found somewhere that there is a program called jazip, ```
sudo apt-get install jazip
```then you need to run the config program```
sudo jazipconfig
``` and then you have a nice interface to mount unmount etc

Just make sure that your zip drive is plugged in ;-)

I have just done that for a client and it does work very well ;-)

---

### Post by user11 on 2008-04-11
I have gutsy, it sees the zip 250, but all I get is 
"mount: /dev/hdb4 is not a valid block device" when I try to use it.
none of the scripts above work. 
I have this device mounted as a primary slave with a CD ROM master.
It would be a shame is Ubuntu wasn't advanced enough to recognize a device that has been out since the mid 90's. I am really trying to pitch Ubuntu to some organizations that are starting to like Linux (or distaste Microsoft for that matter).

---

### Post by ets2006 on 2008-10-30
zip mounted ok first time and now it wont mount again! help?

---

### Post by Bert Mariën on 2008-10-30
> **ets2006 said:**
> zip mounted ok first time and now it wont mount again! help?

It would be handy if you told the forum users which kind of zip drive you have. There are several models, you know.

---

### Post by johnnyhop on 2010-09-18
My legacy Iomega zip100 was doing fine in Hardy--Kubuntu using some of the info in the tutorial provided by pseudonym.  Then Intrepid came along and the zip drive failed to work until jazip was installed.  All was well through Karmic but since Lucid nothing I do produces any results.  Also won't boot if a disk is in the drive while booting.  In /dev sdc exists but sdc4 doesn't.  BTW sdd1, sdd2 and sdd4 is a hard drive with 3 partitions controlled by a PCI IDE controller.  The zip drive is IDE secondary master, DVD is the slave.:confused:

---

### Post by lkraemer on 2010-09-19
Your tutorial looks wonderful, and I want to try it on my drive.

Your Guide states, "Look in System>System Administration>Device Manager",
but in Ubuntu 10.04 there is no Menu like this existing.  Where do I
find this information?  I've even tried EDIT MENUS to see if it can be
selected.  So far I haven't located the information.

Thanks.

lk

---

