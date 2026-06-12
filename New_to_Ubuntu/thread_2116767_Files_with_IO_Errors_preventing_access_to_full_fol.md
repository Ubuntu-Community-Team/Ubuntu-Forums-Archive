---
title: "Files with I/O Errors preventing access to full folders?"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by SineSpe on 2013-02-16
So here's the story: I had a hard drive using Win 7 fail on me recently. I was able to salvage my Documents before it failed completely but my Pictures are still stuck on there. As of now, i cannot boot from my HDD, so I burned Xubuntu 12.10 to a CD and booted from there.

When trying to move the files to an external hard drive, i receive the error **"Error when getting information for file '/media/...xxx.mp3' **(or whatever the file happens to be) and it's detailed as an **"Input/output error."**

There's no doubt that this is due to bad sectors on the disk. When commanding dmesg, i receive:
```
end_request: I/O error, dev sda, sector 50748707
Buffer I/O error on device sda3, logical block 2493348
ata1: EH complete
```Thing is, these bad sectors are also preventing me from opening folders. If i try to open a folder with a bad document *directly* in it (not in a subfolder), an error message displays **"Failed to open directory "Folder"** and it's because of the bad file. 

This is preventing me from viewing all the GOOD files. I'm not too worried about these bad files individually, but might there be a way that i can open the folder without putting on the other files at risk?

If there's anymore information you need, let me know. My vocabulary with this stuff is pretty limited.

---

### Post by schragge on 2013-02-16
Do command-line tools from the [ntfsprogs]("http://manpages.ubuntu.com/manpages/precise/en/man8/ntfsprogs.8.html") suite work on your Windows drive? I mean, can you browse those folders with *ntfsls* and see the contents of files from there with *ntfscat*?

---

### Post by SineSpe on 2013-02-16
I may be doing this wrong, but I can write click the folder and click "Open Terminal Here."

This is what is displayed, commanded, and returned:

```
xubuntu@xubuntu:/media/xubuntu/OS/Users/Username/Music/Album$ ntfsls -a
*mp3
NTFS signature is missing. Failed to mount 'song.mp3': Invalid argument
The device '10 Wasteland.mp3' doesn't ave a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

Like i said, i'm very illiterate when it comes to this, so I may be doing it wrong. 
Also, if it's done in a folder with subfolders, this will return:

```

Usage: ntfsls [options] device
[INDENT]-a, --all            Display all files
-F, --classify     Display classification...
```

[/INDENT]Etc..

---

### Post by schragge on 2013-02-16
Yes, you're doing it wrong. You should specify **device** as argument for ntfsls. To get the device name of your Windows drive, try
```

findmnt -no source /media/xubuntu/[color=green]OS[/color]

```
That should be something like */dev/sda1*. When you know the device name, do
```

ntfsls -p Users/Username/Music/Album /dev/sda[color=green]1[/color]

```
[highlight]Update.[/highlight]
No need to go to the folder in file manager. You can simply launch the terminal (**Ctrl**+**Alt**+**t**) and issue the commands. Your Windows drive can even stay unmounted.

---

### Post by SineSpe on 2013-02-16
Alright, so these are the results...

```
findmnt -no source /media/xubuntu/OS
/dev/sda3 
```

```
ntfsls -p Users/Username/Music /dev/sda3
Access is denied because the NTFS volume is already exclusively opened.
The volume may already be mounted, or another software may use it which 
could be identified for example by the help for the 'fuser' command.
You can use force option to avoid this check, but this is not recommended
and may lead to data corruption.
```

I thank you ahead of time for your patience with me. :oops:

---

### Post by schragge on 2013-02-17
I never used a LiveCD for any Ubuntu flavor, thus I'm not sure how it works. I guess it mounts your Windows drive when you click on it in the file manager. Then don't do it.

You also can try the *--force* option of *ntfsls*, it should be safe because *ntfsls* doesn't change anything on the drive.
```

ntfsls -fp Users/Username/Music /dev/sda3

```

---

### Post by SineSpe on 2013-02-22
I attempted to force it but i got...

```
Forced to continue.
Error opening '/dev/sda3': Permission denied
Failed to mount '/dev/sda3': Permission denied 
```

---

### Post by varunendra on 2013-02-23
Since your disk contains bad sectors, which may get worse with each attempt to access files, I suggest you create a partition image first using testdisk.

You can install and run it from the live session, and use it to store the image on an external drive. Later you can use the same image with testdisk/photorec to recover files from it. To install -
```
sudo apt-get install testdisk
```
On a live session, you may have to run apt-get update before running above, while you are connected to internet.

To run it-
```
sudo testdisk
```

The image option is under 'Advanced' option of testdisk.

Testdisk Image creation guide - [http://www.cgsecurity.org/wiki/Image_Creation](http://www.cgsecurity.org/wiki/Image_Creation)

**PS:**
By the way, you need to use 'sudo' with ntfsls command to get exclusive lock to the partition. But I don't think it would do anything more than what thunar (the file manager in xubuntu) is already doing for you - that is - listing the directory/partition contents as much as possible.

I don't have extensive knowledge about these file managers, but I do know that they use the same or better utilities in the background to give you access to certain filesystems.

So if normal terminal commands can't access the files, then ntfsprogs commands won't either.

In any case, it is best that you create an image, then you can safely try whatever you want.

---

### Post by SineSpe on 2013-02-23
The link you posted doesn't seem to be available for me on either of my computers.. Although i haven't been able to get wireless working on the laptop running Xubuntu, i was able to install testdisk using an ethernet cable. 

```
Select a media:
>Disk /dev/sda - 320 GB / 298 GiB - ST9320325AS
>Disk /dev/sr0 - 726 MB /693 MiB (RO) - Optiarc DVD+/-RW AD-7700H
```I'm still trying to get that link you posted to load...
How do i know if the listed disks have the correct size?

EDIT: I was able to load the cached version of the link you posted. I was able search for partitions and this is what i received:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1     4 254 60      80259 [DellUtility]
 2 P HPFS - NTFS              5  25 21  1917  84 23   30720000 [RECOVERY]
 3 P HPFS - NTFS           1917  84 24 38913  48 31  594338480 [OS]


 [  Quit  ] >[Deeper Search]  [ Write  ]
                          Try to find more partitions

```

None of these are listed as specific partitions, but am i okay to Write?

---

### Post by varunendra on 2013-02-24
Yes, the server at cgsecurity was down the moment I posted the link, but I was confident with the link so posted it anyway. It is working now, sorry for any inconvenience.

However, you do not need to do this-
> **SineSpe said:**
> None of these are listed as specific partitions, but am i okay to Write?

That option is meant for recovering lost partitions, while yours are already accessible.

You have to use testdisk only for image creation, and later, if other attempts fail, use photorec which is part of the same testdisk package to recover files.

So precisely, I referred testdisk only for imaging - to be extra safe. Let me know once the image is created, or if you need help with that.

To just copy the data whrever possible, there are many tools, of which "safecopy" (commandline utility) seems most straightforward to me. But I haven't ever tried it myself, so can't say how reliable it really is.

---

### Post by SineSpe on 2013-06-12
Sorry for how long it's taken me to get back. The semester was really busy so I had to put off this project til the summer.

I have a new computer now, but i'm still working on recovering my files from this old one.
I'm currently creating an image that's being copied to my 1TB external harddrive. It's been going for a few hours and only at about 55.90% -- is it normal to take so long?

---

### Post by SineSpe on 2013-06-12
So the Image Creation just finished, but it reads:

```
Image created successfully but read errors have occurred.
```

What exactly does this mean?

---

### Post by varunendra on 2013-06-15
> **SineSpe said:**
>  It's been going for a few hours and only at about 55.90% -- is it normal to take so long?
Yes that's normal.
That imaging process uses "dd" which does a block-by-block copying of the drive/partition, regardless of whether the block is used or empty (on a corrupt filesystem, you can't predict which blocks are/were used and which ones not). Hence the copying is slow and the size of the resultant image will be almost exactly same as the partition/drive itself (all the blocks + some overhead, descriptors etc.).

> **SineSpe said:**
> So the Image Creation just finished, but it reads:

```
Image created successfully but read errors have occurred.
```

What exactly does this mean?
It means there were bad blocks found during the copy process. That is normal while copying a corrupt or crashed partition or drive. The resulting image can still be mounted as a drive and will be read as the source drive/partition itself. The scanning program will either try to recover, or ignore the error blocks just as it would have done on the source physical drive.

Let me know if you are still on it and need help.
I've totally lost the context, so you may have to refresh it for me again, plus, details of new developments of course if there are any. :)

---

