---
title: "Oneiric X not loving VIA openchrome"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-07-09
This second computer I just hooked up has a VIA UniChrome P4M800 graphics chip which uses the openchrome driver but Oneiric defaults to using VESA :(

Just wondered if anyone else has seen this?

Clear back around Gutsy, and maybe Hardy, I had to edit xorg.conf to make it use the openchrome drivers so I may have to play around a bit.

---

### Post by JRV on 2011-07-09
I'll fire up my old VIA, install 11.10 A-2, and see what happens.
Check back tomorrow.

---

### Post by JRV on 2011-07-09
I installed the Ubuntu 10.10 driver from VIA, 

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

The graphics are improved.  Most notably when I switch workplaces it is a little bit faster.

I don't know what it was using before because I don't seem to have a /etc/X11/xorg.conf file.

---

### Post by kansasnoob on 2011-07-09
The bug was between the chair and the keyboard :oops:

I just got this old VIA box setup with a new router and a KVM switch, and while installing Oneiric I switched the KVM to use my Intel box. So there was no monitor for the installer to read info from.

So it was using the openchrome driver, but offered only 800x600 and 1024×768. I figured this out partly by reading the xorg log, and by experimentation.

I am going to have to do some figuring here though because I very much want to be able to do iso-testing with this setup. Currently with the Intel box I have to boot the live CD (or install) and then plug in a flash drive that has a pre-built xorg.conf I can copy to /etc/X11 and then hit Alt+SysReq+K.

I'll figure it out. Sorry for the false alarm.

---

### Post by kansasnoob on 2011-07-09
> **JRV said:**
> I installed the Ubuntu 10.10 driver from VIA, 

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

The graphics are improved.  Most notably when I switch workplaces it is much faster.

I don't know what it was using before because I don't seem to have a /etc/X11/xorg.conf file.

Thanks for the info. I'll actually check that out.

But my biggest problem was my own stupidity :(

I hope you don't shoot me :biggrin:

---

