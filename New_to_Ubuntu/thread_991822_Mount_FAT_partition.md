---
title: "Mount FAT partition"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by simonlugi on 2008-11-24
I have created a FAT32 partition so that I can access files from either windows or ubuntu.
Can someone tell me how I can set up Ubuntu so that it automatically mounts this partition as soon as I log on.

---

### Post by hyper_ch on 2008-11-24
what have you tried so far to find this information?

---

### Post by simonlugi on 2008-11-24
I tried this forum before and got bump. Found a book in the library for Ubuntu 6.06 which suggests that I go into the /etc/fstab and make some changes to the line starting with /dev/hdb1 media/win1.......
Unfortunately this didnt work either .

---

### Post by hyper_ch on 2008-11-24
The forum search isn't that great... better to use google...
Also very good is the ubuntu wiki: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

What suggestions did the book make? what did you alter in the /etc/fstab?

---

### Post by Michael.Godawski on 2008-11-24
There is also a great how-to made by bodhi.zazen about fstab so check it out:


[LIST]
[*][http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)
[/LIST]

It covers many aspects of the mounting process.

---

### Post by ajgreeny on 2008-11-24
Another useful site to look at [here]("http://www.tuxfiles.org/linuxhelp/fstab.html").  I have also found the following examples of lines to add to fstab and for manual mounting useful.

Change partition info (eg /dev/hdb1, etc) and path (eg /media/xxxx) to suit the situation, and make sure either that it exists or you have made the mount point first.

Automount linux partition.  Add line to /etc/fstab:-
/dev/hdb1       /media/linux   ext3    defaults  0  1

Manual mount linux:-
sudo mount /dev/hdb1       /media/linux/ -t ext3

Automount fat32 windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

Manual mount fat32 windows:-
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

Automount ntfs windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Manual mount ntfs windows:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Mount an iso file:-
sudo  mount -o loop -t iso9660 path/to/file.iso /mount/path

---

### Post by simonlugi on 2008-11-26
Thanks for all the suggestions. I have managed to to automount the partition by writing 
/dev/sda2  /media/disk vfat users,rw,owner,umask=000 0 0
in fstab
Its not exactly what I wanted but at least I have the media icon appear on my desktop

Thanks again Siimon

---

### Post by vanadium on 2008-11-26
> Its not exactly what I wanted but at least I have the media icon appear on my desktop

What is not exactly what you wanted? If you tell, we will be able to help you tweaking it the way you want.

I am not sure if you know why you added all the options in /etc/fstab. If you do not know, you should probably just use the options suggested by ajgreeny:

/dev/sda2 /media/disk vfat iocharset=utf8,umask=000 0 0


The iocharset option will make sure that linux handles "strange" characters in filenames correctly. The umask option as specified will make the drive readable and writable by anyone.

---

