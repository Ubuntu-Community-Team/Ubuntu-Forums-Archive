---
title: "[SOLVED] force windows drive to mount"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-10-19
My computer (laptop) is set up to dual boot Vista and Ubuntu. The Vista partition crashed (big surprise) and will not boot, nothing has worked on it. I want to use Ubuntu to move my important files over to another computer before I wipe out the laptop. 

Ubuntu will not access my windows C drive. It cannot mount the volume. I have tried to use the force command that comes up as an alternative, but it does not work for me. Any thoughts?

you guys rock!

---

### Post by bpowell2005 on 2008-10-19
Hmmm...I'm not too familiar with Vista, but when I have problems with NTFS drives that were not shut down cleanly by Windows, I use ntfsfix /dev/...whatever...ntfsfix is a program that is included with ntfsprogs...(sudo apt-get install ntfsprogs).

Ntfsfix does a good job of repairing the NTFS drive so it'll mount for me. Although, if the drive has physical errors (bad sectors or something) you'll need to run a complete checkdisk in Windows to have those sectors mapped...I haven't found a way to do this in Ubuntu yet.

Hope this helps!




> **chilimac02 said:**
> My computer (laptop) is set up to dual boot Vista and Ubuntu. The Vista partition crashed (big surprise) and will not boot, nothing has worked on it. I want to use Ubuntu to move my important files over to another computer before I wipe out the laptop. 

Ubuntu will not access my windows C drive. It cannot mount the volume. I have tried to use the force command that comes up as an alternative, but it does not work for me. Any thoughts?

you guys rock!

---

### Post by chilimac02 on 2008-10-20
here's some butter 'cause you're on a ROLL!!!

that worked just great!!

---

