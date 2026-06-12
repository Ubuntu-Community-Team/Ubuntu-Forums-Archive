---
title: "How do I change mount point setting?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by luke949 on 2008-05-21
Hi again.

    I was attempting to auto mount my hard drive upon boot up and I changed the mount point settings on my second hard drive. The hard drive doesn't auto mount and I cannot even manually mount the drive. I get an error saying > Cannot mount volume. Mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/) . I think the problem was that I set my Mount setting to "/media/disk". But upon further research I found out you weren't suppose to put the whole directory, just "disk". So, now I am not sure how to change the mount settings because I was able to change it while the disk was mounted, but not while it was unmounted. Can anyone please explain to me how to change the mount setting? Thank you so much!

---

### Post by Paqman on 2008-05-21
The file containing the mount points is /etc/fstab. Open it up and have a look.

This [guide to fstab](http://ubuntuforums.org/showthread.php?t=283131) contains waaaaay more than you'll need, but the important info you want is that the syntax goes:

[Device] [Mount Point] [File_system] [Options] [dump] [fsck order]

So just find the right device and edit it's mount point to match the folder you want it mounted in.

---

### Post by luke949 on 2008-05-21
Ok I fixed it. I referred to this: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

However I'm still not understanding on how to auto mount this drive upon boot up.

---

### Post by luke949 on 2008-05-21
Ok I got everything covered! I referred to this guide here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

