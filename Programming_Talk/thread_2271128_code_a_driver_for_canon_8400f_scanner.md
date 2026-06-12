---
title: "code a driver for canon 8400f scanner?"
date: 2015-03-27
forum: Programming Talk
---

### Post by fwrun2011 on 2015-03-27
hi;
since i cannot find a driver for my canon 8400f scanner, i am thinking perhaps i can code my own. i've never coded a driver before, but would think it would be possible - if i can figure out how to 'talk to' the scanner. since it's usb, there are some universally recognized query and responses, right? 
to start with, i would like to open a terminal, open communication with the device, and see if i can get it to at least give me its usb device code.
it would be really great if canon would give me some info, but from what i have read, they are the worst manufacturer when it comes to linux drivers.
perhaps though, i can find the source code for another canon driver that is somewhat similar? i might be able to get an idea of where to start.

am i being naive to think i could do this, or is it something that might be worth pursuing?

thanks for your input

FW

---

### Post by kurt18947 on 2015-03-27
I believe there's quite a lot involved in writing a hardware driver no matter the O.S. We have a Canon 8800f which worked 'out of the box'. The lid light required for scanning transparencies like slides and negatives doesn't seem to be supported in SANE (the linux scanner driver) so we downloaded VueScan from Hamrick software. The download is shareware and will function if your scanner is supported but any scanned images will have a watermark. Purchasing a license removes the watermark. You could download it and try it. VueScan is different from most linux programs in that it doesn't have to be installed. It consists of 3 files, one of which is an executable called vuescan. It should be marked as executable when downloaded.  Just double-click the vuescan file and it should start. 

Edit: in fact it appears that the Canon 8400F is indeed supported.

[http://www.hamrick.com/vuescan/canon_8400f.html](http://www.hamrick.com/vuescan/canon_8400f.html)

---

### Post by fwrun2011 on 2015-03-27
I wonder whether the 8800 driver would work (albeit with limited functionality) with my 8400. It might be worth a try. If that doesn't work, I'll see what I can do with vuescan.
I guess coding a driver wouldn't really be a good project for me, since I really don't have all that much experience coding. Just thought I might learn a lot faster if I had something 'driving' me (pun intended!).

FW

edit: I went the vuescaon website following your link, read the top - had hope for a few seconds, but scrolling down I read that the 8400F is supported in Max OSX and Windows only.:sad:
I guess that's one of the few reason I have to keep Windows on my system (dual-boot).

---

### Post by pdc on 2015-03-27
[http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

can I suggest you join this list? These are guys do the development for sane; and maintain the sane-development release that has the latest

.... they could best help you

---

### Post by kurt18947 on 2015-03-30
[QUOTE=fwrun2011;13253938
................
edit: I went the vuescaon website following your link, read the top - had hope for a few seconds, but scrolling down I read that the 8400F is supported in Max OSX and Windows only.:sad:
I guess that's one of the few reason I have to keep Windows on my system (dual-boot).[/QUOTE]

Dat sux. I thought VueScan was cross platform. I don't know their development process - perhaps they 'tweak' Windows/OSx drivers and there's no linux driver to tweak. PDC has a good suggestion - contact the SANE devs. I would think the 8800F/9000F is not *that* different.

---

