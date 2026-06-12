---
title: "messed up my removable media!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by stevek123 on 2008-04-24
I've been trying to get help reading mp3 from my sandisk e260. Posted here once already and over at hardware too. I found a thread here  [http://ubuntuforums.org/showthread.php?p=4776609](http://ubuntuforums.org/showthread.php?p=4776609)
and tried it. Now I cant even see it! I get an usb error msg icon in top rt that bubbles me with 'unable to get data'. When I go to System -> Pref -> Removable Media, I get an error message 'The hald service is not currently running - enable it' and it notes Linux kernel 2.6 is necessary to enable volume mgt.   ????  How do I re-enable the hald?   and synaptic doesnt list kernel 2.6 as one of the options (a patch yes but not whole thing). Help please.

---

### Post by kilroy423 on 2008-04-24
> How do I re-enable the hald?

```
ps -e | grep hal 
```

will list if the process is running

```
sudo /etc/init.d/hal {start|stop|restart|force-reload}
```

will do one of the following things ^^

```
sudo fdisk -l
```

will list what your player is detected as

```
lsusb
```

will let you know if it is being detected at all, if its usb


Kilroy

---

### Post by stevek123 on 2008-04-24
> **kilroy423 said:**
> ```
ps -e | grep hal 
```

4617 ?        00:00:00 hald-addon-keyb
 4620 ?        00:00:00 hald-addon-keyb
 4621 ?        00:00:00 hald-addon-keyb
 4631 ?        00:00:00 hald-addon-acpi
 4683 ?        00:00:09 hald-addon-stor
 4691 ?        00:00:11 hald-addon-stor

```
sudo /etc/init.d/hal {start|stop|restart|force-reload}
```

 * Usage: /etc/init.d/hal {start|stop|restart|force-reload}
steve@ubuntudesktop:~$ sudo /etc/init.d/hal {start|stop|restart|force-reload}
 * Usage: /etc/init.d/hal {start|stop|restart|force-reload}

stop: missing job name
Try `stop --help' for more information.
bash: restart: command not found
bash: force-reload}: command not found

```
sudo fdisk -l
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      100405      247697   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(100404, 79, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(247696, 24, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       21767      271577   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21766, 48, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(271576, 60, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      241276      491086   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(241275, 3, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(491085, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      372346      372354       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(372345, 119, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(372353, 14, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         984     1983619+   6  FAT16

```
lsusb
```

Bus 002 Device 015: ID 0781:7422 SanDisk Corp. 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


Kilroy

I entered the codes in terminal and posted them below each line. Looks like a mess. What next? Uninstall hal at Synaptic and reload? (=my 1st guess)

---

### Post by stevek123 on 2008-04-24
I found part of a fix for my issue here [http://ubuntuforums.org/showthread.php?t=69419](http://ubuntuforums.org/showthread.php?t=69419)
I just did what 'bugsout' did and rebooted the system. It looks like everything is back to where I started. The funky rt corner error icon is gone, hald is back, I can open/use Sys-> Pref-> RemovableMedia, my mp3 player is recognized (microSD music there & base unit music NOT). I've no clue what happened but I think I mis-used graphical sudo (here [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) ). At least I didnt mess my configs permanently or the mp3 player either. STILL looking for a way to break past the firmware and read mp3 music on the base unit.....

---

### Post by kilroy423 on 2008-05-07
Sorry that I didn't get back sooner.  You can't access your music because of firmware blocking it?  You should be able to just mount that drive and access the music. Which goes like this.

```
sudo /etc/init.d/hal {start|stop|restart|force-reload}
```

You have to choose one of these: start, stop, restart, or force-reload.  They are not all valid options at one time.

```
Disk /dev/sdd: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000
```

Im going to guess that that is your drive, since that is 2GBs.

and from 

```
Bus 002 Device 015: ID 0781:7422 SanDisk Corp. 
```

It is definently detecting your drive.



```
mkdir music_drive
sudo mount /dev/sdd1 music_drive
cd music_drive
ls music_drive

```

This should mount that device and then ls the contents of the drive. If mount is going to be picky, you can use

```
sudo mount -t vfat /dev/sdd1 music_drive
```

Good luck and let us know how it goes

Kilroy

---

### Post by stevek123 on 2008-05-08
Hi Kilroy
Thanks for late response - better late than never ;) 

The 2G device is the added microSD card. Actually _[U]everything_[/U] works there. 
The actual Sandisk unit is a 4G device. I can read the folders on the Sandisk but ubuntu does not recog the contents of the music folder at all. As a noob to ubuntu and unfamiliar with terminal commands, I'm slow to process them....(fairly fluent in the gui tho...roll-over from windows). Anyway I'll try your commands and post what I get.
Steve

---

### Post by stevek123 on 2008-05-08
I think I missed some info with the big list I inset earlier. When the device is mounted, I get desktop icons for the sandisk and for the microdisk. The microdisk (reading fine) icon -> properties shows it as Fat16. The Sandisk shows as Sansa E200P and -> properties says it is Fat32. When I run   sudo fdisk -l   in terminal, I get this about the Sandisk...

Disk /dev/sdc: 4033 MB, 4033871872 bytes
125 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      100405      247697   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
    
/dev/sdc2   ?       21767      271577   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
    
/dev/sdc3   ?      241276      491086   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
    
/dev/sdc4   ?      372346      372354       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
    
Partition table entries are not in disk order


It looks to me like it does not see Fat32 anywhere - but does see Novell Netware 386 as a system in sdc2 partition = the firmware (I think). 
When I try 'sudo mount /dev/sdc music_device'  I receive a message

steve@ubuntudesktop:~$ sudo mount dev/sdc music_drive
[sudo] password for steve:
mount: special device dev/sdc does not exist
steve@ubuntudesktop:~$ sudo mount dev/sdc1 music_drive
mount: special device dev/sdc1 does not exist
steve@ubuntudesktop:~$ sudo mount dev/sdc2 music_drive
mount: special device dev/sdc2 does not exist

---

### Post by kilroy423 on 2008-05-08
> mount: special device dev/sdc does not exist
steve@ubuntudesktop:~$ sudo mount dev/sdc1 music_drive
mount: special device dev/sdc1 does not exist
steve@ubuntudesktop:~$ sudo mount dev/sdc2 music_drive
mount: special device dev/sdc2 does not exist

I'm almost 100% sure that you need to include the / in front of dev.
Here is the output of a test I ran on my machine.

```
dan@Laptop:~$ sudo mount /dev/sda Desktop/500/
mount: /dev/sda already mounted or Desktop/500/ busy

dan@Laptop:~$ sudo mount dev/sda Desktop/500/
mount: special device dev/sda does not exist

```

you can see that without the / it reports it not existing.  Remember that you have to make the folder that you are trying to mount to.  So if music_folder doesnt exist make sure you create it:

```
mkdir music_folder
```

FAT32 is recognizable by linux so I'm not sure what that output is that you are getting 

> but ubuntu does not recog the contents of the music folder

So you can navigate into the device and see the folders?  Or is this another device?

I did some searching and thought you might want to have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=237881](http://ubuntuforums.org/showthread.php?t=237881)

Kilroy

---

### Post by stevek123 on 2008-05-09
steve@ubuntudesktop:~$ sudo mount /dev/sdc music_device
[sudo] password for steve:
mount: mount point music_device does not exist
steve@ubuntudesktop:~$ mkdir music_device
steve@ubuntudesktop:~$ sudo mount /dev/sdc music_device
steve@ubuntudesktop:~$ ls music_device
AUDIBLE     MUSIC  RECORD        SYS_CONF.SYS  VIDEO
MTABLE.SYS  PHOTO  RES_INFO.SYS  version.sdk
steve@ubuntudesktop:~$ cd music_device
steve@ubuntudesktop:~/music_device$ ls music
steve@ubuntudesktop:~/music_device$ 

music folder still reads empty!

the / was there when I input the code. It was there the first time. Mounting is NOT the issue. Reading the contents of the folders is. Yes I can nav into the device and see the folders. Cannot see folder contents. jpgs in the photo folder or mp3s in the music folder. I believe the 4 partitions in the long list represent the 4 folders. 

Other threads I've looked at including the ones you linked to me deal with mounting and read/write issues. I dont have those problems. I'm stuck!

FWIW - I went into the desktop icon after this last mounting and poked around. It shows I'm not owner/root and dont have any permissions to rw. The attached microSD card is root with rw tho. Attaching other flash drives also show up as root with rw. Its just this player...

when I looked in dmesg in terminal is says that sdc (sansa) has unknown partition table and does not assign it a partition label (i.e. sdc1) . The microdisk is recognized as sdd and is assigned a partition label of sdd1. Ubuntu doesnt like the formatting of the Sansa- tho it is listed as vfat (fat32) when I automount.

---

### Post by kilroy423 on 2008-05-09
> Mounting is NOT the issue. Reading the contents of the folders is.

Well, you can try and list the directory as root or you can try and see if those files are hidden.

as root 
```
sudo su
cd music_folder
ls 
```

for hidden files
```
ls -lha
```

Kilroy

---

### Post by stevek123 on 2008-05-11
Rats - tried that too... still no luck. Its gets as far as the folders in the player but then sees the folders as unmountable partitions (it sees/reads the drive mounted as sdc but then does not mount the partitioned folders-> sdc1, sdc2, ...). When I look/list folder contents, they still appear as empty...

I've a friend (the guy who steered me to the ubuntu world)... I am going to try and get him to crack into this thing. He's very good at this stuff and knows several programming languages, but runs everything from the command terminal and so is little help when messing with GUI issues. If I get a solution, I'll post it here. Thanks for staying with me Kilroy...

---

