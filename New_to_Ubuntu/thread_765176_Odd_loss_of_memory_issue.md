---
title: "Odd loss of memory issue"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Bomberman on 2008-04-24
Hi, 
New to Ubuntu/ Linux and impressed thus far :)
However I have an issue in that the BIOS on my laptop (Fujitsu Amilo-D) reports 640MB of RAM (I upgraded it some time ago). But the laptop seemed to be running Ubuntu nearly as slowly as windows so I thought I'd see why. 
System monitor states I have 218.2MB of memory, whereas sudo lshw states one 256MB made of two blocks of 128MB with a capacity of 384MB :confused:
Any help?

---

### Post by swoll1980 on 2008-04-24
I know it's right in the bios so this seems useless, but just to make sure I would pull the memory and plug it back in see if anything changes

---

### Post by Sef on 2008-04-24
Use the Live CD, on the list of what to do there is a check memory test (memtest86.)  For more info, check the [memtest86]("http://www.memtest86.com/") site.

---

### Post by prshah on 2008-04-24
> **Bomberman said:**
> Hi, 
New to Ubuntu/ Linux and impressed thus far :)
However I have an issue in that the BIOS on my laptop (Fujitsu Amilo-D) reports 640MB of RAM (I upgraded it some time ago). But the laptop seemed to be running Ubuntu nearly as slowly as windows so I thought I'd see why. 
System monitor states I have 218.2MB of memory, whereas sudo lshw states one 256MB made of two blocks of 128MB with a capacity of 384MB :confused:
Any help?

Open a terminal, (Applications-Accessories-Terminal) and post the output of the command ```
free -m
```

---

### Post by Bomberman on 2008-04-24
> **prshah said:**
> Open a terminal, (Applications-Accessories-Terminal) and post the output of the command ```
free -m
```
free -m says;

bomberman@Bomberlap:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           218        214          3          0          1         62
-/+ buffers/cache:        150         68
Swap:          454        118        336

Will check the seating of the RAM after the quite a few hours the upgrade is going to take :)

The LiveCD ran abysmally (I assume due to this very issue), but I'll look at the memtest site.

---

### Post by jmagsho on 2008-04-24
Memtest is the way to go - I used it to successfully identify a bad stick of ram.  Another anomaly I encountered recently was with the BIOS not recognizing the ram properly.   One more thing to try would be resetting your CMOS as per the manufacturer's recommended procedure.  That did the trick for me.

---

