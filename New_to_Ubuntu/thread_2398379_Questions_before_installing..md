---
title: "Questions before installing."
date: 2018-08-11
forum: New to Ubuntu
---

### Post by tarxsix on 2018-08-11
Hello,

Started studying Linux and had a few quick questions.

I got a refurbished Dell Latitude E6430 to set up a home server on. Can I just install Ubuntu server on it or do I also need to install the dell drivers?
Later on, if I upgrade the ram, it will detect automatically?

The first thing I want to do is set up a file server using 2 usb hdd's in a mirror raid. There's a lot of info/discussion out there. Any recommendations to a good guide or thread?

Regards,
David.

---

### Post by TheFu on 2018-08-11
Just install.  It will most likely be fine.  Dell is fairly well supported.
Hardware changes are generally seen automatically, unless an odd driver is necessary. The only time RAM changes aren't seen automatically, is when there's a hardware failure.

Using USB connections for RAID is a bad idea. USB storage commands aren't the full set provided by the SATA commands.  USB connectors vibrate loose too and very often have not-so-great performance.

IMHO.

I'd use USB storage for media or backups, not RAID.

---

### Post by tarxsix on 2018-08-11
For storage, I need a network drive that is mirrored because some important files are updated on a somewhat daily basis. I have the laptop for my server and usb drives are just the most convenient for my home use, not really concerned about performance. The set up will just be sitting on top of my old VCR behind me :) Besides a file server, I'll just be using it to practice Linux and setting up a Terraria server.. :)

---

