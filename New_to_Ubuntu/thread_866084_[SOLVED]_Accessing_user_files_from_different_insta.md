---
title: "[SOLVED] Accessing user files from different installation of Ubuntu"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Doogle999 on 2008-07-21
Hi everyone,

I have two hard drives: Windows XP is on HD1, Ubuntu on HD2. HD1 is much faster than HD2 and I'd like to install Ubuntu on this drive now instead (I'm happy to lose Windows in the process).

I have copied all my user files out of windows to a home dir on Ubuntu on HD2.

My question is this: if I now do a fresh install of Ubuntu on HD1 can I copy my user files from the Ubuntu on HD2? Will I be able to read them because presumably I'll be a different user when logged in on the fresh Ubuntu on HD1?

Hope that makes sense.

---

### Post by mbsullivan on 2008-07-21
Hi Doogle999,

Yes, you should be able to mount HD2 in Ubuntu after booting to HD1. When you mount a drive you are able to set the permissions of the mounted files, such that there should be no problem with what you are trying to do (so long as you have root access).

Mike

---

### Post by Potatoj316 on 2008-07-21
Yes, you will have access to both hard drives while on either instalation of ubuntu.  You will probably have to mount the other drive but thats easy, go to Places->x volume.  You will probably have to put in your admin password before it mounts.  Alternativly you can mount in the terminal
```
sudo mount /dev/hdb1 /MOUNTPOINT
```

you can set mountpoint to whatever you want but make sure that directory exists, I dont know if it has to be empty or not.  If your hard drives are SATA you will have to use sdb1 instead of hdb1

---

### Post by mbsullivan on 2008-07-21
> If your hard drives are SATA you will have to use sdb1 instead of hdb1

Also, if you want to be more sure of what device to use, you may (from the terminal) use the command:

```
sudo fdisk -l
```

This will list all connected drives, mounted or not.

Mike

---

### Post by Doogle999 on 2008-07-22
Thanks guys, installed ubuntu last night and the files copied over no problem!

---

