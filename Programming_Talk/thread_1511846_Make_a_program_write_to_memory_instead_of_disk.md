---
title: "Make a program write to memory instead of disk"
date: 2010-06-17
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-17
I have a situation where I have to use external code that I cannot modify and which writes output to disk that I would much rather have stored in RAM.  Is there a way to convince the program to output to a "file" that actually lives in memory?  (It is written in Fortran)

---

### Post by DanielWaterworth on 2010-06-17
You could mount a ramdisk then get it to write to there.

---

### Post by gvoima on 2010-06-17
Yeah, unless you can modify the source, make a ramdisk.

---

### Post by DanielWaterworth on 2010-06-17
This will mount a ramdisk at /mnt/:

sudo mount none /mnt -t ramfs;
sudo chown $USER:$USER; # change ownership

---

### Post by Zorgoth on 2010-06-17
Thanks!  Got it

---

