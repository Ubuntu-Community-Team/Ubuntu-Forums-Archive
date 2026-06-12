---
title: "Problems formatting a ext2 drive"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by fuchur86 on 2013-11-09
Hey everybody,

I've never used linux, so please be gentle with me asking stupid questions :)
I'm trying to get a DCP (Digital Cinema Package) on an external Hard Drive, that has to be formatted ext2 in order for the projector to recognize it.
So I downloaded the 32bit Ubuntu live disc (64bit didn't work for some reason) and booted from the disc.
I then went to the disk utility and formatted my drive with the ext2 filesystem.
Now I want to copy my DCP (which is on an NTFS drive) from within ubuntu to my newly formatted external drive. (so I don't have to find a way to be able to write to ext2 drives in windows)
For some reason the drive is always read only. I tried checking and unchecking the "Take ownership..." box without any success and I really don't know were I'm going wrong, or what I could do differently for that matter. So any kind of help here would be much appreciated!

Thanks in advance!

---

### Post by ajgreeny on 2013-11-09
This is all because of the permissions that files and folders have in Linux which is a great security advantage that you have to get used to if using Linux as your main OS.  Windows does not have nor understand those permissions.

So, using the live Ubuntu system start the file manager nautilus by holding down Ctrl+Alt+T to open a terminal and in that type gksudo nautilus and hit enter.

That will open the file manager as root and allow you to copy any files and folders needed to anywhere else.

---

### Post by Bashing-om on 2013-11-09
fuchur86; Hi ! Welcome to the forum .

1. Here on this forum, there is no such thing as a "dumb question" ! Ask away !

2. Windows can not recognize the linux file system, unlike the reverse in that ubuntu can cope quite readily ( and getting better all the time) with the Windows' file system.
+
3. Permissions issues. Uhh, that can be perplexing. Are you wanting to auto mount that partition, or use that partition as on demand only ?

For your reference, my data partitions are to be mounted from the command line only, as on-demand. This limits the possibility of inadvertent data corruption. But, this lays on me the responsibility to manage those partitions, an in manually unmounting them when my task is completed.

To the end of properly mounting and addressing these partitions post back the out puts of terminal commands:
- between code tags - 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

```

sudo fdisk -lu
sudo parted -l
sudo blkid
mount
cat /etc/fstab
ls -la /media

```
Will relate the partitioning schemes, permissions and mounting presently set in the operating system.

[INDENT][INDENT][INDENT]so a tale is told
[/INDENT][/INDENT][/INDENT]

---

### Post by coffeecat on 2013-11-09
@Bashing-om, the OP is using an Ubuntu live CD. Much of what you have asked for is really of relevance only to a permanent installation of Ubuntu and will only confuse the OP.

@fuchur86, ajgreeny's suggestion will allow you to write to the ext2 external drive, but all the files will probably be owned by root. This may or may not be a problem when read by the projector, so...
 
> **fuchur86 said:**
> 
I'm trying to get a DCP (Digital Cinema Package) on an external Hard Drive, that has to be formatted ext2 in order for the projector to recognize it.

Can you tell us a little more? Do you have some more details about what is required by the projector?

---

### Post by fuchur86 on 2013-11-09
Unfortunately I don't have much more info on the projector, other than the fact that it didn't mount my exFat formatted flash drive and that it's supposed to be working flawlessly with ext2 drives, as it is running some kind of linux... I'm not sure about auto-mount, but I guess once the DCP is one there I'd be fine with read only, since the DCP will be copied onto the projectors hard drive (or a connected media server).
I'll probably have some more info by tomorrow from the projectionist.
I'm just really confused by the permissions thing. From Windows and OSX I'm used to just format a drive with the filesystem I need and be done with it.
I'll get back to you guys, once I know more.

Thanks!

---

### Post by coffeecat on 2013-11-09
That would be interesting, thanks.

I've done a little reading since I posted last. The media servers serving digital projectors usually run Linux - hence the need for a Linux filesystem. There's also something about inode size for compatibility with some servers, and the default inode size in Disk Utility would be wrong for them. We can come back to that if that turns out to be a problem.

OSX uses exactly the same Unix permissions/ownership system than Ubuntu and Linux generally (albeit with the HFS+ filesystem), but OSX Disk Utility is a bit more user friendly than the Ubuntu Disk Utility when it comes to making sure that the filesystem has permissions and ownership usable by an ordinary user.

By the way, re-reading your first post, I think you may not have done the "take ownership" bit correctly in disk utility. After ticking the take ownership box, you have to reformat the drive. But even if you did, it may not help. In the Ubuntu live session, the user is the live session "ubuntu" with an odd UID (999). Probably more important than file ownership is to get permissions right, but again we can come back to that when you have some more details.

---

### Post by cmcanulty on 2013-11-09
Once you are in gksudo nautilus change the ownership to you by rt cl-props-pick yourself

---

### Post by ajgreeny on 2013-11-10
> **cmcanulty said:**
> Once you are in gksudo nautilus change the ownership to you by rt cl-props-pick yourself

? ? ? 
You nearly totally lost me with that, so I suspect the OP will be even more baffled.

What I think you meant was "**right click, go to properties and select your username**" but that is not very helpful as the OP is only using a live system to do this one job; we are simply trying to help him do it in the easiest manner.

---

### Post by fuchur86 on 2013-11-10
Still no word from the projectionist. It might take a while until I hear from him. The theater just got the digital projector and media server a couple of weeks ago and there's only a few people who really know their way around this stuff.
For my EXT3 formatted drive - using the nautilus command I was able to copy the DCP to the drive. I'm really not familiar with inode size and all that, but again, I hope I'll get some definite info on that from the projectionist.
You'll hear back from me, once I know more.

Thanks!
______
EDIT
So today I'm being told that a simple "windwos formatted" (so I'm guessing NTFS) drive would suffice. I'll try to get some more info out of the projectionist concerning EXT2 and EXT3 drives anyhow.

---

