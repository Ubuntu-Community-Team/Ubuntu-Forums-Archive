---
title: "Accessing windows' files"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by prismriver on 2012-02-23
I'm running Ubuntu off a livecd and I'm trying to access my Windows files. How do I mount my hard drive? It was already mounted last time I used the livecd, but it's not showing up this time. Thanks in advance.

EDIT: Still unresolved. Basically the full situation is that my hard drive's superblock needs to be fixed before it can be mounted. I need help finding the name of the partition so I can follow through a fix for the superblock linked in the thread. (Did I word that right? Please correct me if I stated that incorrectly.)

EDIT 2: Almost there. I can access my hard drive in Ubuntu, but still can't boot windows.

---

### Post by raja.genupula on 2012-02-23
try again with  restarting your PC , some times i have also got strange issues like that . but we can do mounting manually from terminal 

```
sudo mount /dev/sda1 /media
```

where sda1 is your Windows sda , so in that place assume your windows SDA and you can mount your windows partition . 

if anything comes up , please let us know . all the best .

---

### Post by prismriver on 2012-02-23
Alright, thanks. I'll restart and let you know if anything changes.

---

### Post by prismriver on 2012-02-23
Sorry, that restart took a while and it didn't change anything. Typing that line into the terminal returned "mount: /dev/sda1: can't read superblock"

---

### Post by muteXe on 2012-02-23
Morning. Any use?
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments)

---

### Post by prismriver on 2012-02-23
> **muteXe said:**
> Morning. Any use?
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments)
Uh, Sorry. I'm not sure what any of that means. I'm new to Linux obviously. What exactly does that do? Can you explain please?

---

### Post by raja.genupula on 2012-02-23
> **prismriver said:**
> Uh, Sorry. I'm not sure what any of that means. I'm new to Linux obviously. What exactly does that do? Can you explain please?
  thats means we have some errors errors in the hard disk partitions . 
[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)

that will help you to understand  superblock

---

### Post by prismriver on 2012-02-23
If I understand correctly, the superblock contains information about my hard drive that is needed to access it properly. For whatever reason, it can't read it and I need to recover it. So I just need to follow the steps on [www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/") except replace sda2 with sda1, right? Then I'll be all set, right?

---

### Post by raja.genupula on 2012-02-23
yes , you're right . In the example case it is sda2 and for your case it is sda1 . 

All the best and if anything comes up , let us know .

---

### Post by prismriver on 2012-02-23
Actually, before I go ahead, how exactly am I sure that my hard drive is sda1? How could I tell if it goes by a different name? Sorry, I know I'm pretty stupid when it comes to Ubuntu.

---

### Post by sadaruwan12 on 2012-02-23
You can use this command.

```
& sudo fdisk -l
```

This'll list all the partitions and the drive letters along side from this you can get the needed information.

---

### Post by prismriver on 2012-02-23
Uh, that returns with:

```
bash: syntax error near unexpected token `&'
```Are you sure?

---

### Post by Mark Phelps on 2012-02-23
Instead, do "sudo fdisk -lu" (lowercase L, not a one).

---

### Post by prismriver on 2012-02-23
That didn't seem to do anything either. Am I missing something?

---

### Post by raja.genupula on 2012-02-23
could you please provide us the terminal code , how you have entered ? 

Thank you .

EDIT: [http://www.basicconfig.com/linux/linux_fdisk_command_check_hard_disk_partitions](http://www.basicconfig.com/linux/linux_fdisk_command_check_hard_disk_partitions)

that will helps you .

---

### Post by prismriver on 2012-02-23
What I meant was that
```
& sudo fdisk -l
```or
```
sudo fdisk -lu
```didn't help me check if my hard drive was sda1 or not. Are they not working because I'm using a livecd or something?

EDIT: I did a little bit of digging on google, and I found the command[FONT=monospace] [/FONT]"sudo lshw -C disk" and it gave me this. Is it relevant? If so, what does it mean and where do I go from here?
```
*-disk                  
       description: SCSI Disk
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       size: 698GiB (750GB)
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-H653N
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 0409
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          capabilities: partitioned partitioned:dos
          configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=40004468 state=mounted
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sde
```

---

### Post by prismriver on 2012-02-23
Come on, I could really use some help here. I'm terribly new to this and I'd appreciate if the solution was spelled out for me.

---

### Post by Mark Phelps on 2012-02-23
Your hard drive is NOT "/sda1" -- or anything like that.

Driver letters are assigned such that your "first" drive is "sda", your second "sdb" ... and so on.

The first PARTITION in your "sda" drive, is "sda1", the second "sda2", and so on.

Microsoft confuses the sitation in their OS's by referring to "partitions" as "drives" -- but we try to keep them separate, here.

The "sudo" command is a well-know and well-documented command that has been used for a long time.  So, if you are running it from a LiveCD and the result does not show any hard drives, that implies that the BIOS can not see the drive, either.  Linux can not see a drive that the BIOS can not see.

To confirm that your BIOS sees the drive, boot into your PC and press the key needed to enter the BIOS.  This can be "End", F1, F2, or any number of other keys.

---

### Post by prismriver on 2012-02-23
To me it looks like it the BIOS does see it in the last command I entered.[FONT=monospace]
[/FONT]```
*-disk
       description: SCSI Disk 
       physical id: 0 
       bus info: scsi@0:0.0.0        
       logical name: /dev/sda 
       size: 698GiB (750GB)
```So I would assume I can follow the steps on this page using the logical name instead of their example? [http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by prismriver on 2012-02-23
I don't want to go to the next step until someone can confirm that I'm doing the right thing. Would I be using /dev/sda or not?

---

### Post by presence1960 on 2012-02-23
> **prismriver said:**
> I don't want to go to the next step until someone can confirm that I'm doing the right thing. Would I be using /dev/sda or not?

The command from terminal in Live CD should work. You should get output like below. Copy & paste the command from here ```
sudo fdisk -l

```
Here is the result of my command sudo fdisk -l:

```
raz@raz-TA790GXE ~ $ sudo fdisk -l
[sudo] password for raz: 

[COLOR="DarkRed"]Disk /dev/sda: 250.1 GB, 250059350016 bytes[/COLOR]
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7408b4a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             124   140343295    70171586    5  Extended
/dev/sda2       260044155   281008979    10482412+   b  W95 FAT32
/dev/sda3       281008980   301973804    10482412+   7  HPFS/NTFS/exFAT
[COLOR="DarkRed"]/dev/sda4   *   301973805   488392064    93209130    7  HPFS/NTFS/exFAT[/COLOR]
/dev/sda5             126    65978954    32989414+  83  Linux
/dev/sda6        65979018    74364884     4192933+  82  Linux swap / Solaris
/dev/sda7        74366976   140343295    32988160   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05f07bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976768064   488383008+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832    7  HPFS/NTFS/exFAT

Disk /dev/sdh: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052075

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *        2048     3147775     1572864    b  W95 FAT32
/dev/sdh2         3147776   160086015    78469120    7  HPFS/NTFS/exFAT
```

AS you can see in red: sda is my first hard disk which has quite a few partitions on it. Windows7 is sda4. Ubuntu 11.10 is sda7 and Linux mint 12 is sda5. 

The sda describes the physical hard disk and sda1, sda2, sda3, etc describes partitions on the sda disk.

Hope that helps a little bit!

---

### Post by prismriver on 2012-02-23
When I tried that, I got this.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2271cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdf5           16128   976768064   488375968+   7  HPFS/NTFS/exFAT

Disk /dev/sdg: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73696d20

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   ?  1919230059  6204919772  2142844857    a  OS/2 Boot Manager
/dev/sdg2   ?   544829025  1089655755   272413365+  65  Novell Netware 386
/dev/sdg3   ?   168653938   168653938           0   65  Novell Netware 386
/dev/sdg4      2885681152  2885734080       26464+   0  Empty

Partition table entries are not in disk order

```
Crap. That is actually my external hard drive I'm trying to transfer files to. My external is 500gb and my internal I'm trying to reach is 750gb. It automatically detects the external one with no trouble. I safely removed it and tried again, which obviously returned me with nothing. How am I supposed to reach my files? And how am I supposed to fix the superblock if I don't even know what to refer to the drive as? Please, I really need help here.

---

### Post by presence1960 on 2012-02-23
> **prismriver said:**
> When I tried that, I got this.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2271cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdf5           16128   976768064   488375968+   7  HPFS/NTFS/exFAT

Disk /dev/sdg: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73696d20

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   ?  1919230059  6204919772  2142844857    a  OS/2 Boot Manager
/dev/sdg2   ?   544829025  1089655755   272413365+  65  Novell Netware 386
/dev/sdg3   ?   168653938   168653938           0   65  Novell Netware 386
/dev/sdg4      2885681152  2885734080       26464+   0  Empty

Partition table entries are not in disk order

```
Crap. That is actually my external hard drive I'm trying to transfer files to. My external is 500gb and my internal I'm trying to reach is 750gb. It automatically detects the external one with no trouble. I safely removed it and tried again, which obviously returned me with nothing. How am I supposed to reach my files? And how am I supposed to fix the superblock if I don't even know what to refer to the drive as? Please, I really need help here.

Your internal is not being recognized. Do you have any idea of how it was partitioned? Most users will have windows as the first partition on their disk, which in your case would be sda1. Unless you have a recovery partition, dell utility partition or a windows 7 System reserved partition. In my case windows is sda4. There goes the myth that windows has to be the first partition on a disk.

---

### Post by prismriver on 2012-02-23
I would have no idea. I've only used windows 64 bit vista on this computer until a couple days ago where I've been using a livecd if that makes any difference. Speccy says my hard drive is a "733gb Seagate ST375063 0AS SCSI Disk Device (SCSI)". Would that help in any way? I'm starting to get worried here.

---

### Post by presence1960 on 2012-02-23
If you can remember how your internal disk was partitioned you can run the command from the Live CD. If windows was the first partition it was sda1. I am not in favor of running terminal commands from guess work as you can do more harm than good.

Take a breather then try to remember how your disk was set up. Some points to consider:

Make & model of your machine- did it come with a recovery partition? If a dell it may have a dell utility partition. Did you install windows from a windows retail CD/DVD? If Windows 7 from a retail DVD did you install windows prior to linux? If so your sda1 is most likely a System Reserved partition and windows 7 is most likely sda2.

Like I said take a breather. Sometimes it is best to get away from something that is driving you crazy, relax a little, then come back to it.

---

### Post by presence1960 on 2012-02-23
> **prismriver said:**
> I would have no idea. I've only used windows 64 bit vista on this computer until a couple days ago where I've been using a livecd if that makes any difference. Speccy says my hard drive is a "733gb Seagate ST375063 0AS SCSI Disk Device (SCSI)". Would that help in any way? I'm starting to get worried here.

Did you install from a retail/oem DVD?

---

### Post by presence1960 on 2012-02-23
I had to go digging for this. I remembered the command, but couldn't remember how to get to a command propmpt from the Vista DVD.

Assuming you installed Vista from a DVD of course try this:

Boot from the Vista DVD and go the command prompt.

(If you have problems getting to the command prompt:
At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press "Shift F10".)

Type

 diskpart

and then at the 'diskpart' prompt:

 list volume

This will list the drive letters for all the 'NTFS' and 'Fat' partitions on your computer. Determine the drive letter for your Vista partition.
Type


 exit

to exit the "diskpart" prompt.


Type


chkdsk C: /r

but replace "C:" by the drive letter of your Vista partition.


Run chkdsk several times, until no more errors are detected.

Then reboot without the Vista DVD and see if your filesystem is fixed.

This may be a longshot. I would try this before blindly issuing terminal commands from Linux Live CD

---

### Post by presence1960 on 2012-02-23
You mentioned your hard disk is a Seagate. You can try [this]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatooldreg&vgnextoid=480bd20cacdec010VgnVCM100000dd04090aRCRD"). You will of course have to burn the image to a CD and boot from the CD. Used it to repair bad sectors on a seagate of mine without losing any data.

Sorry if I am shooting multiple things your way, but I know how it feels to not have a working back up plan in place and facing the prospect of losing files. I learned from bitter experience to never, ever not have a back up.

---

### Post by presence1960 on 2012-02-23
gotta put my daughter to bed, it's a school night. Will check back later.

---

### Post by prismriver on 2012-02-23
Well, I when I tried to check for a reply, I noticed that my external hard drive was making a funny noise. I tried to safely remove it and this happened.

[http://imgur.com/ZFfPF](http://imgur.com/ZFfPF)

Is this bad? It looks bad. Am I f'd?

I should have been more forward with my situation. I cannot boot windows at all, it would just be loading indefinitely. There were no system restore dates, I couldn't boot in safe mode, and some other stuff didn't work. 

So I was going to use an Ubuntu livecd to back up my files to an external hard drive and completely restore my computer. Then I run into all this trouble of it not detecting the hard drive and such. I'll try your suggestions after I get this panic thing sorted out. Thanks.

Should I do a hard reset or is there something I can do about it?

---

### Post by prismriver on 2012-02-24
Please, I can't do anything on my computer unless I get some help. I don't know what to do...

---

### Post by Mark Phelps on 2012-02-24
I asked a while back if the BIOS sees the drive, and said you needed to boot into the BIOS screens to find out.  Instead, you ran a command in a terminal. You need to do what I suggested first -- BOOT into the BIOS screens and tell us what they show.

I suspect the BIOS does see the drive, so I'm somewhat at a loss as to why "fdisk" does not.

If you try to boot again into Win7 and can get even part way into it, you could try following the steps in the Boot-Repair link below to see if you can repair the Win7 boot loader:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

If that doesn't work, and you can still use your external drive, and there is enough room on there for a copy of your Win7 partition, then you should download and burn the FREE Partition Wizard Boot CD (Windows app), boot from that, connect your external drive, and copy the Win7 partition to the drive.  That will at least allow you to save your files and data from Win7 -- in case you have to do a full restore to get it back.

If you end up simply not being able to restore boot to Win7, and since you don't have a backup, you should check your hard drive to see if you have a Recovery partition.  If you do, you could then restore your original Win7 setup -- and recover your data and files from the copy you made of the Win7 partition on your external drive.

---

### Post by prismriver on 2012-02-24
Ok, I slept and got my head cleared. Hopefully I can help better. Though I'm sure it doesn't help at this point, my computer is a HP Pavilion media center m8530f. [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3740333](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=3740333)

It came with 64-bit vista already on it, not windows7, so I don't have any dvds relevant to that. If I need to burn one using a different computer, I'll need a link to it. 

I booted into BIOS screen and I did not see anything relevant to my hard drive. I tried the seagate disc and it could not find my hard drive. How do I go about recognizing it and making it work? What about the superblock thing from earlier? Would that change if it sees it or was that just for Ubuntu?

I do not remember anything about a recovery partition nor do I know how  it is partitioned. I think there was a C and a D drive in windows. Would that be the partitions or is that irrelevant? C was significantly larger than D. So should I assume that the files I'm trying to reach on C is sda1?

Is the boot repair tool something that I would run through Ubuntu or just when booting? My computer only has one cd drive and I can't run Ubuntu off the livecd and the tool at the same time. I can go buy an extra cd drive if you need me to. (EDIT: I think I misread how it works. If it's already included with Ubuntu, I can just type sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair into the terminal, right?)

Does the partition wizard allow me to specifically select which files I'd want to transfer? The amount of space I have on my external hard drive isn't big enough for the whole thing, but it has room for everything that I'd want to keep. Also, does it work with vista?

---

### Post by presence1960 on 2012-02-24
Got home from work and did a little research. I found that if your boot sector is damaged you will not be able to boot nor access any files. When you attempt to mount the disk from Linux you may get a bad superblock message if your boot sector is corrupted.

A terminal program called testdisk may be able to repair your boot sector. Don't panic about terminal as I have fired up testdisk on my machine and have taken screenshots for you to follow.

First you need to boot from the Ubuntu live Cd/USB. Once you get to the desktop open a terminal and run this command ```
sudo apt-get install testdisk
```

This will install testdisk to the Live CD/USB session. Once testdisk is installed run this command from terminal ```
sudo testdisk
```

Refer to Screenshot-1: select no log. Hit Enter key.

Refer to Screenshot-2: This is the moment of truth-hopefully your internal disk is recognised here or you will not be able to proceed. If it is recognised highlight it (my disk w/Windows is sda) and make sure Proceed is highlighted at bottom. Hit Enter key.

Refer to Screenshot-3: select Intel and hit Enter key

Refer to Screenshot-4: Select Advanced and hit Enter key

Refer to Screenshot-5: Select your windows partition. Based on your model HP it will be the biggest partition (mine is sda4). At bottom select Boot and hit Enter

Refer to Screenshot-6: Select Rebuild BS & hit Enter key.

When it is complete you can quit testdisk and reboot your machine without the Live CD/USB. If the cause of the bad superblock message was a corrupted boot sector you should be good to go. If not the problem may be something else. Good Luck!

P.S. Screenshot-6 is below as there is a limit of 5 attachments per post.

---

### Post by presence1960 on 2012-02-24
Here is #6

---

### Post by prismriver on 2012-02-24
Hm. Nothing happens. I can't open testdisk. Here's the log.
```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

```
What now?

---

### Post by presence1960 on 2012-02-24
> **prismriver said:**
> Hm. Nothing happens. I can't open testdisk. Here's the log.
```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

```
What now?

From the desktop go to Software Sources by clicking the top icon called dash home on the unity panel. Choose software sources. Make sure the universe repository is checked (see screenshot) Close software sources window. Open terminal and run ```
sudo apt-get update
```

When that is done install testdisk by running ```
sudo apt-get install testdisk
```

Then follow instructions posted earlier.

---

### Post by presence1960 on 2012-02-24
After doing Rebuild BS if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write"

---

### Post by prismriver on 2012-02-24
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sr0 - 731 MB / 697 MiB (RO) - TSSTcorp CDDVDW TS-H653N









[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.


```Nononononono. It didn't pick it up. Now what? It did mention that some files weren't updated or changed when testdisk installed. Could it have installed improperly? If not, is my hard drive just disconnected for some reason? How do I check if it's even in right? It was working the day before I started the thread and was even automatically detected.

---

### Post by presence1960 on 2012-02-24
> **prismriver said:**
> ```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sr0 - 731 MB / 697 MiB (RO) - TSSTcorp CDDVDW TS-H653N









[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.


```Nononononono. It didn't pick it up. Now what? It did mention that some files weren't updated or changed when testdisk installed. Could it have installed improperly? If not, is my hard drive just disconnected for some reason? How do I check if it's even in right? It was working the day before I started the thread and was even automatically detected.

If it isn't detecting your disk, did you try what Mark asked and check your BIOS? I also would open the case and check to make sure power cables and data cables are seated properly on the disk, motherboard and power supply. It is strange that your disk isn't detected in any way.

---

### Post by prismriver on 2012-02-24
I did check the BIOS, and I saw nothing that looked remotely related to my hard drive. I'll take a look inside, do you have any tips for me other than to not be reckless?

---

### Post by presence1960 on 2012-02-24
> **prismriver said:**
> I did check the BIOS, and I saw nothing that looked remotely related to my hard drive. I'll take a look inside, do you have any tips for me other than to not be reckless?

Use an anti-static wrist strap. If you do not you risk electrostatic discharge which can fry your components. The hard disk should have 2 cables connected to it. A power cable coming from your power supply. Depending on the type of disk you have, for a power connection you will have a 4 pin molex connector for an IDE hard disk or A Sata connector for a Sata disk. For the data cable for an IDE disk you will have the ribbon type connectors on the disk and motherboard. The ends have about a 2 inch connector with many holes in it. If it is a Sata disk you will have a much smaller connector for the disk & motherboard.

Either way the disk will have 2 connectors in it-one from motherboard and one from power supply. Also check the connections on the motherboard and power supply to make sure they also are seated correctly.

---

### Post by prismriver on 2012-02-25
Inside I found the two cords attached to the hard drive. One went into the motherboard into a slot with sata1 printed next to the slot, and the other was the 4-pin for the power, which was slightly crooked. It didn't click or make any sort of noise like I expected, but it slid in a little bit. Now to continue where we left off. That would be entering "sudo testdisk" correct? Or am I supposed to redo one of the previous steps?

(There were a couple loose plugs on the inside hanging next to the power supply though. I didn't see anywhere to plug them in, so I left them alone. If the same problem persists, I'll go back inside and inspect it further. and take a bunch of pictures for you to look at. I wouldn't want to mess with the wrong thing. The way they're in there is hard to see, they go behind stuff and its pretty crammed in the case.)

---

### Post by presence1960 on 2012-02-25
> **prismriver said:**
> Inside I found the two cords attached to the hard drive. One went into the motherboard into a slot with sata1 printed next to the slot, and the other was the 4-pin for the power, which was slightly crooked. It didn't click or make any sort of noise like I expected, but it slid in a little bit. Now to continue where we left off. That would be entering "sudo testdisk" correct? Or am I supposed to redo one of the previous steps?

(There were a couple loose plugs on the inside hanging next to the power supply though. I didn't see anywhere to plug them in, so I left them alone. If the same problem persists, I'll go back inside and inspect it further. and take a bunch of pictures for you to look at. I wouldn't want to mess with the wrong thing. The way they're in there is hard to see, they go behind stuff and its pretty crammed in the case.)

Boot up and see if you can boot to windows. If not boot the Ubuntu Live CD/USB and go to desktop. Open a terminal and run ```
sudo fdisk -l
```
Let's see if your disk is recognized now.

P.S. Each time you boot the Live CD/USB you must make sure universe is selected in Software Sources. Then install testdisk with the command ```
sudo apt-get install testdisk
```
Then run testdisk with the command ```
sudo testdisk
```
The reason you must do all that each time you boot the Live CD/USB is that those things are only installed to the Live Session. Once you shut down the Live CD/USB changes made are lost, unless you made a USB with persistence.

---

### Post by prismriver on 2012-02-26
So I booted into Ubuntu and it automatically picked up my internal hard drive and I backed up a lot of my files! Woo! I have no idea how that cable became loose, I hadn't opened the inside for about two or three months. I sure feel stupid for something basic like this to be over looked. I can't thank everyone enough for putting up with me for the past few days.

I booted into windows, and I got past where it would get stuck before, but this time the login screen was completely non-responsive. What would sometimes happen in the past is there would be a 10 minute delay when pressing any keys here, then be fine after I login. This attempt, however, was left on for many hours and nothing responded on this screen. It wasn't the keyboard or anything stupid like that, clicking any of the buttons had no response as well.

So here I am back in Ubuntu. While my original request might *technically* be fixed, I still can't boot into windows. What steps would you recommend to fix this and in what order? There was the seagate seatools cd, boot repair, and the testdisk command. I wasn't able to use these until now.

---

### Post by prismriver on 2012-02-27
After going through testdisk, it gave me this.
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 89709 254 63 1441191087 [HP]

filesystem size           1441191087
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               90074442
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]

```
Did this do anything? I couldn't tell. Which choice am I supposed to pick? Dump, list, or quit?

After this finishes, would I need to try seagate's seatools or the boot repair to finish the job?

---

### Post by presence1960 on 2012-02-27
> **prismriver said:**
> After going through testdisk, it gave me this.
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 89709 254 63 1441191087 [HP]

filesystem size           1441191087
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               90074442
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]

```
Did this do anything? I couldn't tell. Which choice am I supposed to pick? Dump, list, or quit?

After this finishes, would I need to try seagate's seatools or the boot repair to finish the job?

This is what I would do. I do not believe booting is the problem as you do get to the windows log in screen. I would do a factory restore. I looked up your model machine and found that if you press F11 when booting you will be able to restore your machine to the way it left the factory.

First back up your data you must save onto the external hard disk. When you are sure you have backed up everything you need reboot without your external disk plugged in. Press F11 and follow the prompts to restore your system to factory configuration. Note you may have the option of restoring Windows without losing your files. If HP gave you that option then use that one. Nevertheless back up your files no matter what When completed you can move your data back. You will have to reinstall any software that did not come with the machine.

[COLOR="Red"][B]Rule #1-back up your files
Rule #2 - After backing up files to the external disk disconnect it from machine prior to doing any partitioning/OS installations/factory restore.
Rule #3 - Follow Rules #1 & #2 because we don't want to hear you lost your files!

[/B][/COLOR]

---

### Post by prismriver on 2012-02-27
Alright, I'll do that. Are you absolutely sure there is no other way though? A different solution might work faster than copying 250 gigs of files. What about the seagate tools or the boot repair program? I still haven't used them after the hard drive was recognized because I wasn't told any specifics on them.

---

### Post by presence1960 on 2012-02-27
> **prismriver said:**
> Alright, I'll do that. Are you absolutely sure there is no other way though? A different solution might work faster than copying 250 gigs of files. What about the seagate tools or the boot repair program? I still haven't used them after the hard drive was recognized because I wasn't told any specifics on them.

I am not sure if there is another way. The 2 boot sectors are identical according to testdisk, which means your boot sector is fine. I am not as versed in windows as I am in linux. Maybe hold off a little and see if anyone else has a suggestion. Nevertheless you should always have a back up plan in place and executed. Stuff happens and it sucks to lose your files!

---

### Post by audiomick on 2012-02-27
> **prismriver said:**
>  I have no idea how that cable became loose, I hadn't opened the inside for about two or three months. I sure feel stupid for something basic like this to be over looked..

Just an interjection to make you feel better. I work as a sound engineer. These days, we nearly always have a digital mixing desk. You really don't want to know how much time my colleagues and I have spent looking for a digital problem only to find that a cable somewhere wasn't plugged in. ;)

It is something that one really has to remind oneself of: look for the idiot problem first, and exclude them before you start looking for the complicated ones. 

I hope you get this sorted.

---

### Post by prismriver on 2012-02-28
Well, I'm going to wait just a bit longer until I'm going to restore windows. If anyone has any suggestions, please speak up. A less drastic and easier way would be preferred greatly.

---

### Post by presence1960 on 2012-03-03
> **prismriver said:**
> Well, I'm going to wait just a bit longer until I'm going to restore windows. If anyone has any suggestions, please speak up. A less drastic and easier way would be preferred greatly.

How did it go? It has been 4 days.

---

