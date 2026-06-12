---
title: "Pyserial port closing problem"
date: 2009-07-29
forum: Programming Talk
---

### Post by kentpend on 2009-07-29
I am writing a script to automate instrument control for circuit testing, but if the script crashes it leaves the serial ports open.  I can still open a port to write to it, but can no longer read from it, as though another program still has it open.  The only way I have been able to reliably fix this is to reboot, but I'm pretty sure there is a better way.  Any suggestions?

---

### Post by Sockerdrickan on 2009-07-29
Hey how did it go with the C++ classes?

---

### Post by kentpend on 2009-07-29
Since you apparently missed the title- python, not c++.  Sorry if you love c++ but there is no reason to write this sort of code in a low level language.

---

### Post by Sockerdrickan on 2009-07-29
I didn't misread the title, some other user had a similar discussion about a week ago(?)

Okey must have been a coincidence then, sorry.

[SIZE=1]**Edit**: [http://ubuntuforums.org/showthread.php?t=1219765](http://ubuntuforums.org/showthread.php?t=1219765)[/SIZE]

---

### Post by kentpend on 2009-07-29
Ah... no worries.  I found that thread while hunting for a solution to my serial problem, but found nothing useful in it.  Sadly google searches didn't turn up much useful information either, most likely because I don't know enough about the problem to run an effective search.

---

### Post by Spirail on 2013-02-27
> **kentpend said:**
> I am writing a script to automate instrument control for circuit testing, but if the script crashes it leaves the serial ports open.  I can still open a port to write to it, but can no longer read from it, as though another program still has it open.  The only way I have been able to reliably fix this is to reboot, but I'm pretty sure there is a better way.  Any suggestions?

Did you (or anyone) ever solve this? I'm writing python serial connections and I really need to make sure i can get back onto the ports in cases when there are script faults and the script terminates without closing the port.

---

