---
title: "No sound after BIOS RESET, (UBUNTU 9.04)"
date: 2009-10-15
forum: Philippine Team
---

### Post by upbeatfury@yahoo.com on 2009-10-15
Hi,

I encountered a problem on my Ubuntu 9.04 after reseting my bios.
My linux now doesnt have any sound, i tried to confugure ALSA and still the sames issue.Tried changing through sound preference and alsa mixer still same after reboot(no sound). 

ANY ADVICE?


Thanks in Advance,

---

### Post by loell on 2009-10-15
is there an integrated sound option on your BIOS settings?

---

### Post by upbeatfury@yahoo.com on 2009-10-16
yes, there is and it is enabled and working on my other OS. i have 5 OS's inside my single drive, and the only one that has an issue is my ubuntu 9.04. any advice sir?

---

### Post by upbeatfury@yahoo.com on 2009-10-16
Can i reinstall alsa driver?

---

### Post by loell on 2009-10-16
try disabling the BIOS' Integrated Sound, then check if it can now restore Sound in Ubuntu 9.04

the driver is a module in the kernel, if you suspect that the module  is doing something wrong, probably just try older kernels in your Grub entry, see if sound can work there. :)

---

### Post by upbeatfury@yahoo.com on 2009-10-18
Thanks for the advice, But i've already fixed it this morning.!It is working now really good. ^^

---

