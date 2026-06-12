---
title: "[SOLVED] Help: hdd disappeared!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by BeccyBug on 2008-08-11
Hi

I posted a problem a couple of days ago, that a second hdd couldn't be monted (see [here]("http://ubuntuforums.org/showthread.php?t=885008&highlight=Mount") that was seemingly solved at the time.  Now a few days later, I'm after stuff stored on this drive and it's nowhere to be found.  This could be just because I'm a noob and am not looking in the right places, but as far as I know I've looked everywhere!

When the problem was solved the console did return a warning (which I ignored at the time since it seemed to have worked!):
$LogFile indicates unclean shutdown (0, 0,)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Backup: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Backup)

any ideas?  it is an old seagate hdd -ntfs - only about 700Mb bit does have the latest edition of open office that I wanted to install without wiping out my 1G a month download limit!

Any help much appreciated!

---

### Post by hyper_ch on 2008-08-11
boot into windows so that it fixes the ntfs journal.

---

### Post by Bölvaður on 2008-08-11
Warning, this might not be related to your problem.
This sounds a little bit different from my problem with ntfs portable hard disks.

But I had big problem with people on windows not unmounting the devise correctly, they only took the usb cable out. The easiest way to fix this is just to unmount it properly in windows with the Remove Hardware option.

But this is only after a windows system fails to unmount the disk before disconnecting it. So if you only uses it for your linux pc, this should not be the problem.

---

### Post by BeccyBug on 2008-08-11
Both right - I hadn't shut down the computer properly before I installed ubuntu - I removed the hdd and installed it in my xp machine, and from there have shared it (easier to share from windoze).

Thick attack, though - the whole thing was a pointless waste of time, since the open office I had downloaded was a windoze version, so presumably won't be that compatible with ubuntu?!  :lolflag:

Thanks though - I had also had problems with usb flash drives not being recognised by ubuntu, due to not being properly ejected from xp

---

