---
title: "Why are there two xorg processes?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by AncientPC on 2008-04-27
In GG there was only one Xorg process, usually taking up ~200m as reported in top.

Now in HH there are two Xorg processes, each taking up ~150m.  However only one of them is ever using CPU.  Why?

---

### Post by AncientPC on 2008-04-28
I'm back down to a single Xorg process using ~240m.  The only thing significant difference I can remember is switching from binary drivers to open source ones.

---

### Post by Kinst on 2008-04-28
The double-xorg thing is some weird bug I have no idea how to fix with ATI's fglrx driver.

---

### Post by banana989 on 2008-07-01
bump ... I'm having this same problem running the fglrx restricted driver

---

### Post by nowshining on 2008-07-01
are u using fglrx and the drivers from the nvidia site? if so remove one - such as the fglrx one and reboot.

---

### Post by ScarySquirrel on 2008-09-26
I have the same problem.  

     The **fglrx** is the root of the problem, as described in the page linked to by the following:
[http://ubuntuforums.org/archive/index.php/t-465435.html]("http://ubuntuforums.org/archive/index.php/t-465435.html")

     The two processes have the same memory map.
     Linux is starting to annoy me again.  First my wireless card driver, and now this.  :(
     Will it end?

---

### Post by dje on 2008-09-26
I too have the same problem, i believe the open source driver in intrepid (which now supports compiz) will fix the problem

dje

---

### Post by markbuntu on 2008-09-26
This is not really that big of a problem. The two xorgs share almost all the same resources so they are not using twice the memory, more like 10% more. The newer ati cards can actually support 2 separate X servers running in two different monitors so I doubt that ati will be doing anything about it.

---

