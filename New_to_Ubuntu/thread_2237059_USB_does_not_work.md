---
title: "USB does not work"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by alexius2 on 2014-07-30
Greeitng I have two problems here;

The USB says I only have 170mb free while I erased all. How can I format it?

My Software Center does not respond, I have to forcefully shut it down.

Is there a way aorund it? 

Can I format the USB without the Center? 

thank you

---

### Post by yancek on 2014-07-30
You can format the usb drive from a system installed on another drive or from a Live CD/DVD or flash drive.  Use GParted.  You can open it is a terminal with: sudo gparted

---

### Post by ajgreeny on 2014-07-30
> **alexius2 said:**
> The USB says I only have 170mb free while I erased all.
It is possible that there is a Trash folder hidden on the USB that still has all the erased files that you mention.

How diid you delete all the files?

---

### Post by alexius2 on 2014-07-30
I just opened disk utility through palimpsest on terminal located the usb, tried to format it and this came out : /dev/sdb is mounted

---

### Post by Vladlenin5000 on 2014-07-30
> **alexius2 said:**
> I just opened disk utility through palimpsest on terminal located the usb, tried to format it and this came out : /dev/sdb is mounted

The question was how did you delete those files, not how you tried to format it... By the way, you can't format a mounted drive.
Now, you don't need to format it but _just empty your trash bin_.

---

### Post by ajgreeny on 2014-07-31
If you can open that USB in nautilus or another file manager, use Ctrl+H to show hidden folders and files.  You may find a lot of hidden stuff in there which you can remove.

Normally a USB will put deleted files into a hidden trash and you are then asked if you wish to empty the trash when you unmount the USB so I am wondering if you always remove the USB safely, or if you simply unplug it, meaning the trash is never emptied.

---

