---
title: "Change permission for main ubuntu drive"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rinasek on 2008-06-06
First i have to tell you i'm really new to linux/ubuntu, and to tell you dont have a clue. Have MCSE and MCSA certificates but that doesn't help a bit :P, but how it should. 

Now here's my problem on my big drive i have two partitions first with winXP pro (well its lastxp v17) and second is just for all other data. Both of them are ntfs. Second smaller drive have instaled Ubuntu 8.04. My main problem is that i got everything working, read/write, on both partitions of big drive. But i cant change permission for drive with ubuntu or how its named "filesystem", only thing i can do is read. How can i change that.

Here is my fstab report:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0212022c-6856-4b81-93fb-36c125a10ddd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=31769a33-786d-4d66-ae79-fe2d18e4c8a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


Please someone help my windows formated brain to catch how this works, or its going to explode of googleing. 

Thanks in advance to everyone.

---

### Post by Bodsda on 2008-06-06
Hi, im not to good with fstab but i notice a missing parameter in one of the lines.

this line 
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
has no permission option, try changing it to

```
/dev/scd0       /media/cdrom0   udf,rw,iso9660 user,noauto,exec,utf8 0       0
``` 

Note: the 'rw' after 'udf,' in the second example

for further, more in depth information look at

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

Hope this helps

---

### Post by cariboo on 2008-06-06
You don't want to change permissions on your ubuntu drive. The only place you have write permissions is your home directory. If you have to make any changes to configuration files use sudo as in:

```
sudo gedit someconfigfile
```

There really isn't any need for you to go into any directories and change things. Remember Ubuntu (and linux) is not Windows, you don't run as an administrator all the time.

Jim

---

### Post by rinasek on 2008-06-06
@Bodsda

Problem is not with dvd drive... but guess i'll eventualy come to that :D

@cariboo907

ok, understand that, but if i want to put skin for aMSN. its located in /usr/share/amsn. No permission to copy there. Maybe i understood wrong instalation tip.....

tnx to both of you

---

### Post by cariboo on 2008-06-06
There should be an amsn directory in your home directory, it may be hidden. Click on Places-->Home Folder and Ctrl-h to see the hidden files and folders.

Jim

---

### Post by The Cog on 2008-06-06
You can get a file manager window with full permissions by running this command either from a console window or entering into <Alt><F2>:
**gksudo nautilus**
This file manager window runs with root's privilege. I always set the bacground red to remind me its not a normal file manager. Go careful with it. 

And remember that if you **move** a file from your own folder to /usr/share/amsn that file still remains owned by you which is wrong - system files should generally be owned by root. If you **copy** the file there instead, the copy is created with root as the owner because root created it, so this is what you should do.

---

### Post by rinasek on 2008-06-07
tnx very much everyone it helped a lot
just downloaded bunch of books, its time for reading :D

---

### Post by Paqman on 2008-06-07
> **rinasek said:**
> 
ok, understand that, but if i want to put skin for aMSN. its located in /usr/share/amsn. No permission to copy there. Maybe i understood wrong instalation tip.....


That's what sudo is for. It's also what stops any malware from affecting your system. In order to make any changes to the root-owned parts of the filesystem you need to authenticate yourself as someone (or something) that has admin rights.

It's the kind of security model MS are moving towards with Vista's UAC. Everybody has limited privileges by default, but users can take on higher privileges temporarily to complete certain tasks.

---

### Post by pbenway on 2008-06-08
Hope you don't mind that I post a question here, but I've been around the forums for hours and nowhere else is anyone closer to my core problem, than what is addressed here.
Question: How do I regain control over an external disk (Fat32) that has suddenly turned "read-only"?
Any help, or direction to a thread that actually solves this appearantly common problem, will be much appreciated. Sorry once again, to barge in with a question like this...

---

### Post by Paqman on 2008-06-08
> **pbenway said:**
> 
Question: How do I regain control over an external disk (Fat32) that has suddenly turned "read-only"?


That sounds pretty odd. The permissions on a drive shouldn't just change by themselves. Is it a hard drive or a USB stick?

---

### Post by pbenway on 2008-06-09
No, it shouldn't! But appearantly others have the same problem with drives, psp sticks, mp3-players, etc. Mine is a hard drive (Lacie 1tb, vfat!). I have two hypotheses:
1. Something went wrong when I first deleted a folder from the external hard drive, then went into Trash and removed it permanently.
2. It seems two folders on the drive have become corrupted (unknown type, unable to open), and if errors are detected while mounting, the permissions turn to read-only. when i print "mount" in terminal, the output says:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)

I have tried all suggestions from this thread: [http://ubuntuforums.org/showthread.php?t=816215&goto=nextnewest]("http://ubuntuforums.org/showthread.php?t=816215&goto=nextnewest")
but nothing helps.

---

### Post by cariboo on 2008-06-09
Can you change the permissions on wherever it is mounted eg:

```
sudo chmod -R 777 /media/disk
```

where /media/disk is wherever you have /dev/sda1 mounted?

Jim

---

### Post by pbenway on 2008-06-09
Thank you for the tip Jim, bu I ran the chmod-command, to no avail (replaced "media/disk" with "media/T_BICKLE", the name of my disk). Also tried to unmount & automatically mount the disk afterwards; still read-only access...

---

