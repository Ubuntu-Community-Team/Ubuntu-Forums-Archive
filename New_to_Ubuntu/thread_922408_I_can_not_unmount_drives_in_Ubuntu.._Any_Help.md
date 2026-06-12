---
title: "I can not unmount drives in Ubuntu.. Any Help?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by ash235 on 2008-09-17
Whenever i try to unmount the hard disk partitions or drives from Ubuntu, it says " Cannot unmount volume-You are not privileged to unmount the volume 'Media' unmount: only root can unmount"
Even when I login as root with sudo -i it says all the same stuff..
What am I doing wrong if at all??
i even tried giving my account root previlages In the user acc and settings, but it is still not working.. What else do I need to do?

---

### Post by knattlhuber on 2008-09-17
Have you tried

```
sudo umount /media/drivename
```

where *drivename* can be found in the output of

```
cat /etc/mtab
```

---

### Post by -kg- on 2008-12-14
I am having exactly the same problem.  Here is further information:

When trying to unmount volumes from the desktop, I have come up with the following information:

> Cannot unmount volume

You are not privileged to unmount the volume "{Name of Volume}"

Details
{mntent}:line 13 in /etc/fstab is bad
umount: only root can unmount /dev/sdb6 from media/sdb6


And as a further piece of the puzzle: When I launch Nautilus and try to unmount from there (by right-clicking either in the right panel or the tree on the left, I get the message:

> Cannot unmount volume
The volume is not mounted

Even though I know good and well it *is* mounted...I can view the files on the volume and, if it were not mounted, I wouldn't be presented the "unmount" selection in the right-click drop down menu (right?).  I would instead be presented with the "mount" option.

I haven't tried your method yet, knattlhuber, and I will momentarily, but thought some of my information might give you better insight on the problem.  Yes, we can probably use your procedure to unmount volumes, but obviously something is wrong somewhere, and I personally would like to fix the problem, not work around it every single time I need to do it.

Thanks!

---

### Post by -kg- on 2008-12-14
Oh sheesh!  I didn't notice the date of the last post in this thread!

Hopefully someone will come by and be able to give me an answer.  Doing a search for this exact problem only supplied me with 4 threads, and this one was the one that contained my exact problem.

---

### Post by GMachine_24 on 2008-12-14
You need to do as previously suggested, i.e. use sudo and umount in a terminal window followed by the location of the drive to unmount... then you will be prompted for root password and the drive should unmount...


as in


sudo umount /drivename


where the information after the / leads to the drive you want to unmount

This is the only way I've ever unmounted a drive.

---

### Post by knattlhuber on 2008-12-14
When automatically mounting the drive using an entry in /etc/fstab, you should set the 'users' flag. That will allow non-root users to mount/unmount the drive.
As there seems to be a problem with you fstab file, it's probably a good idea to post the content. Please do
```
cat /etc/fstab
```
in a terminal and post the output and we'll take it from there.

---

### Post by Kellemora on 2008-12-14
Wow, I had a similar problem like 3 months ago now, so I don't remember the exact details.

But I do remember when I checked the permissions, they were somehow changed to Nobody and No One.

Seems like it was just a matter of chown (something like 755?) from the root terminal and voila, it was fixed.

This happened before I started making notes on how to fix problems I encountered.  But if you check man chown it should give you the exact code to use to restore your permission to that file.

Also, your fstab could be messed up as previously pointed out!

TTUL
Gary

---

### Post by -kg- on 2008-12-14
OK, here's the dump:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb7
UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sdb8
UUID=14d792bb-fb5f-4f54-ab8a-5c113dfdda72  /home          ext3         relatime                    0  2  
# /dev/sdb9
UUID=232b4464-6725-4c4a-9a93-9922027ffe4c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb6                                  /media/sdb6    ntfs         defaults                    0  0  
/dev/sdb5                                  /media/New Volume  ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdb5                                  /media/sdb5    ntfs         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    ntfs         defaults                    0  0  
/dev/sdb7                                  /media/sdb7    ext3         defaults                    0  0  
/dev/sdb8                                  /media/sdb8    ext3         defaults                    0  0  
/dev/sdb9                                  /media/sdb9    swap         defaults                    0  0  


The rest of it:

> When automatically mounting the drive using an entry in /etc/fstab, you should set the 'users' flag.

I didn't knowingly or intentionally set *all* the drives to automatically mount.  I'm not sure what I did (oh, I'm sure I did *something!*) to accomplish it!

:lolflag:

This will be especially useful information for me.  I have posted to the "  Education Focus Group: Call for Topics" sticky in the Beginner's section and intend to attempt to re-write the hard drive partitioning section a bit for clarification and additional information.

It will take a bit...I'm thinking of a general, over-all partitioning guide with leanings towards Linux rather than a short tutorial on just setting the hard drive up for Ubuntu installation (without even *mentioning* extended partitions!).  I'll have to do some research (some of the stuff I just *know* without even thinking about it) then intend to write up a draft and submit it.

---

### Post by knattlhuber on 2008-12-14
OK, first regarding the error:
Line 13 tries to mount to /media/New Volume. You should rename the that folder/fstab entry to something without a space in the name, like "NewVolume".

To enable users to mount/unmount a drive, change the flag in fstab from defaults (= 'nousers') to 'users'. Also, as the OP already pointed out, check the permissions for the folder you are mounting to (should be 744).

Finally, you have quite a list of partitions in your fstab. It's probably a good idea to label these drives (see link below for instructions). The device names are dynamically assigned at boot time. If you change the boot order of the drives (e.g. by removing a drive) this will screw up the device names and result in the wrong drives being mounted to the wrong mount points.

There is a good HowTo on /etc/fstab options:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

