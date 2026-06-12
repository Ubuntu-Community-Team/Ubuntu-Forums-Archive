---
title: "Monitoring the parallel port"
date: 2008-04-18
forum: Programming Talk
---

### Post by costre on 2008-04-18
*I posted this elsewhere, but I thought I'd give this forum a shot too*

My question is this:

I'm going to use the parallel port to control a series of lights. It has worked before, in WIndows XP. First I need to see that the software outputs through the parallel port without plugging anything in.

Is there a software that lets me monitor the parallel port(s) to see if there is any data going through as my application is running?

Kinda like this little application: [img]http://www.esc.auckland.ac.nz/mason/Courses/Computer%20Systems/Pictures/parmon.gif[/img]

I ran it in XP, alongside the program controlling the parallel port, and I could see the changes in real-time.

Thanks in advance

---

### Post by nanotube on 2008-04-18
if you are up to playing with python, you could look at 
[http://pyserial.sourceforge.net/pyparallel.html](http://pyserial.sourceforge.net/pyparallel.html)

---

### Post by costre on 2008-04-19
Thanks, but I'm not into programming myself :) 

I went ahead and ordered two parallelport-testers, a small device with diodes that indicate activity over certain pins. Easy to use for testing/debugging purposes.

[img]https://iftools.com/pictures/ledtester25-big.png[/img]

---

### Post by nanotube on 2008-04-22
hm, well, if you are not into coding, i found an oss parallel port monitor: (there may be others as well... i just did a quick websearch...)

[http://www.ucc.asn.au/~steve/](http://www.ucc.asn.au/~steve/)

under the downloads section, he has a parallel port monitor:
[http://www.ucc.asn.au/~steve/dl/parallelPortMonitor.tgz](http://www.ucc.asn.au/~steve/dl/parallelPortMonitor.tgz)

well, the hardware you bought is probably a nice alternative, too :)

---

