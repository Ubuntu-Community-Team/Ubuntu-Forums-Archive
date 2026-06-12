---
title: "ubuntu as server for raspberry pi's running xmbc by each tv"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by squakie on 2013-05-29
Wondering if anyone has some thoughts on using an Ubuntu box as some sort of server with music, video and pictures so that I could have raspberry pi's running xmbc by each TV in the house and them to have access of this central server of some sort?  Would I need some sort of database so the pi's would be able to access the titles?

---

### Post by Cheesemill on 2013-05-29
The easiest way is to set up an NFS server to share your media to the Pi's.
[https://help.ubuntu.com/12.04/serverguide/network-file-system.html](https://help.ubuntu.com/12.04/serverguide/network-file-system.html)

Or if you want to be able to access your media from Windows machines as well then go for Samba instead.
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

I do this at home with [OpenELEC]("http://openelec.tv/") running on my Pi's.

---

### Post by squakie on 2013-05-29
Great!  Thanks!  I was going to just use my little zbox for my own TV, then I thought about the raspberry pi's and thought - hummmm, they can run xmbc, so why not use my zbox for serving all those other TV's.  This gives me a lot more to read and look at now.

---

### Post by squakie on 2013-06-05
This is all working great!  Thanks Cheesemill!!

---

### Post by papibe on 2013-06-05
> **Cheesemill said:**
> The easiest way is to set up an NFS server to share your media to the Pi's.
...
I do this at home with [OpenELEC]("http://openelec.tv/") running on my Pi's.
+1

I do the same but I'm using [Raspmc]("http://www.raspbmc.com/") instead.

Regards.

---

### Post by squakie on 2013-06-05
Here's what I'm doing:

- the desktop is also running xmbc and samba server
- the desktop xbmc can either play directly from hard disk or from shares
- the Raspberry Pi is running the 5-25 update of Raspian
- I installed xbmc in Raspian (found a great link - hope I can find it again!)
- the Raspberry Pi xbmc accesses both shares and a local usb hard drive

I'll be experimenting with an I/R receiver from Radio Shack later today.  I just have to wire it up and test - I already installed lirc in Raspian also.

Those little buggers are fun to work with.  Brings back memories of long, long ago - but of course this thing runs a lot faster, has more memory, etc., etc., etc..  But the hardware side (all the general purpose IO's layed out like Arduini boards), the voltages available, etc., make it a fun thing to mess with - and only $39!  At least I'm not paying $450 for a bare single board that I have to solder all the parts to (after I find them), build my own keyboard, keyboard interface, disk interface, write the drivers for the disk, etc..  So, it's cheaper, more fun for me where I'm at now in life.

Thanks again, everyone!

---

