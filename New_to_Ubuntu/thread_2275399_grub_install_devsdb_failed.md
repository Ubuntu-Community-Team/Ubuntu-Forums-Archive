---
title: "grub install /dev/sdb failed"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by Yasar_Garip on 2015-04-25
Hello all,
First i wanna say that i am so very new to Ubuntu.
I first installed it alongside windows7 and then i liked it quite a lot and tried to install it to whole disk. 
When i tried to install, i got the error grub install /dev/sdb failed at the end of the installation
some posts here (or somewhere else i don't remember) suggested that i use bootrepair in a live session so did i. 
But now it's stuck on "Reinstall grub sda this may require several minutes" for hours now
I also found other posts with other solutions but i amso new to commands and all and most commands in those did not work. I get nothing when i do "fdisk -1" for instance. Any other solution in other posts didn't work or maybe i just couldn't do it. 
I've been trying to figure this out for hours now and about to go crazy. 
Could you help me please?

---

### Post by Bashing-om on 2015-04-25
Yasar_Garip; Hello; Welcome to the forum.

We will work through this.
1st is the 'fdisk' command it is :
```

sudo fdisk -l

```
that is a lower case L.
Now that out of the way .. what is your goal ? Just to install ubuntu, and let it have the use of the entire hard drive ?
Maybe at this point ubuntu is installed and all we need to do is install grub (GRand Unified Bootloader ) ?
Post back to us the output - Between Code Tags -  of the 'fdisk' command and we see where to go from there.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]millions do it
[INDENT][INDENT][INDENT]you can too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yasar_Garip on 2015-04-26
Hello, here is the result of fdisk, and yes, i want to install ubuntu and let it use the entire disk.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2b93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482127871   241062912   83  Linux
/dev/sda2       482129918   488397165     3133624    5  Extended
/dev/sda5       482129920   488397165     3133623   82  Linux swap / Solaris

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7821311     3910640    b  W95 FAT32


```

---

### Post by Yasar_Garip on 2015-04-26
Oh and i should say that this happened after i installed ubun14.04 , then tryed 12.04  not right atfirst time i tried to install 14.04

---

### Post by dino99 on 2015-04-26
Linux is installed on sda, so you might want to install grub-pc on /dev/sda
and should also set a /home partition for your data & settings

the sbd formatting looks strange: start at 32, so not so much room there (suppose its an old xp formatting or so).

be sure that gparted does not show error(s) on these partitions (red triangle)

---

### Post by efflandt on 2015-04-26
It looks like you might be running from live/install iso on sdb and you installed Ubuntu to sda, so you should be putting grub on /dev/sda, not /dev/sdb, since sdb will not exist when your USB memory stick is not inserted. So boot from live/install iso and do:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```For more info see [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) and scroll down to 
[h=2]Fixing a Broken System[/h] [h=3]via the LiveCD terminal[/h]

---

### Post by Yasar_Garip on 2015-04-26
For the first command i get ```
wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by Bashing-om on 2015-04-26
Yasar_Garip; Morning ..

That:
> 
wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or  so


does not bode well .. however, before jumping to the conclusion that the disk needs to be wiped and ubuntu  (RE-)installed; let's do a minor check:
from that liveUSB -> try ubuntu mode -> terminal:
What results from terminal commands:
```

sudo mkdir /mnt/look
sudo mount /dev/sda1 /mnt/look
ls -al /mnt/look

```

Keep in mind it is not a big deal if a (RE-)install is in order ....

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by Yasar_Garip on 2015-04-26
Hello, re-install is no problem. I just wanna be able to install the os. I backed up everything. So please let's do that :)  the results for the codes you gave are as follows : after the second command i got ```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
again and for the third i got ```
total 0
drwxr-xr-x 2 root root 40 Apr 26 19:45 .
drwxr-xr-x 1 root root 60 Apr 26 19:45 ..
```

Again, my aim is to be able to install ubuntu. No data to save.

---

### Post by Bashing-om on 2015-04-26
Yasar_Garip; Ho-kay;

In the interest of expediency, let's just (RE-)install.
1st however, verify the install medium .
Boot the liveUSB, as soon as the bios screen clears depress the right -shift- key -> language screen; escape key to accept the default -> Boot Options Screen:
here choose " check disk for defects " .
If the test is good, we proceed.

Now I ask if you are happy to do a standard guided install ? This install is just fine for those "new users " and will serve well until you are familiar with the linux operating system. At some later point you might want to repartition and (RE-)install to better suit your use case .

If you know that you want to do "something else" please advise now, or for ever hold your peace .

It is your system ->
[INDENT][INDENT][INDENT]we will do it your way
[/INDENT][/INDENT][/INDENT]

---

### Post by Yasar_Garip on 2015-04-26
Bashing-om , thank you a lot for your help. I just want a standart guided install i can say that. I will do the "check disk for defects" now and report back here. 
But the problem is; i've been trying to install for several times nowand everytimei get the grub install error. So i figure i should do something in live session, fix something. What are you suggesting exactly? Something with codes and stuff during install? Sorry if i don't understand stuff correctly. I'mnot a native English  speaker after all. 
I will be back with the results of the "check disk for defects.

---

### Post by Bashing-om on 2015-04-26
Yasar_Garip; Hey;

My hat is off to you that you are able to communicate so effectively in English. English is the only language I use, and many times not so well.

as to getting installed .. what results with the install of the boot code is that the installer defaults to install the boot code to the 1st device it finds,,, in your case I bet it is the USB rather than the hard drive.
Once the ubuntu system is installed .. AND if need be - when confirmed the system is installed -, then we can install the boot code properly. IF it should come to that situation.
-----------------
When I fail in my attempts to communicate, please do not hesitate to ask me to rephrase or add additional info . My communications skills leave a lot to be desired, but I try to the best I can.
---------------------
[INDENT][INDENT]installation ->
[/INDENT][/INDENT]

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by Yasar_Garip on 2015-04-27
Hello, i just solved my problem. I found something called ultimate boot cd and booted parted magic with it. Since i don't know much about this stuff my approach was to absolutely wipe and delete everything and then it worked. I was able to install ubuntu from live cd. Thanks to everyone for your help, Bashing_om in particular. Have a great day!

---

### Post by Bashing-om on 2015-04-27
Yasar_Garip; Outstanding .

You do good work .. Glad you are up and running ubuntu .
Welcome to our world.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]peace be with you
[/INDENT][/INDENT]

---

