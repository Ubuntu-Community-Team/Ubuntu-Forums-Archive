---
title: "Help activating Swap partition"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by 9173 on 2014-01-19
When I was laying out my hard drive for a dual boot with Windows 7 64 bit, I created a swap partition and I just realized I have to activate t first. 

I tried following [this guide]("https://help.ubuntu.com/community/SwapFaq")  and I got kind of lost.

I got to the step 3 without a problem. Here's the info the terminal yielded.
> nick@PUTER:~$ gksu gedit /etc/fstab &
[1] 5891


The text editor brought me this:
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=9dcaf243-3947-46db-9b16-33c781759ee6 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0


A bit lost to say the least now

---

### Post by Bashing-om on 2014-01-19
9173; Hi !

Not a problem, all that is required is to edit that file and add the entry for the swap partition.
Need to get the UUID so we know what to add:
```

sudo blkid

```
And carry on from there.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by 9173 on 2014-01-21
When I run > sudo blkid I get the UUID and stuff for all the other partitions, but all that is listed for the Swap is
> /dev/sda8: TYPE="swap"


No UUID or any other info. 

After I get the UUID I add it into the document? But where in the document do I paste it? Probably a dumb question, but it isn't obvious for me. Re-uploaded document for easier viewing
[ATTACH=CONFIG]249651[/ATTACH]

In case it isn't obvious, I've only had Ubuntu for about a week now. Loving it so far though

---

### Post by Bashing-om on 2014-01-22
9173, well !

Should be something like this:
```

/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" [color=blue]TYPE="swap[/color]

```

we will find that UUID, so we are sure of what we are doing post the out put of terminal code:
```

sudo fdisk -lu

```

And welcome to the club, it is a steep learning curve, but I assure you, well worth the effort !

Kinda busy right now, but I will 

[INDENT][INDENT]be back
[/INDENT][/INDENT]

---

### Post by 9173 on 2014-01-22
sudo fdisk -lu results


[ATTACH=CONFIG]249675[/ATTACH]

Thanks for your patience

---

### Post by Dave_L on 2014-01-22
What's the output from:

```
swapon -s
```

---

### Post by Bashing-om on 2014-01-22
9173; Sit down, take deep breath;

Format is presently HPFS, that is proprietary to Windows, Linux (ubuntu) will not touch it.

There are no good ways around it except to reformat the drive(s) to some other. Now If there is valuable data, and there is no way to back up that data, I am aware that there is a risky way to convert the dynamic partitioning back to basic, But never been there never done it and I understand it is risky ( as in any partitioning operations).

Best bet is to reformat the drive(s) and re-install Windows in say GPT format. Then ubuntu can cope with it,

We did not make the situation
[INDENT][INDENT][INDENT]we just got to work with it
[/INDENT][/INDENT][/INDENT]

---

### Post by coldcritter64 on 2014-01-22
One more bit of code to check the UUID on /dev/sda8 OP.
```
sudo tune2fs -l /dev/sda8 | grep UUID
``` If that gives an output, I'd recommend edit /etc/fstab (gksu gedit /etc/fstab) and use uuid= in fstab like has been done for the root partition but for swap, removing the /dev/sda**8** _*(see edit below sda7 is the wrong partition for fstab and swap in your case)*_ bit. UUIDs are a far more flexible means of mounting.
Once the uuid is added to the /etc/fstab file use,
```
sudo mount -a
```the swap partition will now be mounted.
To use as swap,
```
sudo swapon /dev/sda8
```

If you can't find the UUID on /dev/sda8, ie no output above you will need to set one
```
sudo tune2fs -U random /dev/sda8
```This will actually set a new UUID to the partition. Find what it is for use in /etc/fstab from the first tune2fs command above.
Good luck.

@ Bashing-om, /dev/sda8 shows as linux swap / solaris in that attachement not windows, check again please. Cheers.

Edit: **your /etc/fstab points to /dev/sda7 the swap partition is /dev/sda8**, first retry editting /etc/fstab to sda8 . Might be an easy fix, but UUIDs would be better imo. cheers

---

### Post by 9173 on 2014-01-22
> **Dave_L said:**
> What's the output from:

```
swapon -s
```

Filename:/dev/sda8
Type: Partition
Size: 4229116
Used: 0
Priority: -1

---

### Post by Bashing-om on 2014-01-22
@ coldcritter64; appreciate watching my back.

I did catch that the swap partition was made, however - and I may be jumping at conclusions, that maybe ubuntu is to be installed onto another drive - but, There is no provision on the sda drive for ubuntu. As the drive is HPFS, there is no way. The current fstab references sda6 as "/", that partition is also Windows proprietary HPFS partitioned, not ext4 (or other linux schemes).

Am I missing something here, or do I have a failure to comprehend ?
> 
When I was laying out my hard drive for a dual boot with Windows 7 64 bit


I often do not know, but I can be led to understand.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by coldcritter64 on 2014-01-22
> **Bashing-om said:**
> @ coldcritter64; appreciate watching my back.

I did catch that the swap partition was made, however - and I may be jumping at conclusions, that maybe ubuntu is to be installed onto another drive - but, There is no provision on the sda drive for ubuntu. As the drive is HPFS, there is no way. The current fstab references sda6 as "/", that partition is also Windows proprietary HPFS partitioned, not ext4 (or other linux schemes).

Am I missing something here, or do I have a failure to comprehend ?


I often do not know, but I can be led to understand.[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


OP, what is on /dev/sda6 & /dev/sda7 (anything data wise ?) your gparted shows /dev/sda6 as unknown but terminal shows it as HPFS etc as Bashing-om notes, also /dev/sda7 on your gparted output shows as ext4 but once again the terminal shows HPFS (???) How did you install the system in such circumstances; **was wubi involved in any way OP ?; ubuntu on a NTFS filesystem****[B] ?; **(it is not the same as "bare metal" dual booting)[/B] and may be important to know if it is used here.

@ Bashing-om, I think this is a bit deeper than I first noted :). fdisk **isn't** noting a GPT table so sda6 sda7 and sda8 are logical partitions and as such Windows can't boot from there (the OS itself, ok for storage though). Unless they are storage volumes it seems they are being detected wrong either in terminal or gparted (they differ for the same device) or may be wrongly formatted. Interesting :-k.

---

### Post by Bashing-om on 2014-01-22
@ coldcritter64; Yeah !

My thoughts too.
I have been in contact with the OP, and have asked the OP the meet us in the thread to clarify what he is doing and what his intentions are.

Gonna hold off for additional info.

[INDENT][INDENT]ain't it just
[INDENT][INDENT][INDENT]great
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 9173 on 2014-01-24
> **coldcritter64 said:**
> OP, what is on /dev/sda6 & /dev/sda7 (anything data wise ?) your gparted shows /dev/sda6 as unknown but terminal shows it as HPFS etc as Bashing-om notes, also /dev/sda7 on your gparted output shows as ext4 but once again the terminal shows HPFS (???) How did you install the system in such circumstances; **was wubi involved in any way OP ?; ubuntu on a NTFS filesystem****[B] ?; **(it is not the same as "bare metal" dual booting)[/B] and may be important to know if it is used here.

@ Bashing-om, I think this is a bit deeper than I first noted :). fdisk **isn't** noting a GPT table so sda6 sda7 and sda8 are logical partitions and as such Windows can't boot from there (the OS itself, ok for storage though). Unless they are storage volumes it seems they are being detected wrong either in terminal or gparted (they differ for the same device) or may be wrongly formatted. Interesting :-k.


/dev/sda6 Encrypted Partition created with truecrypt
/dev/sda7 Just Ubuntu.

Wubi was not involved in anyway.
As for installation, I laid everything out with Minitool Partition Wizard (probably the issue?) and then just installed Ubuntu on the ext4 partition from a DVD.

---

### Post by Bashing-om on 2014-01-24
9173; Nope, I can't see it !

All partitions less swap are HPFS + NTFS or fat .. UHMMM.. ubuntu default install is onto a partition of file type ext4. The installer will happily find "unallocated space" and format it to ext4, but not otherwise.
Now I know nothing about encryption and such, but I do know that on a hard disk, ubuntu will not install on a windows format, and in particular will not touch the proprietary partitioning scheme HPFS.
In my very limited Windows knowledge, the only thing I see to do is back up the data, and (RE-)install Windows using a different BASIC partitioning scheme. Set up then the "unallocated space" ? or let the installer work it's magic and make the install. Then ubuntu can cope.
[INDENT][INDENT]that is
[INDENT][INDENT][INDENT]I see it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 9173 on 2014-01-26
I'll just leave it as is if it just means no swap. 

What other problems (if any) would just leaving it as is cause?

---

### Post by Bashing-om on 2014-01-26
9173; ???

We are working with conflicting information.
To this time it is "unproven" that there is an ubuntu install on that 1st hard drive (sda).
Now there is a /swap partition, and if there does exist an ubuntu install on sda, it is a minor thing to edit /etc/fstab file so the operating system picks it up.

Show us the outputs - between code tags to maintain readability - of terminal codes:
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
To remove all doubt and so we know what we are working with.

One may do with out a swap under these conditions:
The system will not be hibernated;
and
there is 8 gigs or more ram installed;
and
There is no heavy duty computing going on- intense calculations.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by 9173 on 2014-01-27
**sudo fdisk -lu**
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x854fe247

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          208845   209937419   104864287+   7  HPFS/NTFS/exFAT
Partition 2 does not start on physical sector boundary.
/dev/sda3       209940478  1250263039   520161281    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       209940480   451112959   120586240    7  HPFS/NTFS/exFAT
/dev/sda6       451115008   493035519    20960256    7  HPFS/NTFS/exFAT
/dev/sda7       493037568   555950079    31456256    7  HPFS/NTFS/exFAT
/dev/sda8       564411645  1088708984   262148670    7  HPFS/NTFS/exFAT
Partition 8 does not start on physical sector boundary.
/dev/sda9      1088710656  1141136437    26212891   83  Linux
/dev/sda10     1193582592  1246011391    26214400    7  HPFS/NTFS/exFAT
/dev/sda11     1246013440  1250263039     2124800   82  Linux swap /

```

**sudo parted -l**
```

Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      107MB   107GB  107GB   primary   ntfs
 3      107GB   640GB  533GB   extended                  lba
 5      107GB   231GB  123GB   logical   ntfs
 6      231GB   252GB  21.5GB  logical
 7      252GB   285GB  32.2GB  logical   ext4
 8      289GB   557GB  268GB   logical   ntfs
 9      557GB   584GB  26.8GB  logical   ext4
10      611GB   638GB  26.8GB  logical   ntfs
11      638GB   640GB  2176MB  logical   linux-swap(v1)


```


**sudo parted /dev/sda unit s print**

```

Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 1250263728s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        206847s      204800s      primary   ntfs            boot
 2      208845s      209937419s   209728575s   primary   ntfs
 3      209940478s   1250263039s  1040322562s  extended                  lba
 5      209940480s   451112959s   241172480s   logical   ntfs
 6      451115008s   493035519s   41920512s    logical
 7      493037568s   555950079s   62912512s    logical   ext4
 8      564411645s   1088708984s  524297340s   logical   ntfs
 9      1088710656s  1141136437s  52425782s    logical   ext4
10      1193582592s  1246011391s  52428800s    logical   ntfs
11      1246013440s  1250263039s  4249600s     logical   linux-swap(v1)

```

[B]lsblk -f

[/B]```
NAME    FSTYPE LABEL MOUNTPOINT
sda                  
&#9500;&#9472;sda1               
&#9500;&#9472;sda2               
&#9500;&#9472;sda3               
&#9500;&#9472;sda5               
&#9500;&#9472;sda6               
&#9500;&#9472;sda7               /
&#9500;&#9472;sda8               
&#9500;&#9472;sda9               
&#9500;&#9472;sda10              
&#9492;&#9472;sda11              
sr0   
```


Thanks for sticking with a complete noob.

---

### Post by Bashing-om on 2014-01-27
9173; Hey ...
Looking good, now we KNOW !

Ok what is currently .
ubuntu IS installed to the 1st hard drive (sda) in partition #9 (sad9);
ubuntu's swap partition is installed to that 1st hard drive as partition #11 (sda11);
Sidenote - file id 7 we can deal with !

so you want to boot with 'swap' automounted at boot.

Let's get the updated info:
```

sudo blkid
cat /etc/fstab

```
and I will provide you the edits to the /etc/fstab file to make it happen.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

