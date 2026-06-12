---
title: "windows 2003 vmware guest on Ubuntu - setting up printing"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by greavette on 2008-05-16
Hello,

I was thinking of installing windows 2003 within vmware server on ubuntu hardy.  The windows 2003 image needs to have access to a local printer.  

If the printer is networked (connected to a switch or router), would I need to use cups on ubuntu to have the windows image access the printer?  

What if the printer wasn't networked and was connected directly to the PC running ubuntu via usb, would I need cups to use the printer, or could I just setup the printer in the windows 2003 image?

Thanks in advance for your help!

---

### Post by cprofitt on 2008-05-17
No the WIndows 2003 VM should have access to the local printer -- I assume it is USB.

---

### Post by greavette on 2008-05-17
Yes, this is a USB printer.  

That's great news!  I didn't want to add confusion to their network if the printer is not working and then having to fix something in CUPS.  The Ubuntu Host does not need to use this printer either so I will just install the printer in the virtual image and let Windows use it.

Thanks so much for helping me!

---

