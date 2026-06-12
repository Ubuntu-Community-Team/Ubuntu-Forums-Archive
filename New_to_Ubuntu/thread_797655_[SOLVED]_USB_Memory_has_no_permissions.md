---
title: "[SOLVED] USB Memory has no permissions"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-17
My 1 gig memory stick has no "permissions". See attached screenshots. I have used GParted in LiveCD session to re-partition the device, but I can't get it to work.

bodhi.zazen had me do this:

sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb -o uid=100,gid=100,umask=007

So the device mounts, but is unusable.

---

### Post by shifty_powers on 2008-05-17
heh, so where are the screenshots?

---

### Post by Mark_in_Hollywood on 2008-05-17
Shifty, here they are, man ... me baddd!

---

### Post by Mark_in_Hollywood on 2008-05-27
I fixed this by putting the device into a Windows XP computer. XP found the device, said it wasn't formatted and asked me if I wanted to format it. I said "YES". Moments later I was able to read/write to/from the usb memory stick/jumpdrive

Thank you to all who have read/responded to this thread.

---

