---
title: "New drive does not &quot;belong&quot; to me"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-12
Ok, I was following a series of posts, trying to teach my self things Linux.
I messed up several items, and will be posting separately.

General Information:
Ubuntu 8.04.1
Kubuntu meta-package installed under Synaptic

Specific information:

Running Kubuntu:

I purchased a new hard drive (750gb SATA)

installed it, and booted PartedMagic LiveCD, 
and used GParted to created and format one massive ext3 partition
(yeah, not the best idea)

Rebooted to my Windows (because I am still hazy on copying files under Kubuntu), copied a bunch of folders/files.

Rebooted under Kubuntu, and I get an error similar to this:
[COLOR="Red"]
System Policies prohibit mounting internal media[/COLOR]

I'm going from memory here, so it may be slight;ly different.


where are these POLICIES and can I change them?
Or how do I "fix" this problem?

---

### Post by Pro-reason on 2008-09-12
I've never come across this before, but I presume that what it's telling you is that only external media can be automounted.  Internal media must be listed in your filesystem table (/etc/fstab).

Please post the output of:

```

cat /etc/fstab
sudo fdisk -l
sudo blkid

```

---

### Post by Rolcol on 2008-09-12
This sounds to me like it's a problem with filesystem permissions.  The current solution I can think of would be to mount it from the command line and recursively set the owner to your user.

---

### Post by egalvan on 2008-09-12
> **Pro-reason said:**
> I presume that what it's telling you is that only external media can be automounted.  Internal media must be listed in your filesystem table (/etc/fstab).

Please post the output of:

```

cat /etc/fstab
sudo fdisk -l
sudo blkid

```

Remember that this new internal drive was created on "another system",
a liveCD that I used to partition and format the drive, and XP used to copy files.
(I prefer the way PartED Magic LiveCD works over the other LiveCD's out there. It has the latest GParted that supports drive labels)

Same hardware, different software.

Also, the first hard drive is working fine, and it's internal also.
It doesn't auto-mount on boot, but when I go to "System Menu" the partitions on it are listed, and clicking on them mounts the partitions, no further action needed on my part.

The drive named "movies" is the problem SATA drive I am talking about in this thread, 
the "100gb" is a USB hard drive that WAS working, and is now also giving 'permission denied". I have another thread on this one.


I have not tried installing a new drive under the Kubuntu system I use.

In any event, here is the info you requested:


**fstab**
```
ernest@m7690n:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=b89bf81f-e350-4400-9ca7-4a7451c5d238 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=9753c87c-bace-4082-9ae7-0efd8f8d46bb /boot ext2 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda7
UUID=9c673b2e-aeeb-415d-95a8-1be135c4b400 /home ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda2
UUID=f091c8ab-aa29-4ca6-a540-b2d0aa1ca924 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdg1 /media/sdg1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
LABEL=100gb /media/100gb auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
LABEL=movies /media/movies auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
ernest@m7690n:~$ 

```


**sudo fdisk -l**
```
ernest@m7690n:~$ sudo fdisk -l

Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        2550    20482843    7  HPFS/NTFS
/dev/sda2            2551        2932     3060382   82  Linux swap
/dev/sda3            2933        3314     3060382   83  Linux
/dev/sda4            3315       30401   217568295    5  Extended
/dev/sda5            3315        3441     1012095   83  Linux
/dev/sda6            3442        6137    21647587   83  Linux
/dev/sda7            6138       30401   194892547   83  Linux

Disk /dev/sdb: 750 GB, 750153761280 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 100 GB, 100027630080 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1       12161    97683201    7  HPFS/NTFS
Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Error: Unable to open /dev/scd0 - unrecognised disk label.

Disk /dev/sdh: 203 GB, 203921141760 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdh1               1       24792   199141708   83  Linux
ernest@m7690n:~$ 

```


**sudo blkid**
```

ernest@m7690n:~$ sudo blkid
/dev/sda1: UUID="796E14707BC20CEB" LABEL="m7690n" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="f091c8ab-aa29-4ca6-a540-b2d0aa1ca924" 
/dev/sda3: LABEL="buffer" UUID="5a92e359-9a8c-46a7-8cf2-99b05f11f356" TYPE="ext2" 
/dev/sda5: UUID="9753c87c-bace-4082-9ae7-0efd8f8d46bb" TYPE="ext2" 
/dev/sda6: LABEL="ubuntu-root" UUID="b89bf81f-e350-4400-9ca7-4a7451c5d238" TYPE="ext3" 
/dev/sda7: LABEL="linux-home" UUID="9c673b2e-aeeb-415d-95a8-1be135c4b400" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: LABEL="750-data1" UUID="ea49cca2-75fc-4082-a4d7-4bc040df5d8b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="C084E89884E891E8" LABEL="100gb" TYPE="ntfs" 
/dev/sdh1: LABEL="movies" UUID="0128757d-0ba4-4f4c-809a-1e75b51c524a" TYPE="ext2" 
```
ernest@m7690n:~$

---

### Post by Pro-reason on 2008-09-13
OK, you have so much stuff there that I had to sketch out a diagram to understand it all!

Your fstab file does not properly correspond to your hardware.

Do this in a terminal:
```

cd /etc
cp fstab fstab.backup
kdesu kwrite fstab

```

Then paste the following into the file, replacing its contents.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
**proc /proc proc defaults 0 0**

##################
## SATA drive A ##
##################

## sda5,6,7 are logical partitions within extended partition sda4.

# /dev/sda5
# No label set, so using UUID
**UUID=9753c87c-bace-4082-9ae7-0efd8f8d46bb   /boot   ext2 nouser,relatime,atime,auto,rw,dev,exec,suid   0 2**

# /dev/sda6
# UUID=b89bf81f-e350-4400-9ca7-4a7451c5d238
**LABEL=ubuntu-root   /   ext3   nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid   0 1**

# /dev/sda7
# UUID=9c673b2e-aeeb-415d-95a8-1be135c4b400
**LABEL=linux-home   /home   ext3   nouser,relatime,atime,auto,rw,dev,exec,suid   0 2**

## sda1,2,3 are primary partitions.

# /dev/sda1
# UUID=796E14707BC20CEB
**LABEL=m7690n   /media/m7690n   ntfs-3g   defaults,umask=007,gid=46,noauto,user,rw   0   1**

# /dev/sda2
# SWAP SPACE
**UUID=f091c8ab-aa29-4ca6-a540-b2d0aa1ca924   none   swap   sw   0 0**

# /dev/sda3
# UUID=5a92e359-9a8c-46a7-8cf2-99b05f11f356
**LABEL=buffer   /media/buffer   ext2   defaults,user,exec,auto,rw   0   0**

##################
## SATA drive B ##
##################

# /dev/sdb1
# UUID=ea49cca2-75fc-4082-a4d7-4bc040df5d8b
**LABEL=750-data1   /media/750-data1   ext3   defaults,user,exec,auto,rw   0   0**

##################
## SATA drive C ##
##################

# /dev/sdc1
# UUID=C084E89884E891E8
**LABEL=100gb   /media/100gb   ntfs-3g   defaults,umask=007,gid=46,noauto,user,rw   0   0**

##################
## SATA drive H ##
##################

# /dev/sdh1
# UUID=0128757d-0ba4-4f4c-809a-1e75b51c524a
**LABEL=movies   /media/movies   ext2   defaults,user,exec,auto,rw   0   0**

####################
## Optical drives ##
####################

[B]/dev/scd1 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0

/dev/scd0 /media/cdrom1 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0[/B]

```

This should be an improvement.  There are still things we could change, however.  You need to decide which ones should be mounted at start-up, and which should only be mounted when the user wants to do so.

The numbers at the end govern filesystem checks.

Your fstab file was a mixture of /dev/, UUID and LABEL.  I've tried to standardise on LABEL.  It's the one way of referring to a partition that will not change unless you decide to change it.  I've consistently given the other two ways of referring to the partition too.  I've marked these alternatives with one hash sign (#).  I've used multiple hash signs for other comments.

You should probably try to give sda5 the volume label &#8220;boot&#8221;.

Make sure you have all the right software for those Windows partitions, by doing &#8220;*sudo apt-get install ntfsprogs ntfs-3g*&#8221; in the terminal.

You should also make sure that all those mount-points exist.  Unmount the partitions in question, and do this:

```

cd /media
sudo mkdir m7690n buffer movies 100gb 750-data1

```

---

### Post by egalvan on 2008-09-13
First, many thanks for your rather etensive help on this.

As for labels, I prefer them, but support seems spotty under Linux partition editors....
and I've been wary of using them since Gparted wiped my XP partion whe I changed the label. No great loss, it was a one-week-old install of XP.

I now use PartED Magic, it uses a newer version og GParted, and labels seem to be much better supported. I'm still wary, though.

As for the mix of dev, UUID and Labels, this is more or less Linux doing its thing.

I found a screen-shot I took when I finished using  Parted Magic to set up the first drive.

Maybe it will help. And you can see that sda5 has a label. I couldn't give 'swap' or the extended partition labels.

---

### Post by Pro-reason on 2008-09-13
> **egalvan said:**
> As for labels, I prefer them, but support seems spotty under Linux partition editors....

...

Maybe it will help. And you can see that sda5 has a label. I couldn't give 'swap' or the extended partition labels.

I've never tried to set a label from Gparted.  I always use [the command line for volume labels]("https://help.ubuntu.com/community/RenameUSBDrive").

Yes, as far as I know you can't set a label for swap spaces, unfortunately.  You just have to use UUID.  As for extended partitions, you never need to refer to them, so it doesn't matter.

---

### Post by egalvan on 2008-09-13
> **Pro-reason said:**
> I've never tried to set a label from Gparted.  I always use [the command line for volume labels]("https://help.ubuntu.com/community/RenameUSBDriv").

Yes, as far as I know you can't set a label for swap spaces... just have to use UUID.  As for extended partitions, you never need to refer to them, so it doesn't matter.

Again, thanks. I understand about some labels not being "settable". It's the nature of the beast.

My "problem" with labels is that I look at them from 29 years of DOS-based systems (TRS-DOS, DR-DOS, PC-DOS, MS-DOS, etc.) and am having trouble adjusting my mindset to *nix-based systems. 
(Well, in truth, I'm having trouble with a lot of things. :) )

Anyway, I clicked the link you gave and reached the
Community Document area...
but I got this message:

**This page does not exist yet. You can create a new empty page, or use one of the page templates.**

I ran a search for "label" and "labels" but the site claimed "no matches found".
I find it hard to believe there are no docs that have those words in them...
 so I must have done something wrong in the search...

---

### Post by Pro-reason on 2008-09-13
> **egalvan said:**
> 
but I got this message:

**This page does not exist yet. You can create a new empty page, or use one of the page templates.**

Sorry.  If you look, you'll see that I accidentally chopped an “e” off the end of the URL.  Try again; it should be fine now.

---

### Post by egalvan on 2008-09-15
> **Pro-reason said:**
> Sorry.  If you look, you'll see I accidentally chopped an “e” off ...the URL.  Try again; should be fine.

Oops, I didn't see that missing "e"... sorry.

But I read the page, and it's got a goodly amount of info,
and some excellent links at the bottom.

Thanks!
Lotsa good reading ahead for me..... :)

I just wish all of this documentation was also available "off-line",
such as PDF-formatted files.

I may be an old fogie, but I'm not on-line 25/7. (heresy, I know)

I have downloaded almost all the docs available in the Linux Documentation Project, but much of it is oriented towards programmers and/or server admins...

ErnestG

:popcorn:

---

### Post by Pro-reason on 2008-09-15
If you want the page offline, just save it from your browser, or do:

```
wget -O Labels.html https://help.ubuntu.com/community/RenameUSBDrive
```

If you want it as PDF, then open that in OpenOffice Writer, and export as PDF.

--------

I don't see why you would need to do anything like that though.  All you need to do is skim though the text and see that the command you need is:
```

sudo umount /boot
**sudo e2label /dev/sda5 Boot**
sudo sed -i "s/UUID=9753c87c-bace-4082-9ae7-0efd8f8d46bb/LABEL=Boot/g" /etc/fstab
sudo mount /boot

```

I've never had a separate /boot partition myself, but I presume that once you have booted the system, it is possible to unmount that partition at any time and do this sort of stuff.  It is fails to unmount, then you'll have to do this from a live CD.

---

### Post by egalvan on 2008-09-18
> **Pro-reason said:**
> If you want the page offline, just save it from your browser, or do:
--------

I don't see why you would need to do anything like that though.  All you need to do is skim though the text and see that the command you need is:


Don't quite know what you are referring to here,
but if  you are asking "why do I want to download pages, etc..."

Well, I am not connected to the internet 24 hours a day. :)

In fact, I have been know to go five or more days with-out being on-line.

So having the information on my portable drive, or Palm Pilot,
 makes it easy to read at my leisure,

 wherever I am, whenever I want.


I've been experimenting with the 'wget' command and it's options.
Not always what I want....
which is ONE file, that can be viewed off-line, such as PDF.

I used to use IE's "save as single file" option, which would save a single file with everything the page had, basically a snap-shot, easy to move around, easy to re-name.
Not as good as PDF, but close for single-page-sized documents...
I have to admit, I've not had the same experience with Firefox.

---

### Post by Pro-reason on 2008-09-18
> **egalvan said:**
> Don't quite know what you are referring to here,
but if  you are asking "why do I want to download pages, etc..."

I wasn't asking anything.  I was pointing out that since “sudo e2label /dev/sda5 Boot” was the entirety of the information that you needed to extract, there was no need to save the entire page (with all the sections dealing with other filesystems) to disk for later.

When saving web pages, if the HTML of the page is not enough for you (because you want the pictures, etc), then install the [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") extension for Firefox.

---

### Post by egalvan on 2008-09-20
> **Pro-reason said:**
> I wasn't asking anything.  I was pointing out that since “sudo e2label /dev/sda5 Boot” was the entirety of the information that you needed to extract, there was no need to save the entire page (with all the sections dealing with other filesystems) to disk for later.

My problem is remembering information such as "sudo e2label /dev/sda5 Boot"
which is one reason I like to download all the page...
also, the rest of the information (page) will better help me remember the context.
And also, you have given me a LOT of useful information...
just because i don't need it right now, doesn't mean I won't need it later...and I probably will... so it's real nice to have it fairly well accessible.


> When saving web pages, if the HTML of the page is not enough for you (because you want the pictures, etc), then install the [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") extension for Firefox.

See, even more useful information. which a month from now I will have trouble remembering in detail, so having it on my hard drive is very useful to me...

Which is why all the help you have given is so useful...
not only directly, but because you have pointed out other ways and directions to follow, and study, and expand my knowledge...

---

### Post by egalvan on 2008-09-20
> **Pro-reason said:**
> there was no need to save the entire page

One more observation (which will surely show my age)...

I am more comfortable reading from a printed page, rather than a screen.

In 1979, I saw my first computer screen; I was 25 years old :eek:

Old habits die hard.

ErnestG

---

