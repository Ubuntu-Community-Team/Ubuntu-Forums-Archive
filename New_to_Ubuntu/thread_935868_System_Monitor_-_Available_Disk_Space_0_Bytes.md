---
title: "System Monitor - Available Disk Space: 0 Bytes  ??"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by nutkin on 2008-10-02
System Monitor reports under the System tab that I have Available Disk Space: 0 Bytes.

What does this mean? I've seen screenshots of other people's where theirs is over 200 megs. I installed Ubuntu using Wubi. So far it's been running slower than WinXP.

Firefox 3.0.3's memory usage also bloats up to over 200 megabytes but that might be a separate topic. 

Any help would be appreciated.

Thumbnails below are screenshots of system monitor.

[[IMG]http://img206.imageshack.us/img206/2126/sysstatusxj9.th.jpg[/IMG]](http://img206.imageshack.us/my.php?image=sysstatusxj9.jpg)[[IMG]http://img206.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img528.imageshack.us/img528/7857/sysstatus2gs3.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=sysstatus2gs3.jpg)[[IMG]http://img528.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Calmatory on 2008-10-02
This might somehow be Wubi related issue, but I'd assume it is a bug. It shows something it shouldn't, at least if believing the second picture you posted. While it seems odd, I wouldn't be too concerned about it really. Then again, I might be too ignorant to see the real problem, but thats just me. :)

---

### Post by nowshining on 2008-10-02
what version of ubuntu are u using? do u have all available updates?? Have u restarted the computer yet??

---

### Post by nutkin on 2008-10-02
Sorry I wasn't more clear. I installed Ubuntu using Wubi over a month ago and have been using it regularly since. Everything's updated and it's the latest version of Ubuntu (8.04 Hardy) which is mentioned in the system monitor picture.  However, Ubuntu's been rather slow and I've been rather disappointed with it due to that fact. I wasn't sure if it's supposed to be or not which is kind of the point of this thread. I noticed the system monitor saying that I had Available Disk Space: 0 byte which seemed odd to me and might have been the reason why it's running slow? I don't know. If everything looks in order, I can look elsewhere. Suggestions would be appreciated too. :)

---

### Post by Calmatory on 2008-10-02
Well, doing a fresh install from a LiveCD could do wonders. Or not. At least it would be a new experience towards Linux if you like Ubuntu. I'd just wait until 8.10. :)

---

### Post by nowshining on 2008-10-02
> **nutkin said:**
> Sorry I wasn't more clear. I installed Ubuntu using Wubi over a month ago and have been using it regularly since. Everything's updated and it's the latest version of Ubuntu (8.04 Hardy) which is mentioned in the system monitor picture.  However, Ubuntu's been rather slow and I've been rather disappointed with it due to that fact. I wasn't sure if it's supposed to be or not which is kind of the point of this thread. I noticed the system monitor saying that I had Available Disk Space: 0 byte which seemed odd to me and might have been the reason why it's running slow? I don't know. If everything looks in order, I can look elsewhere. Suggestions would be appreciated too. :)

the pics were too small for me to read and the .gif ones didn't show up...

---

### Post by halitech on 2008-10-02
If you used WUBI, then you don't have a true ubuntu install and instead have it installed in a file on the windows hard drive so it might be giving some false readings on hard drive space.

---

### Post by cariboo on 2008-10-02
I don't know if it will make a difference, but you didn't format your boot partition according to the image you posted. I don't like graphical representations of disk usage. Could open up a terminal and type:

```
sudo fdisk -l
```

and 

```
df -h
```

Jim

---

### Post by jerome1232 on 2008-10-02
I happen to have a wubi install on one laptop and it reports the same type of thing. It is inaccurately reporting the available space on that tab.

Wubi does have reduced performance when it comes to disk access but otherwise it shouldn't suffer performance wise. Mine preforms better than Vista does on this laptop at least.

---

