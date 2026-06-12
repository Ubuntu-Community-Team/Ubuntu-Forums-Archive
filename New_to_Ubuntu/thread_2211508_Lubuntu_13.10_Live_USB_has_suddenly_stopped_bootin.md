---
title: "Lubuntu 13.10 Live USB has suddenly stopped booting"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by flyfisherbryan on 2014-03-16
I am trying to spread the word about Linux in general and Ubuntu in particular.  I made a Lubuntu Live USB for a friend for whom I spend a lot of time helping him with his Windows.  He is not very knowledgeable and it took a while to get him able to boot the USB.  After he finally got it working, he liked it, for a few days, but then it stopped working.  After the word Lubuntu appears with the moving dots below, the screen goes blank and nothing else happens, although the USB stick is still working (the light is still on in the stick).  The computer has to be manually powered down. 

The USB is Lubuntu 13.10 desktop i386 and he used it on am HP Pavillion 500-205t.  The USB did have Casper and I had installed GIMP and a card game. Unfortunately I cannot get any further info from my friend, but I do have the stick back and it does not work for me either (another stick created on the same day still does).  I can look at all the files and folders on the stick, but would not know what to look for, any thoughts?

Thanks.

---

### Post by sudodus on 2014-03-16
I think the storage for persistence (the casper-rw file or partition) is borked. This can happen, if the system is shut down before the cached data has been written to the casper-rw file or partition, for example by unplugging the pendrive too early or making a hard shutdown with the power button.

The good part of it is that you can easily restart by replacing (reformatting) casper-rw (or restoring from a backup copy/image).

An installed system (installed to the pendrive) is more stable for long time usage, but is also vulnerable, if the system is shut down before the cached data has been written to 'disk'.

---

### Post by flyfisherbryan on 2014-03-16
How to restore the Casper?  I tried (Before even seeing your reply) copying Casper from my USB to my friends USB (and removing his).  These USBs were supposed to be identical so I could run mine and help him with  his over the phone, so I thought this might solve the problem, but it did not.  I am sure you are right about what happened, but could there be any other file corrupted?  In the end I can just re-format the USB and re-install, but I am trying to use this as a learning experience.

Thanks.

---

### Post by sudodus on 2014-03-16
Do you use casper-rw files?

Do you copy when booted from another system, so that neither the source nor target casper-rw file is 'live'?

Have you checked the file permissions, that they are correct in the target system?

-o-

Something else might be borked too, you can check that the system runs live, when you remove the boot option 'persistent'.

In the worst case, the pendrive is damaged physically. Pendrives have short expected lifetime compared to hard disk drives and SSDs.

But you can do a lot before giving it up. See this link (and links from it) for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by flyfisherbryan on 2014-03-16
It was the Casper-rw file.  I  replaced it and the USB re-booted, although I lost settings it was OK.

Thank You!

---

### Post by sudodus on 2014-03-16
You are welcome :-)

---

