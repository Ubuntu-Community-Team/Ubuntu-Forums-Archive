---
title: "Disable Routine Check of drives"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by vashwood on 2008-06-03
I'm using ubuntu as a headless server and it gets annoying when I try to WOL my box and I can't connect to it because of the Routine Check of drives.  Is there anyway to disable it?

---

### Post by KingTermite on 2008-06-03
If you're talking about what I think you are, then a command "tunefs" is supposed to be used to set/change it. I've never used it, just read about it.

---

### Post by Arthur Archnix on 2008-06-03
In /etc/fstab just change the last number to a zero for all drives you want to disable the check on. Probably not a good idea to completely disable unless you're willing to setup a cron job or something to manually fsck the drives when not in use or once a month or something.

---

### Post by isparkes on 2008-06-03
tune2fs

```
tune2fs -c 50 -C 1 /dev/yourdevice
```

sets it up so that it does the check every 50 times, and sets the current count to 1. I tend to set all drives at the same time so that when it does happen, I know that I can go for a cup of tea...

---

