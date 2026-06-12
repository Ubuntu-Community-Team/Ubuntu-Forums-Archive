---
title: "laptop is restarting continuously"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by pradeepkaruturi on 2008-08-19
I resized my C drive(vista) using ubuntu live cd(gparted) and moved this drive to the right on the harddrive 
now when i restart my laptop it is continuously restarting..
donno what to do..
I dint yet install ubuntu in it.
thanks in advance...

---

### Post by cdtech on 2008-08-19
You should resize Vista through Vista only. You'll need to boot with your recovery disc and repair that way. I would suggest repairing this issue before attempting to install Ubuntu.

---

### Post by starcannon on 2008-08-19
At this point you should do what ctech said as you either need to fix the mbr of the hdd for windows, or go ahead and install ubuntu and let grub do the job. You likely put windows on a "second" partition when you moved it to the right, it likes to be on the first. Linux is happy anywhere you put it.

Normally the best thing to do is to just shrink the windows partition, not move it. Then install Ubuntu to the empty space. I'm not sure if just installing ubuntu will fix your boot problem at this point or not. But I'd probably try that first. No guarantees though. 

GL

---

