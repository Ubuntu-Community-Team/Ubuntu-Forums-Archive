---
title: "Permanently mount partition"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-04-29
Hi,

I have my hard disk divided into 2 partitions:
Ubuntu 
Files (pictures, videos etc ..)

In Gutsy Gibbon, the second partition was mounted at boot and appeared on the desktop.

In Hardy Heron, I must always click on Places -> Files, then the partition appears on the desktop.

Is there any way to change this so that it gets mounted automatically (like in Gutsy)?

Thanks in advance

---

### Post by Joeb454 on 2008-04-29
Hi there,

Is the 2nd partition an NTFS partition or another ext3?

---

### Post by Jim_in_Germany on 2008-04-29
Hi,
The second partition is an NTFS partition.

---

### Post by Sjovan on 2008-04-29
Well... If the HD is on palce --> files, then it's mounted... look in gconf-editor, maby something have changed there so the HD isn't showing.

---

### Post by hyper_ch on 2008-04-29
if you want it to read/write-mount then you have to use ntfs-3g

---

### Post by Joeb454 on 2008-04-29
Unmount the partition, then install ntfs-config.

You can use the terminal to do this by ```
sudo aptitude install ntfs-config
```

Then run it from Applications>System Tools :)

---

### Post by Jim_in_Germany on 2008-04-29
Thanks for the replies,

I have to shoot out for a while, but I will try looking in gconf-editor / trying out ntfs-config when I come back and I will post back here if I have any questions. Thanks for that.

@hyper_ch:
Ubuntu seems to mount ntfs partitions for read/write access automatically. How good is that?
:-)

---

### Post by hyper_ch on 2008-04-29
it shouldn't mount with read/write automatically... just as read.

---

### Post by Jim_in_Germany on 2008-04-29
But it does.

---

### Post by Jim_in_Germany on 2008-04-29
Back again,

So, installing ntfs config solved the problem.

Now when I turn on the computer my second partition is mounted for read/write access and has an icon on the desktop.

Thanks for the help.

P.S. As I am new to Linux and interested in finding out what is where, could someone tell me what gconf-editor does and where I can find it to have a look at it.
Ta

---

### Post by Sjovan on 2008-04-29
> **Jim_in_Germany said:**
> Back again,
P.S. As I am new to Linux and interested in finding out what is where, could someone tell me what gconf-editor does and where I can find it to have a look at it.
Ta
gconf-editor does alot of things my friend. Everything from telling what prog to use when i ipod is detected to telling your system that you don't want to se any HD on your desktop.
open termianl --> gconf-editor <-- if you want to have a look. Don't play around to much :)

---

### Post by Jim_in_Germany on 2008-04-30
That's cool.
Thanks a lot.
I'm messing around with it now and it does in fact have quite a lot of options for the handling of ntfs partitions.
No idea what any of them mean yet :-)
Thanks again.

---

