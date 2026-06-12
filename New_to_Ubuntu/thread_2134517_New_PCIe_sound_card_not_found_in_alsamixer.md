---
title: "New PCIe sound card not found in alsamixer"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by sfroberson on 2013-04-11
Hello Ubuntubers!  :guitar:

I recently installed a PCIe sound card (CMI8788) into a PBX/IVR server running a copy of Ubuntu Server 10.04 and it is not showing up in my alsamixer interface.  I can recognize that the card is installed and found on my server however:
(Hopefully I will use these tags correctly)
```
root@pbxserver:/home/user# lspci
....
08:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
root@03pbxserver:/home/user#
```

Also ran an alsa detecting script that I found someone else referring to in another thread that may help
[http://www.alsa-project.org/db/?f=d2d7315737c4ee4f0acf7b7ffacf0b84b2ce23f7](http://www.alsa-project.org/db/?f=d2d7315737c4ee4f0acf7b7ffacf0b84b2ce23f7)


I am assuming this is something simple that I just don't know how to do - like how to locate the correct card in alsamixer or maybe there is a driver missing and I don't know how to apply a specific driver to a piece of hardware without using apt-get update (apparently running an update might break some of the other software on the server).  Currently I have a USB device that can stream music and it shows up in the alsamixer but I was hoping to upgrade the hardware to provide some music on hold service with better quality.  

If anyone could provide some guidance I would greatly appreciate it!  
Thank you,

---

