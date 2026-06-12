---
title: "Parallel port IRQ handling"
date: 2007-06-05
forum: Programming Talk
---

### Post by eckertd on 2007-06-05
Having a tough time with this. 

 I want to track 5V square wave pulses from an external source.  I figured the best way would be to put the signal onto parallel port pin-10 and use an interrupt handler to increment a counter in shared memory.  This is then captured, logged and zeroed by another process/thread so the counting can begin again for another interval.

I had it working with a simulated signal via a nanosleep loop, rather than an interrupt.  I can't seem to get it compiled since I included linux/interrupt.h.

Anyone have experience with interrupt handling?  Any glaring errors in my code?  Thanks!

Doug Eckert
Pennington, NJ

Code and gcc errors attached.

---

### Post by eckertd on 2007-06-05
I don't have linux-source installed, going to install tonite and retry.

---

### Post by Ulix on 2009-04-22
Buddy I have the exact same problem, how you made it, 
ok 
cheers

---

### Post by Craftonix on 2010-01-07
Hello :)

Hello,

I just read :
[http://www.captain.at/howto-linux-kernel-parallel-port-interrupt.php](http://www.captain.at/howto-linux-kernel-parallel-port-interrupt.php)

And try to make it work under : Ubuntu Karmic Koala
Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

I added :
#define SA_INTERRUPT IRQF_DISABLED

SA_INTERRUPT seems deprecated

Further later when i make the :
sudo insmod ./parint.ko

and see what happen in dmesg ... i don't see any IRQ Handler Trace
and in cat /proc/interrupt i see no interrupt

I also try to kill all device attached to IRQ 7
sudo rmod lp
sudo rmod parport_pc
sudo rmod ppdev
 sudo rmod parport
 
I also tested the older version skeleton.c
[http://www.captain.at/howto-linux-device-driver-template-skeleton.php](http://www.captain.at/howto-linux-device-driver-template-skeleton.php)

It does not work better but i see interrupt in cat /proc/interrupt.

Perhaps someone can help me figure out what happens ..

To generate IRQ i have a frequency generator Wired to the right pins of Parallel port.

Best Regards and Happy New Year :P

---

