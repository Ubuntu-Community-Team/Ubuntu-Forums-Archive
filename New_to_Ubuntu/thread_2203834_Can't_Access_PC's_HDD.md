---
title: "Can't Access PC's HDD"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by bryan15 on 2014-02-05
Hi, I just installed Ubuntu 13.10 on my Seagate Drive after I got into some problems booting my Windows 8.1.

But now I only can access the external drive, but not the PC's HDD (C:\), nor its partition (E:\)

The following message comes out when I try to open Acer (C:\)

Error mounting /dev/sda4 at /media/ubuntu/Acer: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubuntu/Acer"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

And when trying to open GA Management Services (E:\)

Error mounting /dev/sda6 at /media/ubuntu/GA Management Services: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda6" "/media/ubuntu/GA Management Services"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I thought I could somehow fix my Win8.1 if I used Ubuntu but now I can't even get into the HDD. Any help would be appreciated. Thanks.

---

### Post by vitz_3 on 2014-02-05
Hi there bryan, welcome to the forums! :)

The reason you're seeing this problem is because there might be disk problems with the hard drive. Most likely nothing serious, or anything considerable to worry about. Basically all that needs to happen is a quick(ish) disk check on the device. When an NTFS type partition is modified or not properly unmounted the disk gets marked as unclean more or less.

You can simply boot into your Win 8 install and do a disk check on the hard drive or you can do it from within Ubuntu. Just for consistency I'd recommend doing it within Windows 8. It might even prompt you to do it when you boot into it. Let it finish and you should be good to go.

I found an Ask Ubuntu post somewhat related to your problem you can reference [here]("http://askubuntu.com/questions/290630/problem-to-enter-in-ntfs-partition").

Cheers!

Edit: 
Just read that you can't boot into Win8, sorry. Try the fix mentioned on the Ask Ubuntu post.

---

### Post by Vladlenin5000 on 2014-02-06
You can't access the Win8 system HDD unless you did a full shutdown in the last time you used Windows 8, just like the error message says ("no hibernation or fast restarting"). The default for Windows 8 is the opposite and that has been discussed *ad nauseum* all over the interwebs.

Bottom line: Ubuntu can't help you with that.

---

