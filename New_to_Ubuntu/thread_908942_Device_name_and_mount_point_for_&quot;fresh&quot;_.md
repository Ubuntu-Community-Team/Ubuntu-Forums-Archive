---
title: "Device name and mount point for &quot;fresh&quot; USB pen drive"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Lorin Ricker on 2008-09-03
I recently purchased a generic 8GB USB pen drive (aka memory stick) from a "cheap bin" at my local computer supply store, planning to use it for some simple, non-critical experiments.  When I first physically inserted the pen drive into a USB slot on my HH 8.04 system, Ubuntu did not auto-mount it, and I was unable to find where (if anywhere) the drive was located.

Using lsusb, I could indeed see something:

```
$ lsusb
Bus 002 Device 008: ID 1307:0165 Transcend Information, Inc.
...

``` so I knew that the hardware was at least connecting somehow -- but using just a mount command failed to show that the drive actually was mounted.  All my reading in various Ubuntu "cookbooks" indicated that auto-mounting **should** happen... so why not?

I took the same pen drive to a Windows 2000 system and plugged it in... indeed, Windows auto-mounted it, showing it as drives I:, J:, and K: (why three?!), with the K: apparently as the "real" device.  Looking at its Properties dialog box, I discover that the pen drive is a VFAT, and **has no label**!... Could that be the problem for Ubuntu?  So I create a label, "USB1-8GB" for it, dismount it from Windows, and take it back to my Ubuntu box...

...and insert it again.  Bang!  It now auto-mounts!  Conclusion?  Apparently, in order for Ubuntu to auto-mount a USB pen drive, that drive needs to have a label.  Once auto-mounted, I can then use

```
$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
  ...
/dev/sdf1 on /media/USB1-8GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1111,utf8,umask=077,flush)
```...so now I know:  it's "/dev/sdf1" and it's mounted as "/media/USB1-8GB".  Hooray.

OK, then here's the $64K question -- If I didn't have a Windows system to create the drive's label with, how would I do this on Ubuntu?  I would still have to:

[LIST=1]
[*] Know, guess or figure out where the pen drive "should have" auto-mounted; that is, what/where would I expect it to show up as "/dev/sdXX" and "/media/DriveLabelXXX"?  How can I figure this out if it's not (yet) auto-mounted?
[*] If I knew the answers to #1 above, then what's the next step to label the drive?  Must the drive be formatted with some form of mkfs (mkfs.ext3, etc.) to apply a label?  Or is there a tool which just writes/creates a drive label without (re)formatting the whole drive?
[/LIST]
   Hopefully, this little bit of blundering-about learning will help someone else out.  Everything I've read so far (cookbooks, forum threads, other websites) _always_ seems to  assume that:

[LIST]
[*] the user/reader knows how his pen drive is formatted, including label;
[*] that auto-mounting always works, giving the "/dev/sdXX" and "/media/XXX" mount point information; or
[*] that the user always somehow independently knows exactly what "/dev/sdXX" and "/media/XXX" are for the exercise
[/LIST]
  _But what if you don't_?... Shouldn't Ubuntu provide the tools to ferret this all out easily and directly?  Start with a **blank** USB pen drive... _then what_?

---

### Post by Lorin Ricker on 2008-09-03
Follow-on question to the above:  Let's say that I want to reformat that same USB pen drive, changing it from vfat to ext3.  So I do this:

```
$ sudo umount /dev/sdf1
$ sudo mkfs.ext3 -b 4096 -L usb1-8GB /dev/sdf1
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=usb1-8GB
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
493856 inodes, 1974264 blocks
98713 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2021654528
61 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
$
```But when I try to manually mount it, I get this (and I'm making some noobie error here):
```

$ sudo mount /dev/sdf1 /media/usb1-8GB
mount: mount point /media/usb1-8GB does not exist

```If I physically unplug the drive, and then re-insert it, it auto-mounts just fine, and my next mount command shows:
```

$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
...
/dev/sdf1 on /media/usb1-8GB type ext3 (rw,nosuid,nodev,uhelper=hal)
$
```So, it auto-mounted just fine, and on mount point "/media/usb1-8GB", just as I'd expected.

What's my syntax (or conceptual) error here?  I don't get it... what am I missing?  Thanks!

---

### Post by mc4man on 2008-09-03
> sudo umount /dev/sdf1 When you unmount the drive the mount point is also removed.

> sudo mount /dev/sdf1 /media/usb1-8GB
mount: mount point /media/usb1-8GB does not exist

This is correct, the mount point is only created by reinserting the drive (unless you've created it previously) 

Without an fstab entry then by default the pen drive is mounting to /media/<volume name>. (in other words as part of the auto mount process the mount point /media/usb1-8GB is created.

Everything is working as it should

---

### Post by Lorin Ricker on 2008-09-03
> When you unmount the drive the mount point is also removed.Thank you -- I'd missed this point completely; got it now!
> 
Without an fstab entry then by default the pen drive is mounting to /media/<volume name>. Sounds like an opportunity for a bash script, esp. if one is going to do this alot.  Thanks again, you've got me on the right track!

Now, let me nudge on the other question(s) that started this thread:

> Everything I've read so far (cookbooks, forum threads, other websites) _always_ seems to  assume that:

[LIST]
[*] the user/reader knows how his pen drive is formatted, including label;
[*] that auto-mounting always works, giving the "/dev/sdXX" and "/media/XXX" mount point information; or
[*] that the user always somehow independently knows exactly what "/dev/sdXX" and "/media/XXX" are for the exercise
[/LIST]
  _But what if you don't_?... Shouldn't Ubuntu provide the tools to ferret this all out easily and directly?  Start with a **blank** USB pen drive... _then what_?Any takers/wisdom on this?  TIA!

---

### Post by ediblestarling on 2008-10-08
These questions are relevant to me. I have a drive that worked fine until I did some work with it on a windows computer and I think I may have done something similar. Unfortunately, I have no windows computer available, so if someone could figure out how to set it up via ubuntu, I would tip my hat to you!

---

### Post by drowner on 2008-10-08
Interesting.

FOr the record, I have 2 partitions that have no 'label', and they auto-mount fine (as 20gig media) or something like that.

So i'm not sure if this is ALWAYS a problem - I would have like to have seen what "fdisk -l" thought of it.

---

### Post by Ubuntiac on 2008-10-08
I use unlabled usb sticks all the time.

In a pinch though you can use qparted (*not gparted) to put on a label from memory.

---

### Post by SaintDanBert on 2009-03-04
> **Ubuntiac said:**
> 
In a pinch though you can use qparted (*not gparted) to put on a label from memory.

If you right-click then select properties from the Computer
display of file systems, you see the volume label.
You can edit this label all day long. However, if you try
to close the dialog, you get an error saying roughly,\
"Nyet! rename not supported by backend" or that effect.

Also the nautilus file display has a hard time with
right-click on an installed but unmounted usb something.
If the stick were not mounted, one could alter the name
and automount would use it next mount. Apparently, any click tells nautilus to process a mount cycle on the stick.

This is understandable given the automount dance, but sadly another case where win-doze (win-dose) does something that linux does not do [yet].

~~~ Dan 0;-D

---

### Post by mkvnmtr on 2009-03-04
I have used gparted to format and give a name to usb sticks. It seems I have problems with untitled 1 after mounting it a time or two. It looks to me like the problem is becaust of the space between untitled and 1. The system can't seem to read the empty space.

---

