---
title: "[SOLVED] USB-media ownership problem"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by utnubuuser on 2008-09-25
Hello - ...having a bit of a problem with my usb memory stick ownership.

I have a memory stick I've been using to transfer files for use on my 7.04 desktop, and my 7.04 laptop.

Today I installed 8.04 on my laptop, but when I tried to transfer my old files from the usb stick, I lost ownership of the stick. Now I get read-only permission on the stick for either machine.

How do I locate the media in the terminal, and how do I chown it?

Thanks.

---

### Post by nowshining on 2008-09-25
right-click the icon in my computer or whatever - i forgot the exact name 'cause i don't use gnome, and post the path... or try to find a tab where the mount point is shown...

---

### Post by Sealbhach on 2008-09-25
Have you tried 

```
sudo nautilus
```


.

---

### Post by utnubuuser on 2008-09-25
Yeah, so far all I'm getting back is the message that changes can't be made to a read-only stick.

Hardy somehow changed it's status when I plugged it into the laptop.
I'll report the issue to the development team.  I've come across this issue before, I just can't remember where

---

### Post by billgoldberg on 2008-09-25
> **Sealbhach said:**
> Have you tried 

```
sudo nautilus
```


.

please use 

```
gksudo nautilus
```

sudo nautilus can cause serious problems.

---

### Post by utnubuuser on 2008-09-25
alright!!  got read/write back   ..not sure if it's anything I did, or if it was auto-detected properly again.  (Plugged it into a brand new 7.04 install)

Thanks

What's gksudo? ...if you don't mind me askin'

---

### Post by utnubuuser on 2008-09-25
Thanks

---

### Post by billgoldberg on 2008-09-25
> **utnubuuser said:**
> alright!!  got read/write back   ..not sure if it's anything I did, or if it was auto-detected properly again.  (Plugged it into a brand new 7.04 install)

Thanks

What's gksudo? ...if you don't mind me askin'

If you want to launch any gui program as root, use gksudo instead of sudo.

Especially if you launch nautilus as root.

Normally sudo will do fine, but there are some horror stories on the net about people using sudo when you should use gksudo.

---

### Post by utnubuuser on 2008-09-25
ok   ...thanks

---

### Post by utnubuuser on 2008-10-25
Chances are this "ownership" problem was due to an unsafe hardware removal.
I was reading an article yesterday re- Ubuntu on USB, and they stressed always removing the USB-stick properly, ie unmount, eject, etc, because Ubuntu wont recognize USB-media that's been improperly removed.

---

