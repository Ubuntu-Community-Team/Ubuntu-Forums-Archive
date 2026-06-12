---
title: "Cannot start the system"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by karanbpathak on 2013-07-17
I have Ubuntu12.04 LTS on my computer,so as i was shutting down the system there was power failure in between  due to which the shutdown down process could not be completed,After everthing was Ok,i restarted my computer .at first the Grub came then i selected Ubuntu,after that Ubuntu with progress bar appeared on desktop as usaull but this time my operating system got stuck on that Ubuntu progress bar and it did not move on to Login Screen.So i am confused right now what do, and i want to keep reinstallion or Formatting  as my last option.Please help me to recover the system.

---

### Post by karanbpathak on 2013-07-17
please help`

---

### Post by Bashing-om on 2013-07-17
karanbpathak; Hi !

Panic not. Just proceed in a calm and orderly fashion.

Let's check/repair the file system.
I am "assuming" you have only one hard disk installed, and that ubuntu is installed onto the first partition of that disk.
If this is not the case, or you are not certain;
post the output of terminal code:
```
sudo fdisk -lu
``` to see how your disk(s) is/are laid out.
Await further advise.
If sure do:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```
#if errors: -y auto answers yes for fixes needing response 
```
sudo e2fsck -f -y -v /dev/sda1
```
see: 
```
man e2fsck
```

[INDENT][INDENT]ubuntu, it is fixable
[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-17
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102606847    51200000    7  HPFS/NTFS/exFAT
/dev/sda3       102608894   572556599   234973853    f  W95 Ext'd (LBA)
/dev/sda4       572559360   625142447    26291544   12  Compaq diagnostics
/dev/sda5       102608896   396854518   147122811+   7  HPFS/NTFS/exFAT
/dev/sda6   *   397062603   572556599    87746998+  8e  Linux LVM
/dev/sda7       396855296   397062143      103424   82  Linux swap / Solaris

Partition table entries are not in disk order



ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
/dev/sda6 is mounted.  


WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? yes

/dev/sda6: recovering journal
                                                                               
  223708 inodes used (4.08%)
     271 non-contiguous files (0.1%)
     197 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 180542/68
 1836999 blocks used (8.37%)
       0 bad blocks
       1 large file

  142145 regular files
   24194 directories
      57 character device files
      25 block device files
       0 fifos
       0 links
   57275 symbolic links (43005 fast symbolic links)
       3 sockets
--------
  223699 files

---

### Post by Bashing-om on 2013-07-17
karanbpathak;

Shesh... The direction was to use e2fsck from a live environment as in use a liveDVD.
And looking at the output of "fdisk"... did you encrypt your home directory ?

If you do not know how:
set bios to boot from dvd as 1st boot priority;
boot the liveDVD;
choose "try ubuntu"
at the desk top key combo ctl+alt+t yields a terminal.

Now, I have never ran with encrypted file systems, I do not know what would result from attempting to run "e2fsck" on such a partition.
We need to exercise patience and see what others advise in this instance.


[INDENT][INDENT]it is still fixable[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-17
[Quotes][B]
The direction was to use e2fsck from a live environment as in use a liveDVD.[/B]
set bios to boot from dvd as 1st boot priority;
boot the liveDVD;
choose "try ubuntu"
at the desk top key combo ctl+alt+t yields a terminal.
[/Quotes]
Iam already on live cd,since i can't start my system.The output which i posted were excuted on "Try Ubuntu"(means to say on Live CD) _*terminal*_
My root partition is on sda6 and i have never encrypted it.Only USB is encrypted with BitLocker

---

### Post by Bashing-om on 2013-07-17
karanbpathak; Outstanding !

Ok, I can not understand why "e2fsck" is screaming and hollering about sda6 being mounted;
The out put of "fdisk" indicates that sda6 is either part of Logical Volume Managed Group (LVM).. or that there is some type of encryption going on.
For reference, my first hard drive, no encryption, no Windows - my output:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e
   Device Boot      Start         End               Blocks   Id  System
/dev/sda1   *        2048    10242047        5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665   5  Extended
/dev/sda5       443795688   443811689         8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154  76798701   83  Linux
/dev/sda7       597409792   976771071 189680640   83  Linux
/dev/sda8        34207744    44447743      5120000   83  Linux

Partition table entries are not in disk order


We have got to determine where that LVM indicator is coming from, and why "e2fsck" says sda6 is mounted !
Can you post a screen shot of what "GParted" (liveDVD -> dash ->type GParted ->icon below, click on icon) has to indicate about the partitioning and mounting ? That will tell us a little.

[INDENT][INDENT]solutions = no problems
[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-17
Gparted ScrrenShot is below

---

### Post by Bashing-om on 2013-07-17
karanbpathak;

It is always amazing to me what I do not know, Let us suppose that as the swap partition is mounted by the file system, and that as that swap partition is within an extended partition that also contains sda6 that sda6 is also mounted when the swap partition is mounted.
Try this,
In gparted, click on the key icons and choose to unmount sda 7(swap) and sda 6 see if that unmounts the extended partition.
still in GParted see if the option to "repair broken system" will do it's magic (that option calls e2fsck). -All Hard Disk partitions must be (un-)mounted for "e2fsck" to check/repair the file system.

[INDENT][INDENT]we be try'n[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-18
My All Hardisk partition are unmounted and tried repairing with the Command 
# fsck -y /dev/sda6 

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda6: clean, 223706/5488640 files, 1837292/21936749 blocks

This was the output obtained, does this mean my files are not corrupted?
I think there may be problem in boot since as mentioned at very beginning Ubuntu freezes at progress bar
Below is just an example image of where i get error ,After booting  and before login

---

### Post by Bashing-om on 2013-07-18
karanbpathak; Morning;

fsck: Yes in this instance the file system reports no errors ( but you did not ask to see the errors ). The output does indicate all is intact with the file system.

As a rule of thumb, any time there is an interruption in power, the probability of file system corruption does exist and a file system check should be run.

We need to get you booted up. Try this:

From a cold boot, as soon as the bios screen clears, depress and hold the shift key -> grub boot menu;
Arrow down to a "recovery" entry, press enter to boot to the "recovery console" choose "resume normal boot" .
Can you now boot to a GUI ?... degraded graphics is OK at this point. 
Depending on that outcome, is what we will do next.
[INDENT][INDENT]
no step for a stepper
[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-18
Yeah i tried that step 
1.Grub is Loaded
2.I selected Recovery Console
3.and selected resume normal boot

and i cannot boot to GUI, only a blank screen appears,so i swicth off the device and again restart and same error again "Ubuntu Progress bar freezes"

---

### Post by Boab1993 on 2013-07-18
I used to have a problem like this when using my desktop computer, however im not sure if there is a fix in place now.
Basically the configuration was incompatible with my monitor, all i had to do was go into the grub menu by holding SHIFT on reboot and edit the line mentioning 'quiet_splash' to 'nomodeset'
Wondering if this could be a similar case?

Just a thought.

---

### Post by Bashing-om on 2013-07-18
We can certainly try that, maybe get some other indicators.. but choosing "recovery mode" is basically the same, "nomodeset" is set.
Not attaining to a GUI is generally a graphics related issue and is therefore the first line of attack.

[INDENT][INDENT]won't hurt to try
[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-18
I tried it,and when i edit the line mentioning 'quiet_splash' to 'nomodeset' did not work
I think i should at last reinstall Ubuntu 12.04 LTS on my system,I have few Question 
1. as i have uploaded  the image of Gparted for my system,is that partition right should i format and install new Ubuntu on same partition(/dev/sda6)
2.Today I have learned a basic things "_**precaution is better than cure**_",what precaution should i take ,if these things happen again? 
3.Normal backup of data is simple but can i take a backup of system configuration,(i.e all software installed should be recovered),example In Windows there is restore point,similar to it can i take backup of my system?

---

### Post by karanbpathak on 2013-07-18
please help

---

### Post by Bashing-om on 2013-07-18
karanbpathak; Hey;

(Re-)installing may not be a bad idea at all as the swap partition is very small... I would make the suggestion of 2 gigs for the swap partition. Ubuntu is happy to run in an extended partition as you presently have it set up, but making swap 2 gig .. will have to resize ubuntu's root partition.

Backup: Before altering your system ... always back up important data ... anything can happen !
Backing up in ubuntu: you will get as many opinions as there are users of ubuntu.
Me personally for the way I use my system, and how I have it set up... all I backup is my data files in my home directory and a few .config files. I have written scripts to do that as well and write my files back in place if required. Many suggest to backup the entire /home directory.

Bear in mind ubuntu (linux) is not Windows ! ubuntu's file system is separate from your /home directory and for the most part remains staid, such that any part or whole may be (re)installed if actually required. All system changes you are concerned with reside within that /home directory.
If this is a fresh install that you are going to (re-)install..... there is little or nothing to save.

I think it would behoove you to (re-)install with that larger swap partition. 

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by techvish81 on 2013-07-18
you can try boot repair with live dvd , here is the link for instructions:- [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

