---
title: "can't write to USB flasdrive"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by gam01hr on 2012-09-16
1/ if I want copy a file FROM home TO usb0 in nautilus I get Error opening file '/media/usb0/example.pdf': Permission denied

2/ copy FROM usb0 TO home folder is OK

3/ if I run $gksudo nautilus the copying a file FROM home TO usb0 works OK

4/ here is how looks /media before USB is plugged and after that

:) [before USB is plugged]
```
/media$ ls -l
total 36
lrwxrwxrwx 1 root   root      7 May 23 22:25 floppy -> floppy0
drwxr-xr-x 2 root   root   4096 May 23 22:25 floppy0
drwxrwxr-x 2 ubuntu ubuntu 4096 Sep  2 17:01 usb0
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb1
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb2
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb3
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb4
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb5
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb6
drwxr-xr-x 2 root   root   4096 Sep  2 17:01 usb7
```:( [after USB is plugged]
```
media$ ls -l
total 40
lrwxrwxrwx  1 root root    7 May 23 22:25 floppy -> floppy0
drwxr-xr-x  2 root root 4096 May 23 22:25 floppy0
drwxr-xr-x 17 root root 8192 Jan  1  1970 usb0
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb1
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb2
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb3
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb4
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb5
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb6
drwxr-xr-x  2 root root 4096 Sep  2 17:01 usb7
```I use ubuntu 12.04

---

### Post by ajgreeny on 2012-09-16
Where do those usb0 to usb7 folders come from in /media?  Have you got a lot of flash drives (or other usb drives) plugged in, each with its own corresponding folder, or is your usb drive divided into many logical partitions?

Have you added the usb drives to your /etc/fstab file in the mistaken belief that you need to do that to get them to mount?

Finally what is the filesystem type of the usb drive; ntfs, fat32, ext#?  Let's see the output of the command ```
mount
``` with the drive attached (& mounted) and then removed.

---

### Post by coffeecat on 2012-09-16
Judging by this mountpoint:

> **gam01hr said:**
> Error opening file '[COLOR="Red"]/media/usb0[/COLOR]/example.pdf': Permission denied

It looks as though you may have the app usbmount installed. If so, and if you are using the desktop version of Ubuntu, please uninstall it and your problems should go away. usbmount is intended for GUI-less server systems and interferes with the automounting functionality of the GUI desktop.

---

### Post by gam01hr on 2012-10-02
I use ubuntu 12.04.
after "usbmount" is removed still not able automount. Please, how do I reinstall GUI to enable automout.
Or how do I mount  my flashdrive (/dev/sdb1) to /media/usb with user-read-write permissions access

---

### Post by two4two on 2012-11-30
Still no definitive answer?  I have something of the same issue.  Here is my problem:

I once was able to simply plug in a flash drive (for example a  Kingston) and it would be found and identified by the name "Kingston" and automount, and I could access it fully to read, write, unmount (safely remove).

Then one day something changed.  Now when I plug it in it recognizes TWO things:  "Kingston (or whatever)" AND "usb0".  I can't access "Kingston (or whatever)" AT ALL.  "usb0" automatically mounts, but I can only READ from it; I can NOT WRITE to it. Also I can't  unmount it because I am not the owner.  

What happened?

About the time this began I was trying to recover a mac-formatted Seagate usb 1TB drive, so I installed some various software to try to get that ability.  I did recover an image of that drive and was able to carve recognizable files from it.  But now that drive is finally dead.  At least I have the image and recovered files.  But I am left with the problem of NOT being able to write to a flash drive and having it be recognized as both Kingston (or whatever) and usb0.

Please, someone who knows anything about this maybe has some suggestions?

Oh, this is Natty which is not supported any more, so I won't be able to install any updates.  I'd rather not upgrade this OS because it has some software that I rely on in the most important way and can't risk breaking it if the upgrade doesn't go my way.  I have VM installs of other (newer) releases.  I'd just like to get this one fixed somehow.  It is my host OS where VirtualBox runs.

---

