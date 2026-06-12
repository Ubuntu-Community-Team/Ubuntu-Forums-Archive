---
title: "Reverse of: sudo hal-disable-polling --device /dev/scd0"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by kikapu on 2008-05-02
Hi,

i have run this command ans i am facing some problems with the auto-mount of my cd/dvd.

What is the command to undo this one (and put things as they were before this) end enable polling ?

Thanks in advance!

---

### Post by riven0 on 2008-05-02
Try this command: > sudo hal-disable-polling --device /dev/scd0 --enable-polling

---

### Post by kikapu on 2008-05-02
> **riven0 said:**
> Try this command:

a million thanks, it's ok now!

---

