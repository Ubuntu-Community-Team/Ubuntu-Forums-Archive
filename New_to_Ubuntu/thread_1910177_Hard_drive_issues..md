---
title: "Hard drive issues."
date: 2012-01-16
forum: New to Ubuntu
---

### Post by rennerjack on 2012-01-16
Okay, I have had a few issues with ubuntu before, but I absolutely NEED help with this one.
I need help mounting a hard drive that already has data on it, it's logical name is /dev/sdb. I tried making a mount point like this: "sudo mkdir /media/dev/sdb", but I got a "no such file or directory" error. 
Does this count as absolute beginner talk?

---

### Post by sudodus on 2012-01-16
If you have 'vanilla' Ubuntu, your file browser should be Nautilus. When you run it, click on the icon or name in the left panel. If it does not mount, click once more. If it still does not mount, start Nautilus as superuser (root) ```
sudo nautilus
``` and try the same again.

If you want to use terminal commands, first make a directory, then mount partitions, not the whole drive. The [COLOR=Red]first partition[/COLOR] of the [COLOR=RoyalBlue]second drive[/COLOR] is **[FONT=Courier New][SIZE=3]/media/sd[COLOR=Red][COLOR=RoyalBlue]b[/COLOR]1[/COLOR][/SIZE][/FONT]** etc. Run the following command to find all partitions ```
sudo fdisk -lu
``````
sudo mkdir /media/sdb1    # only once (the directory stays)
sudo mount -t auto /dev/sdb1 /media/sdb1   # every time
```Later on you can enter the mounting command into the file [SIZE=3]**[FONT=Courier New]/etc/fstab[/FONT]**[/SIZE] to make it happen every time you boot.

---

### Post by Double.J on 2012-01-16
Welcome to the forums rennerjack
When you say you tried to make a mount point with mkdir... did you mean mount with a format such as
```

sudo mount /dev/sdb /path-to-mount-at

```

or make a directory with mkdir? mkdir can't write to a device that isn't mounted :)


it sounds you want to make a directory such as ```
 sudo mkdir /data
``` then mount your drive at /data for example ```
 mount /dev/sdb /data 
```

also is it an ntfs partition?
___________________________________________________________________
PS
> **sudodus said:**
> ```
[COLOR="Green"]**gk**[/COLOR]sudo nautilus
```  ;)

---

### Post by rennerjack on 2012-01-16
I ran the last command you told me to try and got the following error:                     mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I've seen this before, what does it mean?

---

### Post by rennerjack on 2012-01-16
The last command Sudodus gave me.

---

### Post by rennerjack on 2012-01-16
Yes it's ntfs.

---

### Post by sudodus on 2012-01-16
Please post the output of
```
sudo fdisk -lu
```You can cut and paste between the web browser and terminal window in both directions. And remember to put code tags around the text from terminal, mark it and press the # icon above. Then we have a better chance to help you.

---

### Post by Double.J on 2012-01-16
Are you able to mount with

```

sudo mount -t ntfs-3g /dev/sdb1 /media

```
?

---

### Post by rennerjack on 2012-01-16
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001e67a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   965458304   482729121   83  Linux
/dev/sda2       965458305   976768064     5654880    5  Extended
/dev/sda5       965458368   976768064     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010879

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1941439184   970719561   83  Linux
/dev/sdb2      1941439185  1953520064     6040440    5  Extended
/dev/sdb5      1941439248  1953520064     6040408+  82  Linux swap / Solaris

```

There it is.

---

### Post by sudodus on 2012-01-16
> **rennerjack said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001e67a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   965458304   482729121   83  Linux
/dev/sda2       965458305   976768064     5654880    5  Extended
/dev/sda5       965458368   976768064     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010879

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sdb1   *          63  1941439184   970719561   83  Linux[/COLOR]
/dev/sdb2      1941439185  1953520064     6040440    5  Extended
/dev/sdb5      1941439248  1953520064     6040408+  82  Linux swap / Solaris

```There it is.
The second drive /dev/sdb seems to contain a big partition with a linux file system, not ntfs. Furthermore is contains a swap partiion, but no ntfs partition is found by fdisk.

Are you sure it is the right drive? Or has something unexpected happened to it?

---

### Post by Double.J on 2012-01-16
Scratch previous command - as sudodus says, there's no ntfs partition :)

Judging by the extended partition swap and ext4 systems with boot flag, I'm assuming you've installed linux on this disk?

OR

Do you have 3 Disks, is there one not showing up?

---

### Post by rennerjack on 2012-01-16
Some background on my issue.

I was merrily going about my stuff one day when my computer completely locked. When I cycled the power, it went to a grub rescue screen instead of booting. I tried to fix the problem by plugging in another, smaller, blank hard drive, installing Ubuntu on that, and getting to my files. But on the original hard drive there is a filesystem that I just can't get too using any tools I've seen after a great deal of internet searching. Furthermore, it won't mount.

That's it in a nutshell.

---

### Post by rennerjack on 2012-01-16
I thought it was ntfs, but I wasn't entirely sure. Probably should have said that in the first place.

---

### Post by sudodus on 2012-01-16
> **rennerjack said:**
> Some background on my issue.

I was merrily going about my stuff one day when my computer completely locked. When I cycled the power, it went to a grub rescue screen instead of booting. I tried to fix the problem by plugging in another, smaller, blank hard drive, installing Ubuntu on that, and getting to my files. But on the original hard drive there is a filesystem that I just can't get too using any tools I've seen after a great deal of internet searching. Furthermore, it won't mount.

That's it in a nutshell.
Probably the beginning and end of your 1TB drive is overwritten. It is hard to know how much (only the partitioning, or also operating system files). There are tools that might save the whole ntfs system for you, if only a little is overwritten. Browse the internet for the following tools:

gpart
testdisk

If those two tools don't work, you can save whatever files were not overwritten with

photorec

but you lose the file names and file system (directory structure). This is hard work, but worthwhile if there were important files. Photorec can save files without any information about partitions and file systems, but the more info its gets, the better it works.

---

### Post by Double.J on 2012-01-16
I'd try once more to mount at /media with```
 sudo mount /dev/sdb1 /media
```
Then check if anything is there with
```

cd /media && ls

```

If you get an  error mounting, I'd recommend running fsck to check the volume for errors:
```

sudo fsck /dev/sdb1

```

---

### Post by rennerjack on 2012-01-16
I tried testdisk and it didn't work.
You say photorec can get my stuff off? At this point I don't care what happens to the hard drive as long as I can get my stuff off first.

---

### Post by Double.J on 2012-01-16
> **sudodus said:**
> 
photorec



+1 if anything else turns up a read error - stop any attempt to read the drive and go straight to photorec before trying anything else - it'll attempt to recover files from the drive by scanning - it'll take an age for 1TB, but will hopefully be worth it. You run it as a live CD just like Ubuntu or gparted

[Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by rennerjack on 2012-01-16
Mirow, I see sdb1 in the output of the second command, but the mount command failed.

---

### Post by Double.J on 2012-01-16
> **rennerjack said:**
> I tried testdisk and it didn't work.
You say photorec can get my stuff off? At this point I don't care what happens to the hard drive as long as I can get my stuff off first.

If testdisk ran into trouble, definately try photorec, Unfortunately is sounding more and more like hard drive failure - it still showed up in fdisk though, so hopefully all is not lost.

Good luck!

---

### Post by sudodus on 2012-01-16
> **gnu/mirow said:**
> I'd try once more to mount at /media with```
 sudo mount /dev/sdb1 /media
```Then check if anything is there with
```

cd /media && ls

```If you get an  error mounting, I'd recommend running fsck to check the volume for errors:
```

sudo fsck /dev/sdb1

```
Since you are not sure about the file system, I agree with *gnu/mirow* that you should try more things before starting with advanced rescue operations. By the way, in order for the rescue operations to work, it is a good idea to have a third drive (for backup and/or place to write rescued files)

---

### Post by rennerjack on 2012-01-16
All right guys, if that's all you have for me, I'll try photorec in 5 minutes.

Thanks for your help! The thing I really love about Ubuntu is that no matter where or when you are there is always an expert who is ready and able to help you! :KS

---

### Post by rennerjack on 2012-01-16
Well Sudodus, I posted that comment before I saw the one you posted immediately before. I will think about this and check for more tools. I'll try to get it running in a mundane fashion for a day or 2 more, if I can't this photorec thing sounds awesome. :p

---

### Post by sudodus on 2012-01-16
> **gnu/mirow said:**
> If testdisk ran into trouble, definately try photorec, Unfortunately is sounding more and more like hard drive failure - it still showed up in fdisk though, so hopefully all is not lost.

Good luck!
Can you check the S.M.A.R.T. status with ```
palimpsest
```

---

### Post by rennerjack on 2012-01-16
The hard drive itself seems fine.
In any case, I've done a lot of computer stuff today, and it's getting late where I am. I'll check this again tomorrow.

---

### Post by sudodus on 2012-01-16
> **rennerjack said:**
> The hard drive itself seems fine.
In any case, I've done a lot of computer stuff today, and it's getting late where I am. I'll check this again tomorrow.
Yes, take it easy, do not rush into something that creates more problems than you have.

I think, in the end you will need photorec, and a big enough third drive for the rescued files. Maybe you can borrow a USB hard disk drive for that purpose.

---

