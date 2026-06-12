---
title: "nvidia driver and wireless, how are they connected?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by jlbr21 on 2008-11-03
I installed intrepid through a Wubi installation in my new laptop, an HP div5 1095, intel centrino 2, and with an nvidia geforce 8600. I installed 8.10 just to try it out in this new machine. So one of the first things I do is to activate the nvidia driver, the 177 version, (since the one I downloaded from the nvidia webpage did not work, first it told me i was running a 32 bit version of ubuntu, then i tried again and told me i was running an X server!!! WTH!!), and so I activate the driver and upon restart the wireless is gone. I deactivate the driver and wireless is on again...

Any suggestions or advice on what to do? I am a bit confused and can't keep up with the nvidia card and Intrepid issue and their discussions in the forums.

Thanks in advance.

---

### Post by spydon on 2008-11-03
You are probably running the 32-bit version of ubuntu and you are definitely running a x-server on it, almost everybody(99,99%) of all people that has some kind of graphical interface on their linux distro runs the x-server. What does the network-manager show when you have the nvidia driver activated?

---

### Post by jbrown96 on 2008-11-03
Which intel card do you have 3945abg or 4965abgn? Could you post the output of the following commands when the driver is enabled and disabled (please indicate the status of the driver) ```
ifconfig
``` ```
iwconfig
``` ```
lsmod
``` To get to a terminal: Apps-->Accessories-->terminal

---

### Post by igknighted on 2008-11-03
I have a centrino2 and it's a 5100, so that's what I would guess OP has.  I don't have nvidia though, and don't have any issues like the OP has.

---

### Post by jlbr21 on 2008-11-03
OK, now it works, the simple solution is always the one, I just installed the version 173 of the driver and it worked like a charm.

Thanks you all for your help!

---

### Post by spydon on 2008-11-03
But still, I can not understand how the graphical driver can affect the wireless one... :???:

---

