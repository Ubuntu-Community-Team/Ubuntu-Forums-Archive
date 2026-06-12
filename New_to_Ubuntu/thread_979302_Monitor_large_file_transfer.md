---
title: "Monitor large file transfer"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by lmlypfan on 2008-11-11
I'm moving about 300 Gigs of data from one hard drive, to a RAID array.
I've already initiated the command to move the data, but i would like to monitor its progress. 

Is there a command for this?

---

### Post by maxhax on 2008-11-11
You could try 

> watch -n 1 '[ls -alh destination]'

---

### Post by ghost_ryder35 on 2008-11-11
top

---

### Post by lmlypfan on 2008-11-11
top just shows my processes, but doesn't show the progress of the file transfer. am i missing something? 

this gives me a scrolling "permission denied", even w/ sudo ```
watch -n 1 '[ls -alh destination]' 
```

The transfer is complete now, but would still like to figure this out.

---

