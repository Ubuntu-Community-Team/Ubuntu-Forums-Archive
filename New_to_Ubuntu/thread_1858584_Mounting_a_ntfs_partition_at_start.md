---
title: "Mounting a ntfs partition at start"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Carllacan on 2011-10-12
Hi!

I've just installed Ubuntu on my laptop and created some partitions, the one for Windows, the one for Ubuntu and a larger one to store data. I decided to make the last one a NFTS partition, since I read that, through ext4 was better it can't be seen from Windows.

So now the only thing left I want to do is to configure Ubuntu to mount the data partition al starting. I tried to edit fstab, but when I use mount -a I just get a error, and I've read that may be due to the NFTS format, which is unfriendly to ubuntu.

Is there anything I can do?

---

### Post by 11jmb on 2011-10-12
Linux does not like NTFS
Windows does not like ext

They both can read and write to/from FAT32 format as long as the files are under 4 GB apiece

---

### Post by Carllacan on 2011-10-12
Actually many of the files are larger than 8 GB... 

Isn't there anything I can install in order to make ubuntu able to mount the data along with the others? 

I have no problem at all reading files stored in the NFTS partition, so it is not completely troubeling for Ubuntu to handle with it.

---

### Post by Morbius1 on 2011-10-12
> I tried to edit fstab, but when I use mount -a I just get a error, and  I've read that may be due to the NFTS format, which is unfriendly to  ubuntu.
Linux can read and write to an NTFS partition.

Please post the output of the following commands please:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by Mark Phelps on 2011-10-12
You can't use "mount -a"; instead, it needs to be "sudo mount -a".

Perhaps that is why you were getting an error.

Also, do not format a shared data partition FAT32; instead, format it NTFS.  Linux has been able to read/write NTFS partitions for years now.

---

### Post by 11jmb on 2011-10-12
> **Mark Phelps said:**
>  Linux has been able to read/write NTFS partitions for years now.

Thanks for correcting me. I've been using shared f32 partitions forever and somehow missed that update!

---

### Post by BHEJU on 2011-10-12
Well Fat 32 is old and does not support large files (<4 gig).
Two options:
1
NTFS Partition.. automount it using GUI by NTFS Config Tool (available in synaptic).
2
EXT3 or ext4 partition.
And install Ext2Read in windows. Ext2Read makes windows smart enough to read - write to ext.

Cheers,

---

### Post by Lisiano on 2011-10-12
> **11jmb said:**
> Linux does not like NTFS
Windows does not like ext

They both can read and write to/from FAT32 format as long as the files are under 8 GB apiece

> **BHEJU said:**
> Well Fat 32 is old and does not support large files (<4 gig).
Two options:
1
NTFS Partition.. automount it using GUI by NTFS Config Tool (available in synaptic).
2
EXT3 or ext4 partition.
And install Ext2Read in windows. Ext2Read makes windows smart enough to read - write to ext.

Cheers,

FAT32 only 4GB... Lie. FAT32 supports upto 2TB (2048GB). FAT16 is up to 4GB 
[http://en.wikipedia.org/wiki/File_Allocation_Table#Size_limits](http://en.wikipedia.org/wiki/File_Allocation_Table#Size_limits)

Though yes, Linux has NTFS R/W support but it's still better to avoid it since you NEED to use Windows to check the FS if anything goes wrong, better to use either EXT2/EXT3 (There are drivers for Windows to see it) or to make it FAT32.

Note: EXT4 is NOT compatible with Windows 3rd party drivers as is. It needs to be manually created with most features that make it EXT4 and not EXT3 disabled, that is, dumb EXT4 down to EXT3.

---

### Post by Morbius1 on 2011-10-12
> FAT32 only 4GB... Lie. FAT32 supports upto 2TB (2048GB). FAT16 is up to 4GB You're confusing the amount of space fat32 can access with the largest file size permissible. If you look at the wikipedia link you referenced you will see that the max file size limit is 4GB - 1 byte.
> Though yes, Linux has NTFS R/W support but it's still better to avoid it  since you NEED to use Windows to check the FS if anything goes wrong,  better to use either EXT2/EXT3 (There are drivers for Windows to see it)  or to make it FAT32.It's a toss up as to what's the worst thing to do:

(1) Mounting the WindowsOS partition read/write in Linux.

(2) Installing a driver in Windows and actually allow it to access a Linux partition.

Luckily, the OP is creating an NTFS data partition and is avoiding both (1) and (2).
> NTFS Partition.. automount it using GUI by NTFS Config Tool (available in synaptic)ntfs-config is a very strange little utility. When you first run it it asks you if you want to enable write support for ntfs, apparently oblivious to the fact that it's already enabled by default. Combine that with it's inability to identify partitions by UUID, and the fact that it hasn't been maintained since the Carter administration and well .....

---

### Post by Lisiano on 2011-10-12
I take my words back, I misread the article (Bad tables)
Then yes, only option is to use NTFS or to feed Windows some drivers for EXT2.

---

### Post by JC Cheloven on 2011-10-12
I think the OP deserves some concise advice on how to mount his NTFS partition at startup, which AFAI understood is what he wanted in the first place. 

1) Find out the UUID of your partition. This command from terminal will tell you:```
sudo blkid
```

2) Edit the file etc/fstab as root with your favourite editor (for ex., run "gksudo gedit /etc/fstab" from a terminal), and add a line like this```
UUID=[COLOR="Red"]734240563B00719[/COLOR]   /media/DOC    ntfs   defaults
```
You must replace the UUID (in red) with the actual identifier of your disk. You can also replace "DOC" by any other string you would like to see. If you want to know more about the options (other than 'defaults'), you can type "man fstab" at terminal.

EDIT: and yes, you made the right decision setting uo an ntfs partition to access data from both OSes.
JC

---

### Post by Morbius1 on 2011-10-13
> **JC Cheloven said:**
> [COLOR=Blue]I think the OP deserves some concise advice on how to mount his NTFS partition at startup, which AFAI understood is what he wanted in the first place. [/COLOR]

1) Find out the UUID of your partition. This command from terminal will tell you:```
sudo blkid
```2) Edit the file etc/fstab as root with your favourite editor (for ex., run "gksudo gedit /etc/fstab" from a terminal), and add a line like this```
UUID=[COLOR=Red]734240563B00719[/COLOR]   /media/DOC    ntfs   defaults
```You must replace the UUID (in red) with the actual identifier of your disk. You can also replace "DOC" by any other string you would like to see. If you want to know more about the options (other than 'defaults'), you can type "man fstab" at terminal.

EDIT: and yes, you made the right decision setting uo an ntfs partition to access data from both OSes.
JC
It would also have been helpful if your advice was correct.
> UUID=[COLOR=Red]734240563B00719[/COLOR]   /media/DOC    ntfs   defaults* You left off the dump-freq and the pass-num at the end of that line.
* Although once corrected for the above it will work there are some problems with it:

- He'll get an error message if he tries to send something to the trash because trash is owned by root.
- Since this is a dual boot and the partition will also be used by Windows he'll need to take precautions against saving file names with characters that Windows cannot interpret.

The following would eliminate both problems:
```
UUID=734240563B00719 /media/DOC ntfs defaults,uid=1000,nls=utf8,windows_names 0 0
```[COLOR=Blue]EDIT[/COLOR]: Had the OP provided the requested information:
```
sudo blkid -c /dev/null
cat /etc/fstab
```He would have been provided aid from any number of people specific to his exact situation.

---

### Post by JC Cheloven on 2011-10-13
> **Morbius1 said:**
> It would also have been helpful if your advice was correct.
* You left off the dump-freq and the pass-num at the end of that line.

Implying that my advice was incorrect because of "that", is a symptom of anger or something? I'm really sorry, I didn't intend to. Only, I was surprised of looking at people getting engaged in offtopic discussions while the OP remained unanswered. 

I offered a simple solution. I still wonder why someone else didn't drop a line before with something similar.

> 
The following would eliminate both problems:
```
UUID=734240563B00719 /media/DOC ntfs defaults,uid=1000,nls=utf8,windows_names 0 0
```[COLOR=Blue][/COLOR] 
Agreed, it's a better one. Should this have been post#4? ;)

Have a nice day
JC

---

### Post by Carllacan on 2011-10-13
Ok, I tried some stuff -thank you for all those answers, by the way- and ¡it's works perfectly fine!

The key was to use this:

UUID=734240563B00719 /media/DATA ntfs defaults,uid=1000,nls=utf8,windows_names 0 0

on the fstab. I had been trying something alike before, but it wouldn't work. I guess using the UUID made the difference.

Thanks to all of you :-)

PD: I learned a lot reading all your discussions; I think I'm gonna love this place :-)

---

### Post by JC Cheloven on 2011-10-13
Glad you solved it. And be careful, you may eventually get caught by this site, as many of us did :)

@Morbius1: in a second read of your last post, it's possible that we had a little misunderstanding. Please note that the two trailing zeroes will default to the correct values if ommited. I use the command (for this same purpose) ending by 'defaults,users', for example.

Cheers
JC

---

### Post by Morbius1 on 2011-10-14
> **JC Cheloven said:**
> Please note that the two trailing zeroes will default to the correct values if ommited.And what would those "correct" values be? Do you know? Is it the same for every filetype? My recommendation is to finish the sentence in fstab.
> **JC Cheloven said:**
> I use the command (for this same purpose) ending by 'defaults,users'This forum is obsessed with the use of "user" and "users" in fstab and I really don't know why. From man mount:
> users: Allow every user to mount and unmount the file system.It's not going to do what you think it will do. Let's take a simple example of an ntfs partition I have automounted via fstab:
> UUID=734240563B00719 /windows/WinXP2 ntfs defaults,users 0 0Can I as an "every user" mount the partition?
- First, it's already mounted so why do I want to mount it again.
- Second,
> mount UUID=734240563B00719 -t ntfs /home/morbius/WinXP2
mount: only root can do thatNope

Can I as an "every user" at least unmount the partition?
- First, if I've gone through all the trouble of having it automount why do I want any old user to unmount it.
- Second,
> umount /windows/WinXP2Yep, that works. Now what? Have the next user mount it again?

Ok, so I try to mount it now that it's unmounted:
> mount UUID=734240563B00719 -t ntfs /home/morbius/WinXP2
mount: only root can do thatHmmm ... OK how about this way:
> mount UUID=734240563B00719
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
Hmmm ... maybe this way:
> mount /windows/WinXP2Nope, same error

Well, fudge.

Don't get me wrong, the use of user and users has it's place ( user + noauto makes sense for a Linux partition for example ) but in general it I would recommend just leaving it out.

In all seriousness though I was really expecting some Linux purist to take me to task for my use of "defaults" in fstab since ( among other things ) it made every file executable telling me that the "proper way" to write the line was this way:
> UUID=734240563B00719 /media/DOC ntfs defaults,uid=1000,nls=utf8,windows_names,dmask=000,fmask=111 0 0

---

