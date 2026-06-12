---
title: "Force rewrite"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Zenereffect on 2012-02-04
I've searched the web with no luck in finding an explanation of what "force rewrite" is actually doing when you say yes.  I've been trying to mount a 2TB westen digital drive and am in the process of using fsck and have ignored several errors and performed just as many force rewrites. I'm seeing numerous failed commands and errors, usually error { UNC } and failed command: READ DMA. I'm just wondering what all this means since I'm very new to Linux in general.

---

### Post by hansdown on 2012-02-04
Welcome to the forum, Zenereffect.

Hope this helps.

[http://manpages.ubuntu.com/manpages/lucid/man1/ecryptfs-rewrite-file.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/ecryptfs-rewrite-file.1.html)

---

### Post by Zenereffect on 2012-02-04
Thank you! That's exactly what I was looking for.

---

### Post by sudodus on 2012-02-04
Please describe your computer and your operating system (version)!

Have you been able to mount that hard disk drive (HDD) before (with Linux or Windows or MacOS)?
Is it internal or external?
What partitions and file system are there on the HDD?
Is there an operating system on the HDD?

---

### Post by Zenereffect on 2012-02-04
I don't know if it was actually a problem with ecryptfs, I'm too new at this to say. But here are the specifics: 

I'm running a Mac pro with Ubuntu 11.10

The drive is a western digital my book live 2tb. The drive quit working with the wireless so I took it out of the case and into the Mac pro desktop tower. 

While researching forums I tried installing mdadm and running associated commands, but that didn't seem to help, so I started running the fsck command. As I said i've forced rewrite a few times, but at this point it's been on the same force rewrite for about an hour (seems to me that means it's frozen).  I don't have valuable data on there, but there are a handful of movies I didn't get a chance to backup before the problems started, so I'm trying to mount the drive using Ubuntu so I can recover those files. Any other advice is welcomed, although I'm stuck in the force rewrite command, so I can't run any others till it either finishes or I decide it can't complete the current task...

---

### Post by sudodus on 2012-02-04
So it was an external HDD that stopped working. Did it ever work after you took it out of its case and put it into your Mac? I mean: have you run it normally inside your Mac for some time, or did you put it there now, and still try to get some response from it?

If the disk is failing (with read/write errors) you should not [COLOR=black]start any more force rewriting,[/COLOR] but clone it to a fresh drive of the same size with ddrescue. Install it
```
sudo apt-get install ddrescue
```and read the excellent manual page
```
info ddrescue
``` [COLOR=Red]but wait. Don't do that at once. Just stop wearing the disk![/COLOR]

Maybe you know what file systems there are (were). So first you can check if they are found by Ubuntu
```
sudo fdisk -lu
``` Do you see what you expect? Please post the output of the command within code tags (mark the text and use the # icon above). Or you can use ***Gparted*** to view it (and later on maybe edit). In that case you can make a screenshot and attach the screenshot file to your next post.

---

### Post by Zenereffect on 2012-02-04
The WD My Book Live uses an internal drive attached to an Ethernet card that you connect to your wireless router in order for the drive itself to become wirelessly accessible to any computer on the network (as well as through a website).  I don't know for sure but I think the Ethernet card failed, not the drive itself. Because of the specific format they use, when you install it inside the tower, as you would any other internal drive, the computer doesn't know exactly what to do. My Mac recognizes the drive but says it can't read the format. Windows won't even recognize the drive. Linux sees the drive but gives me the error message "Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb4, missing codepage or helper program, or other error. In some cases useful info is found is syslog - try dmesg | tail or so". (I now have all three OS's running on my MacPro - those being Ubuntu, Win7, OSX, all updated to the most recent versions). When I tried to run fsck, force rewriting and ignoring errors, the process at some point seemed to get stuck, since it didn't proceed from the "current" task (for about 2 hours) I forced shut down the computer holding the power button. 

To be specific, since I removed the drive from its external case and installed it internally to the Mac I have not been able to access the data (which means I have not been able to get it working since the initial "crash", but as I said I think it's the network card, not the drive, but I can't be sure until I reformat it - something I don't want to do until I recover my data). 

The only file system reference I've seen is that it's formatted in EXT4, but that doesn't mean anything to me because I'm new to Linux. And I don't know for sure that what I saw was informing me of the drive's format (though I don't have a clue what else it could have been in reference to). 

No OS is installed as far as I know, but their could be some proprietary software or drivers that are designed to work directly with the network card. 

If I'm going to attempt cloning a 2TB drive, that means I need another 2TB drive (obviously), so my preference is to avoid that because I only have 2 50GB drives and one 1TB drive, all being used in form or another. Though if it comes down to it the drives are cheap enough these days. 

Being new to Linux any commands with f makes me think format, so what command (probably listed as a dangerous command) do I NOT want to use to avoid reformatting the drive? In other words, what does fdisk do/mean? (I realize this is a newb question, randomly I know some advanced stuff, yet I still don't know all the beginner stuff). If you're willing, can you describe what the commands you recommend are doing more specifically? Or even just what the acronyms stand for, since those are usually self descriptive. 

Lastly, what are the different screen shots I can take and how do I take them in Linux? I'm reading an intro to Linux book, so eventually I'll get there, but I'm also being impatient and want to get the data off the drive so I can be done with it and start "playing." :)

Most importantly, thanks for all the help and support! I'm impressed to see such a dedicated community and am glad I found it! I plan to start helping others with their inquiries as soon as I know enough, which shouldn't take long. Thanks again! Cheers!!

---

### Post by sudodus on 2012-02-05
> **Zenereffect said:**
> ...  I don't know for sure but I think the Ethernet card failed, not the drive itself. Because of the specific format they use, when you install it inside the tower, as you would any other internal drive, the computer doesn't know exactly what to do. My Mac recognizes the drive but says it can't read the format. Windows won't even recognize the drive. Linux sees the drive but gives me the error message "Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb4, missing codepage or helper program, or other error. In some cases useful info is found is syslog - try dmesg | tail or so"
...
When I tried to run fsck, force rewriting and ignoring errors, the process at some point seemed to get stuck, since it didn't proceed from the "current" task (for about 2 hours) I forced shut down the computer holding the power button. 

To be specific, since I removed the drive from its external case and installed it internally to the Mac I have not been able to access the data (which means I have not been able to get it working since the initial "crash", but as I said I think it's the network card, not the drive, but I can't be sure until I reformat it - something I don't want to do until I recover my data).

The only file system reference I've seen is that it's formatted in EXT4,  but that doesn't mean anything to me because I'm new to Linux. And I  don't know for sure that what I saw was informing me of the drive's  format (though I don't have a clue what else it could have been in  reference to). 

We don't know what file system it is. /dev/sdb4 is partition number four. I does not mean ext4 (which is a modern linux file system) but the drive might have had a dedicated small linux system with ex4. [COLOR=Red]If someone else here know about this type of drive, please let us know![/COLOR]
> 
...
what does fdisk do/mean?  If you're willing, can you describe what the commands you recommend are doing more specifically?
***fdisk*** is an old tool to format disks (edit partitions and file systems), but used with the -l option (lower case L) and -lu it is only listing and describing to partitions it finds. So
```
sudo fdisk -lu
``` is safe.

***Gparted*** is a new tool to edit partitions and file systems. It has a graphical user interface (GUI). When not only listing but actually editing, you should boot your computer from another drive (for example a live CD or USB drive).
> 
Lastly, what are the different screen shots I can take and how do I take them in Linux? I'm reading an intro to Linux book, so eventually I'll get there, but I'm also being impatient and want to get the data off the drive so I can be done with it and start "playing." :)
...
The output of ```
sudo fdisk -lu
``` and other terminal commands can be cut and pasted into the editing box of the Ubuntu Forums (quick and easy, no screenshot is necessary). But to show what Gparted finds, you take a screenshot with alt + PrintScreen, save the file and attach the file using the [COLOR=Red]Additional Options[/COLOR] below this editing box.

Finally, if we cannot find any file system or understand what it should be, you can use 

- special tools to try to get partitions and file systems back, for example ***testdisk*** and ***gpart***, or

- a special tool to get back the files without [knowledge about] a file system, ***photorec***. This tool looks at the data stored on the drive and can identify the beginning of several file types. It started as a tool to recover photo files from flash cards with borked FAT file systems, and has developed into a general tool for several common file types. But it does not recover the file names, and it does not recover the directory structure. It is hard work to recover files that way, but it works.

Several threads in this forum describe how people succeed using testdisk and photorec. A few thread show success with gpart. Depending of the damage, different tools work.

---

### Post by Zenereffect on 2012-02-05
Here is the output of 

```
sudo fdisk -lu
``````
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33          16+  ee  GPT
/dev/sda2              34    48828159    24414063   82  Linux swap / Solaris
/dev/sda3   *    48828160   976771519   463971680   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT
```

---

### Post by Zenereffect on 2012-02-05
Also, I don't remember what command I typed to see it, but somewhere along the line I did see EXT4, seemingly in reference to the drive in question.  I recognize that /dev/sdb4 is not in reference to fs type, but rather the path/location of the drive.  That being said, I cannot guarantee the fs type is EXT4, but it looked that way.

---

### Post by Zenereffect on 2012-02-05
How does Gparted work? I installed gparted, but got the message: "cannot open display" (I did not try booting from cd then running it, if that's required first)

And is there a way to change the subject of this post, since we've deviated quite a bit from the "force rewrite"? or should I bother?

---

### Post by sudodus on 2012-02-05
There is GPT, GUID Partition Table on both drives.
[[COLOR="Red"]_http://en.wikipedia.org/wiki/GUID_Partition_Table_[/COLOR]]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

If you can mount and read this partition table on the first drive /dev/sda, you should also be able to mount and read it on the second drive, /dev/sdb, which is the one with problems.

But fdisk does not find any partition on that drive. I suggest that you browse the internet to learn about testdisk and gpart, and then try to use them. If no luck, resort to photorec!
--
[COLOR="red"]Maybe someone knows about this drive and can suggest what to do:
The WD My Book Live[/COLOR] uses an internal drive attached to an Ethernet card that you connect to your wireless router in order for the drive itself to become wirelessly accessible to any computer on the network (as well as through a website.

---

### Post by sudodus on 2012-02-05
> **Zenereffect said:**
> How does Gparted work? I installed gparted, but got the message: "cannot open display" (I did not try booting from cd then running it, if that's required first)

And is there a way to change the subject of this post, since we've deviated quite a bit from the "force rewrite"? or should I bother?
How did you install gparted?

0. It is already there on the install CD or USB, when you run a live session.

1. ```
sudo apt-get install gparted
``` should do the trick. You might have installed something not compatible. Take that away!
--
You must ask the [COLOR="Red"]**moderators**[/COLOR] to change the title of the thread, I think you cannot do it yourself. But an alternative is to start a new thread with an appropriate title (and we can continue there, hoping to attract someone with more knowledge about your drive and problem).

---

### Post by Zenereffect on 2012-02-05
I posted a new thread [here]("http://ubuntuforums.org/showthread.php?p=11666098#post11666098")

[http://ubuntuforums.org/showthread.php?p=11666098#post11666098](http://ubuntuforums.org/showthread.php?p=11666098#post11666098)

---

