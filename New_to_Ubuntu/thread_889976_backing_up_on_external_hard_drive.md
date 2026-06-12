---
title: "backing up on external hard drive"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by moonbat% on 2008-08-14
can some one link me to a backing up linux on an external hard drive howto?  ubuntu crashed and i want to use my external for back up.  thanks for the help

---

### Post by Diabolis on 2008-08-14
- Boot up with a live-cd.
- Plug in you external hard drive, it should be mounted automatically.
- Copy tthe files from you old installation to the external drive.

For your next installation I recommend you to make a separate partition for your files.

---

### Post by moonbat% on 2008-08-14
shazam thanks for the help

---

### Post by hrod beraht on 2008-08-14
For general backing-up, I don't think rsync can be beat.
For your situation, probably something like:
```
rsync -r -t -v --progress --delete -b --backup-dir=/media/USBDRIVE/backup/archive /home/moonbat/ /media/USBDRIVE/backup/current/
```

Or, if you prefer a GUI front-end, check the Synaptic package manager for a program called **grsync**.

Bob

---

