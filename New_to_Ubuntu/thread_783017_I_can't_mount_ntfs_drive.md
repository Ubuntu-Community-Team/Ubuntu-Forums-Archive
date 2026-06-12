---
title: "I can't mount ntfs drive"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Twizzle on 2008-05-05
I have just moved an NTFS drive from an XP machine to an Ubuntu machine (8.04 fresh install).

I have tried to mount it by double clicking and get a 'Cannot Mount Volume' error. The details say something about an unclean shutdown and that I can try to force it.

I then did:
sudo mount -t ntfs-3g /dev/sda1 /media/Video -o force

as it recommended but I get:
fuse: failed to access mountpoint /media/Video: No such file or directory.

I typed in exactly what the error box suggested.

The drive had been in a machine that was is S3 standby when I turned it off and removed the drive. Is there any way I can fix this - I don't want to loose the contents!

---

### Post by joshsmith on 2008-05-05
it says:
fuse: failed to access mountpoint /media/Video: No such file or directory.
so there is no such file or directory
you should create it :)
run sudo nautilus, browse to media and create the folder. you cant do it with normal user as it is a system folder, so you use sudo

im sure there is a way to get ubuntu to scan the disk

edit: i asked google
ntfsfix, which is a part of ntfsprogs, may be what you're looking for
of course, you could just unmount the disk safely in windows in the first place, put it back onto windows, then umount properly

---

