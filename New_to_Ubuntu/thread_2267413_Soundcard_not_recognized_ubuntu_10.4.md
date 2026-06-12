---
title: "Soundcard not recognized ubuntu 10.4"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by laura14 on 2015-03-01
Hello,

I am new to Ubuntu and I need some help. 
My soundcard is not recognized by ubuntu 10.4 LTS.  The soundcqrd is:

00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
    Subsystem: Hewlett-Packard Company Device 1948
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d0a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

Could someone please help me? 

Thank you in advance.

---

### Post by grahammechanical on 2015-03-01
The last release of Ubuntu 10.04 was 10.04.4 on 14 February 2012. If your computer hardware is newer than 2012 then it may be that the Linux firmware that comes with comes with the Linux kernel in 10.04.04 cannot recognise the hardware because that Linux kernel didn't know of its existence. 

Have you set the repositories to old-releases repositories. Ubuntu 10.04 desktop has reached end of life its software repositories have been closed and put in an archive. This means that you cannot update 10.04 or install any drivers.

This is why we recommend using supported versions of Ubuntu. They have all the improvements to Linux that have been made by the Linux developers and that includes hardware modules.

Have you tried running a live session of a newer version of Ubuntu and testing if sound works in that version? If I remember correctly those old versions of Ubuntu installed with sound muted. The latest versions install with sound set to half way. Have you checked to see if sound is muted?

I cannot give you instructions on how to do these things because it is coming up to 5 years since I last used 10.04.

Regards.

---

