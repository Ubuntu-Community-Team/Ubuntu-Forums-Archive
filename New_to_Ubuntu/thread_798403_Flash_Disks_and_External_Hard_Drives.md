---
title: "Flash Disks and External Hard Drives"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by MattGEri on 2008-05-18
Hey all,

I am trying to get my western digital external hard drive to mount as well as my usb memory sticks.

How do I get them to work? When I plug them in nothing happens :confused:

Thanks for any help!! :guitar:

- Matt

---

### Post by hyper_ch on 2008-05-18
once you plugged them in, run

```

lsusb

```

and post the output here

---

### Post by MattGEri on 2008-05-18
Hey,

Here is the output:

```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Thanks,

Matt

---

### Post by hyper_ch on 2008-05-18
oh, it is not connected at a USB port?

---

### Post by MattGEri on 2008-05-18
Both the external hard drive and usb stick are plugged in :S

---

### Post by hyper_ch on 2008-05-18
strange that they don't show up

---

### Post by brujoand on 2008-05-18
Try rebooting with the disk plugged in, that should help find it.

---

### Post by MattGEri on 2008-05-18
Will give this a go now and see what happens :)

---

### Post by MattGEri on 2008-05-18
Just restarted and still nothing is showing up..

---

### Post by hyper_ch on 2008-05-18
can't help you then

---

### Post by brujoand on 2008-05-18
Then I'd say some hardware is broken, either the disk or the usb bus. But maybe someone else has a good idea?
sry mate

---

### Post by MattGEri on 2008-05-18
Hmm.. They were working on windows just before I installed Ubuntu.. :( Thanks for you help.

Anyone else have some ideas?

---

### Post by MattGEri on 2008-05-18
(There is also power coming out of the USB ports as the lights go on and my coffee warmer works ;) )

---

### Post by adamgram on 2008-05-19
I have the same problem. Same situation (works on windows partition), same outputs.  Assistance requested.  I can return the favor in the form of online guitar lessons.  Thank you.

---

### Post by adamgram on 2008-05-19
correction: USB drive does not work on windows partition because windows partition boots to the "Blue Screen of Death" However...

USB drive does work (in other computer with windows)
USB port does work (with USB mouse)

lsusb output with USB drive
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lsusb output with USB mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

