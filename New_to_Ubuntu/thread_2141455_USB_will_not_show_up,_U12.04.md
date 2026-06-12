---
title: "USB will not show up, U12.04"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by FarmersDaughter on 2013-05-02
My USB pens won't show up. Not sure why. Acer Aspire One laptop. Can provide terminal output.

---

### Post by Bashing-om on 2013-05-02
FarmersDaughter; Hi ! Welcome to the forum .

"My USB pens won't show up" ; You mean the file manager does not pick up those devices ?

To see if the system recognizes them; terminal code
```
lsusb
```
Then plug in a USB pen drive and run the command again. Is there a difference?

Safely remove the pen drive ( have the pen drives been used in Windows, and not properly unmounted ?) and
Plug in another drive. Run that terminal command again for each drive.(safely remove the drive each time)

This as a good place to start for troubleshhoting, additional advise follows when we know what there is to work too.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by FarmersDaughter on 2013-05-02
Okay
Without anything
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b19d Chicony Electronics Co., Ltd 

```Plug 1
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b19d Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8644:800b  

```Plug 2
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b19d Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 8644:800b 

```

Plug 3
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b19d Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 8644:800b 

```

So, yes, I did mean that I can't see the pen drives when I insert them. I've never used this pen drive on a Windows. The laptop also has an SD card reader, that doesn't work either.

---

### Post by Bashing-om on 2013-05-02
FarmersDaughter;

Well appears they are recognized by the system. Let's go a bit higher up and see if they are mounting.
With a device plugged in; terminal codes:
```
sudo fdisk -l 
ls -la /media
mount
```
Oh, and are you plugging the pen drives in through a usb hub device ?[INDENT]
so a tale is told

[/INDENT]

---

### Post by FarmersDaughter on 2013-05-03
Output:
```
***@TinyPenguin:~$ sudo fdisk -l
[sudo] password for ***:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2038


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   310505471   155251712   83  Linux
/dev/sda2       310507518   312580095     1036289    5  Extended
/dev/sda5       310507520   312580095     1036288   82  Linux swap / Solaris


Disk /dev/sdb: 504 MB, 504365056 bytes
5 heads, 20 sectors/track, 9850 cylinders, total 985088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6d0a80f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32      985087      492528    6  FAT16
***@TinyPenguin:~$ ls -la /media
total 8
drwxr-xr-x  2 root root 4096 Apr  9 21:38 .
drwxr-xr-x 23 root root 4096 May  2 10:46 ..
***@TinyPenguin:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ursina/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ursina)

```

Just plugged straight in. Still nothing

---

### Post by matt_symes on 2013-05-03
Hi

Try giving the stick a label.

Kind regards

---

### Post by FarmersDaughter on 2013-05-03
> **matt_symes said:**
> Hi

Try giving the stick a label.

Kind regards

Thanks, how do I do that? Or is the stick showing up in a media folder somewhere? Sorry, new, I figured it would show up on the side near "File System" on the file manager.

---

### Post by AndyOpie150 on 2013-05-03
Try using Gparted to give the USB drive a label. Once you open it up and login go to the tab with the partition name in the upper right hand corner. Click on it and select the USB device labeled sdc1 or sdb1, etc.
Click on it again in the list. Then go to the top of the app and select the format option. Scroll down to the label option. Name it whatever you want.

---

### Post by Bashing-om on 2013-05-03
FarmersDaughter; Hey --

Not really making sense to me at this time; "fdisk" sees the pen drive --504 MB (???)-- is that drive that small ??
Why format set to FAT 16 ?

And even though "fdisk" sees the disk, not picked up in the media directory, nor is it mounting as per the "mount" command.

Configuration: System Settings -> Details -> Removable Media : What is set for the check box "Never prompt or start programs on media insertion" ?

@ the Guys;
Recon we ought to try and mount a pen drive manually and see what results ??[INDENT=2]
process of learning

[/INDENT]

---

### Post by FarmersDaughter on 2013-05-03
> **Bashing-om said:**
> FarmersDaughter; Hey --

Not really making sense to me at this time; "fdisk" sees the pen drive --504 MB (???)-- is that drive that small ??
Why format set to FAT 16 ?

And even though "fdisk" sees the disk, not picked up in the media directory, nor is it mounting as per the "mount" command.

Configuration: System Settings -> Details -> Removable Media : What is set for the check box "Never prompt or start programs on media insertion" ?

@ the Guys;
Recon we ought to try and mount a pen drive manually and see what results ??[INDENT=2]
process of learning

[/INDENT]


Yes, it is 504MB. I have no idea about the FAT16. No, that box is not checked.

I can try Gparted later today but its a pen drive I've been given for work. My desktop (Mac) can't do anything more than word-process (old and I work for a newspaper). I'm supposed to use the pen drive to open files that my boss hands me. My Windows laptop died last week so I'm left with this Ubuntu netbook. I like it for the most part, its been fairly easy to set up. This is the only part that is causing me trouble.

---

### Post by Bashing-om on 2013-05-03
Well, Should mount ... not mounting to me remains a mystery. As this is work related, accessing the data on those disk I assume is a high priority !( be nice if/when your employer is impressed with ubuntu ) The ubuntu documentation team provides documentation on maybe why it is not mounting and the instructions on how to manually mount the devices:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Have a read and we all will discuss this further //best I recall the d-conf editor will have to be installed, if you choose to go this route. [INDENT=2]
try'n to help

[/INDENT]

---

### Post by FarmersDaughter on 2013-05-03
I'll read that and try.

He's alright with it so far. He loves his Macs. He did like this better than the Windows I had, that was a major security concern for him.

---

### Post by Bashing-om on 2013-05-03
FarmersDaughter;

Good deal, If the docs do not guide you to solution, or any questions in that regard, post back.

We are here to get ya over the hurdles !

---

### Post by FarmersDaughter on 2013-05-04
Thank you!

Okay, so I checked that page, I didn't have ```
dconf-editor
```
I installed it as directed and got the follow error message when running the above again.
```
** (dconf-editor:11458): WARNING **: dconf-schema.vala:401: Unknown tag <comment>


** (dconf-editor:11458): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:11458): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:11458): WARNING **: dconf-schema.vala:401: Unknown tag <comment>

```
And at manual mounting I got this:
```
@TinyPenguin:~$ sudo fdisk -l


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2038


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   310505471   155251712   83  Linux
/dev/sda2       310507518   312580095     1036289    5  Extended
/dev/sda5       310507520   312580095     1036288   82  Linux swap / Solaris


Disk /dev/sdb: 504 MB, 504365056 bytes
5 heads, 20 sectors/track, 9850 cylinders, total 985088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6d0a80f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32      985087      492528    6  FAT16
@TinyPenguin:~$ sudo mkdir /media/externalCOOP
@TinyPenguin:~$ sudo mount -t vfat /dev/sdb /media/externalCOOP -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
what did I do wrong?

---

### Post by Bashing-om on 2013-05-04
FarmersDaughter;
on dconf-editor: I do not have it installed so presently can not advise much (if needed I will install it and have a looksee) did you install from command line "apt-get install dconf-tools" ??

For manually mounting a usb device, continue reading the documentation in "manually mounting" section. You take the info provided from the "fdisk" command (for this one instance of the pen drive has been identified as sdb1 and formatted to fat 16 - this "sdb1" is not a permanent assignment and is possible that it could change, run the "fdisk" command each time you want to manually mount a usb device.

Ok now follow the instructions and make a "mount point" (attaches another file system to ubuntu) like so:Terminal code:
```
sudo mkdir /media/pendrive1
```My example for a name is pendrive1 the documentation uses "external"
Now you may mount that device to access the files on it //as pendrive1 is formatted as fat 16 do Terminal code:
```
sudo mount -t vfat /dev/sdb1 /media/pendrive1 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```copy and paste this code sequence to preclude errors in transmission.

You should now have access to pendrive1: Terminal code:
```
ls -la /media/pendrive1
``` to list the contents of that file system.
To go deeper into any directories:
```
ls -la /media/pendrive1/<A-directory-name>
```

When you are done with that device REMEMBER to UN-MOUNT that device, failure to do so will result in file corruption at some level maybe small or maybe very destructive. UNmount the device !!!
```
sudo umount /media/pendrive1
```

** At this point one should also be able to use the GUI file Manager to access the files **

Label the physical pendrive it's self as pendrive1, each time you mount a different pendrive make another mount point for it- and label the physical device accordingly--:
```
sudo mkdir /media/pendrive2
``` and 3 and 4 and so on, make sure that each pen drive is formatted as FAT 16 and use the mount command as above substituting the correct label (as in pendrive3 vice 1) and the identifier remains as sdb1; NTFS format will require a different mount command. EXT4 yet another.
To mount the SD card follow the same procedure.


This seems like a lot just to mount a drive, really once you have done it a few times, only takes a few seconds to Get-er-Done !
Nothing much to it.[INDENT=2]
am I helping ?

[/INDENT]

---

### Post by matt_symes on 2013-05-05
Hi

Mix and match the instructions from bashing-om's post and this post. The main thing i want to point out in this post is that...

...the vfat mount option is for FAT32 (IIRC).

You are using FAT16, so try the msdos filesystem type instead if the vfat option does not work - it's been an very long time since i have even had to think about FAT16 :)

```
sudo mkdir /media/externalCOOP
```

You may have already create the directory above so ignore the error if you have.

```
sudo mount -t **msdos** /dev/sdb1 /media/externalCOOP
```

You need to specify a partition as that is where the filesystem resides. In the case above sda**1**.

Verify it's mounted.

```
mount
```

Once that is done then unmount it.

```
sudo umount /media/externalCOOP
```

That will prove it's manually mountable.

After that we can look for a workaround if it will not automount a FAT16 pen drive.

Kind regards

---

### Post by MrSteve on 2013-05-05
FAT16 formatted drives will not auto mount
the minimum is FAT32 for auto mount ...

---

### Post by Bashing-om on 2013-05-05
@  		MrSteve; Thanks for the input on FAT16 auto mounting, a cause of much concern on my part trying to understand why those pen drives were not automounting ![INDENT]
what I do not know fills up a larger book than that of what I do know

[/INDENT]

---

### Post by Bashing-om on 2013-05-07
@ FarmersDaughter;

Just checking in to inquire of your present status.[INDENT=2]
regards

[/INDENT]

---

### Post by squakie on 2013-05-07
It may help when this is all sorted out to create a udev rule to get this mounted each time automatically.

---

