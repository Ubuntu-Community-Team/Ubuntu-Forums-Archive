---
title: "Check usb speed negotiated"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by quirinovix on 2015-09-30
Sometimes, when i plug a usb 2 drive, it's clear that it's working at usb 1 speed because of terrible transfer rate.
How can i check the speed negotiated before starting a data transfer?
I'm at 14.10.

---

### Post by sudodus on 2015-10-01
Have a look at the following link (and links from it) concerning USB speed. Maybe you are transferring many small files.

[FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

(But I don't know how to check the speed *negotiated*.)

---

### Post by Bucky Ball on 2015-10-01
Just throwing this in: 14.10 is not supported. I suggest you upgrade to 15.04 (or clean install 14.04 LTS). You will no longer receive updates, including security updates, on 14.10 and your current issue may be a consequence of an old, unsupported, out of date release. Hard to know which is why we generally don't give support for out of support releases. 

Good luck. :)

---

### Post by grahammechanical on 2015-10-01
You might also want to check the BIOS/UEFI settings for USB. On my BIOS boot system under USB>USB 2.0 Controller mode there are 2 settings. FullSpeed & HiSpeed. Actually, Hispeed is much, much faster than Fullspeed. So, check the data transfer rates with each setting.

Regards.

---

### Post by quirinovix on 2015-10-01
Thank you all.

sudodus: not many small files. Pictures and movies. Pictures about 5MB. Movies with more than 100MB. Transfer rate: 150kbps. Randomly, unplugging and plugging again, i will get about 20MBps.

Bucky Ball: i will upgrade to 15.10. Waiting for stable.

grahammechanical: Not sure. I will check when i get home. But not sure if is this, since with some tries (plug, unplug) i will get higher speeds. I will look if it's possible to "turn off" USB 1 compatibility, so will "force" to use USB 2.

---

### Post by Bucky Ball on 2015-10-01
You might be tweaking around with this until it is released. Let's hope not and I'll keep my fingers crossed for you. Good luck. :)

PS: Why not upgrade to 15.04 now and 15.10 when it is stable, probably a month or so after its release? (Although many report they are having a fine time with it a month out from release). Probably better to run an upcoming, testing release than a completely unsupported one, but ...

---

### Post by quirinovix on 2015-10-01
> **Bucky Ball said:**
> You might be tweaking around with this until it is released. Let's hope not and I'll keep my fingers crossed for you. Good luck. :)

PS: Why not upgrade to 15.04 now and 15.10 when it is stable, probably a month or so after its release? (Although many report they are having a fine time with it a month out from release). Probably better to run an upcoming, testing release than a completely unsupported one, but ...

A bit of fear. Last time i upgraded, the SO crashed and i had to format (what i don't enjoy anymore). I will stick to next LTS.

---

### Post by Bucky Ball on 2015-10-02
Well, if you're on 14.04 LTS you can upgrade directly via the net to 16.04 LTS when available, leapfrogging the interim releases. Just in case that hasn't been mentioned. :)

---

### Post by quirinovix on 2015-10-22
Looks like lsusb -t shows what i need. usbview does the same with a better looks.

---

### Post by sudodus on 2015-10-22
Good that you found tools showing what you want :-)

- Have you been able to obtain higher speeds in a reliable way?

- What kind of USB drive is it - pendrive, memory card, HDD, SSD?

---

