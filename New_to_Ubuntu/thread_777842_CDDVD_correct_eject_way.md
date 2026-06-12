---
title: "CD/DVD correct eject way"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by kikapu on 2008-05-01
Hi,

I installed 8.04 before 4-5 days and i remember that i had succesfully listened to one of my CDs and also watched a dvd movie (all these on a Thinkpad T61).

But now i am facing the following problem: I insert a CD and listen to it. On /Places/Computer i see "FileSystem" and 'Audio CD".
Ok until now. Now press the Eject button of my CD/DVD and place a dvd movie on it. The Places/Computer, still displays "Audio CD" and i cannot do anything with the just inserted DVD.

Am i have done something wrong ? Do i have to use the "Eject" meny entry from programs or Places menu or is is something else that i can do ? And the "mount" command ?
I checked the entries in Nautilus and all are correct (i mean the actions to be done when a media is inserted).

??

---

### Post by SunnyRabbiera on 2008-05-01
this is why I have the disk mounter applet enabled, so if something does not eject I can just click on a icon and select eject.
to get it just right click a panel (top or bottom, doesn't matter) and select "add to panel"
and scroll down to "disk mounter"
and then go to "add"
this will add it to your panel and when you pop in a disk or something it will pop up on your panel.
the "mount/unmount" commands when right clicking are almost the same as eject, though disk mounting can cause some chaos still (its still an old bug that is still under work)

---

### Post by spiderbatdad on 2008-05-01
This is probably not the perfect solution, but it is possible to have a tiny bash script umount the volume and eject the disk. You could then create a launcher to sit on the panel, so you could just click it from your desktop. I used to use something like that. I did not have to umount...eject was fine, but I did  not have a dvd player, either.

---

### Post by kikapu on 2008-05-01
> **SunnyRabbiera said:**
> this is why I have the disk mounter applet enabled, so if something does not eject I can just click on a icon and select eject.
to get it just right click a panel (top or bottom, doesn't matter) and select "add to panel"
and scroll down to "disk mounter"
and then go to "add"
this will add it to your panel and when you pop in a disk or something it will pop up on your panel.
the "mount/unmount" commands when right clicking are almost the same as eject, though disk mounting can cause some chaos still (its still an old bug that is still under work)

Hmmm...i did what you said, i have this "disk mounter" and i inserted a music cd. I was forced to do a "mount" operation through "disk mounter" and then i open "RhythmBoxMusicPlayer" and do a "rescan media.

This way it is now working but do i have to this all over again for EVERY inserted media on cd/dvd ??

I am pretty sure that when i first installed Ubuntu (8.04), i didn't have to do all this...I was changing media from music cd's to dvd and from dvd to data-dvd and that was it.

is there a chance that i have adjust the wrong way something on my system ??

Thanks for the help!



EDIT: Is there a chance that these commands:
hal-disable-polling --device /dev/cdrom
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

can have strange result to the usage of the CD/DVD ??

---

### Post by kikapu on 2008-05-02
I still not get it. Why i have to do a mount click every time i insert a media in Cd/Dvd ??
There are settings that tell the OS what to do when a media is inserted, e.x. what program to run. If i have to manually do this, these programs (totem,rhythmbox etc etc) are never executed.

There must be a way for the OS to do an "auto" mount when a cd/dvd is inserted...

---

### Post by ethanay on 2008-05-17
> EDIT: Is there a chance that these commands:
hal-disable-polling --device /dev/cdrom
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs


yes, the first one.

run this:

```
sudo hal-disable-polling --enable --device /dev/cdrom
```

to reverse it.  according to [this]("http://www.lesswatts.org/tips/disks.php") our drives should be able to announce media insertion without it, which will reduce laptop power consumption.  but i haven't got it to work, so I keep re-enabling :-/

consider this a bump if anyone has any suggestions to take advantage of the hardware-based notification.

---

