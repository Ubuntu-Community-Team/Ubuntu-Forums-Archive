---
title: "External HD Sharing"
date: 2020-08-07
forum: New to Ubuntu
---

### Post by swanysto on 2020-08-07
I attached my external HD an Ubuntu found it right away, however, I am unable to share that drive. Whether through the GUI, or by editing smb.conf files and chmod commands via terminal. I have tried unmounting and mounting. Is Ubuntu not allowed to share HFS+ file system, or am I doing something wrong? I don't really want to format the drive, but if Ubuntu won't share it, I guess I have to.

Any work arounds?

---

### Post by pbear42 on 2020-08-07
Wait for a second opinion, but I expect what you want/need is *hfsplus*.  [http://manpages.ubuntu.com/manpages/focal/man7/hfsplus.7.html](http://manpages.ubuntu.com/manpages/focal/man7/hfsplus.7.html).
Actually, I'm pretty sure you need that.  The question is whether you need anything else, which I don't know as I don't have a Mac.

---

### Post by swanysto on 2020-08-07
So I installed hfsplus. It seems to have gotten me a bit further than before. It is letting me share a folder on my external drive. When I try to access it from another computer, it shows the folder, but does nothing when I double click it. I have set all the options in my smb file, and still nothing. I have a feeling it has to do with the drive being read-only due to the filesytem. I will wait for other replies, but thank you for you help.

---

### Post by ajgreeny on 2020-08-07
I don't really know much about hfs+, but being an apple filesystem you may need to investigate the permissions of the mountpoint of that external disk, probably /media/***username***/***diskID***, though I am suggesting this never having used an hfs+ partition/disk.

NB: My mountpoint will not be exactly as I wrote but will be your username and however the system identifies the disk, maybe its UUID or possibly its label.

---

### Post by swanysto on 2020-08-07
You are correct in the location of the mount point. However, I am unable to change permissions, even in terminal with root.

---

### Post by ajgreeny on 2020-08-08
You say you have installed **hfsplus** but I believe you also need **hfsutils** in order to use hfs filesystems fully.

I missed that earlier, so apologies for the miss if that turns out to be your problem.

---

