---
title: "Module problem..."
date: 2006-09-17
forum: Programming Talk
---

### Post by wibbedw on 2006-09-17
Hi!

I'm trying to write my own driver module, just a simple one that reads and writes to/from the parallel port. The modules works, so I can load and unload it using insmod and rmmod. But the problem's start when I try to use the parallel port. 

If I try to load my module after a boot it complains about the parallel port address 0x378 already being in use. So after checking /proc/ioports I see that the address 0x378 is used by parport0. I then try to unload the modules using that port, namely lp, parport_pc and parport. After doing that my module doesn't complain about the port being used. But if I write anything to the port nothing happens. I have a 7-seg display hooked up to the data lines of the parallel port, so it should light up when I write something to the port.

So I wonder if there are any other modules I need to unload, or anything else Ubuntu specific I need to do to be able to use the parallel port in my own kernel module?

Oh, and I'm using Ubuntu version 6.06 on a AMD 2000+ pc.

Would appreciate any help I could get
/Daniel

---

### Post by amo-ej1 on 2006-09-18
Once I did a similar project the problem there was that the parallel port didn't supply sufficient power to feed the display. Which was mainly a problem on the newer pc's back then while it worked perfectly on older pc's ?  Can you rule this option out ? Is it possible to get an external power supply for your display and test it that way ?

Other than that, perhaps you can first try to access it from userspace and after that from kernelspace ?

---

