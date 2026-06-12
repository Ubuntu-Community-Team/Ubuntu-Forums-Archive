---
title: "failed command: IDENTIFY PACKET DEVICE"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by expatCM on 2011-09-21
I power on my server and the login prompt appears.  A few seconds later the following lines appear.

```
[  35.040073] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  35.040090] ata1.00: failed command: IDENTIFY PACKET DEVICE
[  35.040098] ata1.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00  tag 0 pio 512 in
[  35.040099]          res40:00:03:00:00:00/00:00:00:00:00/a0  Emask 0x4 (timeout) 
[  35.040110] ata1.00: status: { DRDY }
[  35.040082] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen 
[  35.040098] ata1.00: failed command: IDENTIFY PACKET DEVICE
[  35.040106] ata1.00: cmd a1/00:01:00:00:00/00:00:00:00:00:00/00 tag 0 pio 512 in
[  35.040107]          res40:00:03:00:00:00/00:00:00:00:00/a0  Emask 0x4 (timeout) 
[  35.040118] ata1.00: status: { DRDY }


```

I looked round google and this post (July 29, 2011) is similar but in my case the udev rule is already commented out.
[http://paulphilippov.blogspot.com/](http://paulphilippov.blogspot.com/)

Does anyone know what the error means and how to fix it?

I have a few problems with SATA ports on this motherboard (some have failed), could this be a related event?

---

