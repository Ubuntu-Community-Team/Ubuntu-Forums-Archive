---
title: "Problem with /dev/dsp"
date: 2011-02-12
forum: Programming Talk
---

### Post by Aqlor on 2011-02-12
Hey again guys,

I wanted to test some really interesting code I found online on [http://www.arachnoid.com/signal_processing/fft.html](http://www.arachnoid.com/signal_processing/fft.html)

At one point the program uses /dev/dsp1 and as far as I know, this isn't being used in a while so an error pops as expected.

Is there any other way to get the audio input values such as easily?

Before, we could get the input just by doing "cat /dev/dsp" right? If we wanted to do something similar to that now, what should we do?

Thanks, 
Levi

---

### Post by eeperson on 2011-02-13
You can get back the '/dev/dsp' file by installing the 'oss-compat' package.

---

### Post by Aqlor on 2011-02-13
Already had it installed:


levi@laptop:~$ sudo apt-get install oss-compat 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oss-compat is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

the problem continues :S

---

### Post by Zugzwang on 2011-02-13
@OP: Do you also have the package "alsa-oss" installed?

---

### Post by Aqlor on 2011-02-13
I have it too...

> levi@laptop:~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.


---

### Post by The Cog on 2011-02-13
Try starting your program with the prefix aoss. This fixed ut2004 for me in Ubuntu 10.10. So instead of:
**ut2004**
I run
**aoss ut2004**
The error message I get without aoss is that it can't find /dev/dsp.

---

### Post by Aqlor on 2011-02-13
Thank you The Cog, I'm marking this solved :D

---

### Post by mandza on 2012-06-30
Thank you The Cog again, this was helpfull for me too.

---

