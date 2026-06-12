---
title: "How do I find the path to an external drive?"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-18
I'm trying to reset permissions for an external. I've been using the external on a Mac, but now I want to change permissions so I can use it on an Ubuntu machine. 

On my Mac, the drive shows up with the name I gave it: VelaNoche 

On Ubuntu, it shows up as: 1.0 TB 

I'm a little worried that the (Ubuntu designated) drive name is going to cause problems when I list it in a path, due to it having a period in its name. 

Is there a way to see, in terminal, the complete path name by doing a search for the drive (using the drive name, I assume)? 

Many thanks, 
Joel

---

### Post by winh8r on 2012-03-18
Open a terminal and enter 

```
df -h
```

you should see the name of the drive listed there


OR

open Disk Utility

and rename the drive.

---

### Post by chipbuster on 2012-03-18
I believe the name in the GUI browser is usually that given by the label on a particular partition.

The drive itself should be found in /media. Just do an ls /media and find the one that looks right (or look into all of them)

---

### Post by jps2012 on 2012-03-18
Thank you, winh8r and chipbuster. That looks pretty straightforward. I appreciate the help.

Joel

---

