---
title: "Wireless connection on dell latitude d630."
date: 2012-12-01
forum: New to Ubuntu
---

### Post by computerandwoodslife on 2012-12-01
well I am kind of new on this world of Ubuntu and basically on computers in general so excuse my inexpertly. Am running Ubuntu 12.04 Lts from my Usb into my laptop dell latitude D630 so my problem is that i can only get wired network conection through Ethernet cable. Does anybody knows how to fix the wireless connection?
i think the wireless card is a Broadcom BRCM94311MCG

Thanks

---

### Post by boogerama on 2012-12-01
I've had problems on most Dell's with Broadcomm drivers.

Try this:
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer

If that doesn't work search google for Ubuntu Broadcomm drivers.  You'll get a slew of hits.

---

### Post by squakie on 2012-12-01
If indeed it's a 4311, I had the same problem in a different model but the procedure is the same.  I'm posting this link to my thread as the answer was given there by Wild Man:

[http://ubuntuforums.org/showthread.php?t=2077104](http://ubuntuforums.org/showthread.php?t=2077104)

---

### Post by Bartender on 2012-12-01
Whew, I lucked out.  My boss gave me an old D630 that the IT dept. was gonna turn out to pasture.  It has an Intel 4965 chipset and it works just fine.

If the various Broadcom work-arounds don't work, you could always try buying an Intel 4965 chip via eBay or what have you.  I've done that with a coupla laptops.

---

### Post by Bucky Ball on 2012-12-01
Well, is the USB an install CD and you are using the 'Try Ubuntu' option or you have created a persistent install, i.e. Ubuntu is installed to the USB dongle like it would be to a hard drive?

In the former case, you can't 'install' wireless drivers to installation media. That would be like attempting to put information on a bootable, read-only install CD ... nowhere for it to go ...

If you do a real install to a hard drive (or a persistent install to USB) the wireless card would probably work 'automagically' without you needing to faff about. Broadcom are very well supported on Linux nowadays ...

---

### Post by squakie on 2012-12-01
> **Bucky Ball said:**
> Well, is the USB an install CD and you are using the 'Try Ubuntu' option or you have created a persistent install, i.e. Ubuntu is installed to the USB dongle like it would be to a hard drive?

In the former case, you can't 'install' wireless drivers to installation media. That would be like attempting to put information on a bootable, read-only install CD ... nowhere for it to go ...

If you do a real install to a hard drive (or a persistent install to USB) the wireless card would probably work 'automagically' without you needing to faff about. Broadcom are very well supported on Linux nowadays ...

Unfortunately, with the 4311 at least, using the 12.04 or 12.10 installation media - in my case DVD (12.x doesn't fit on a normal CD) - and doing an install, the wireless still comes up and says the firmware is missing.  The thread I posted the link to is what I had to do in order to get this to work.

EDIT:  I should probably mention that this was verified last night when I loaded 12.10 64-bit on my old laptop instead of using the 32-bit that was there.  No wireless after install - firmware missing - went back and followed Wild Man's post in my old thread I linked to and it worked like a charm (I had to add B43 to /etc/modules to get it to "hold" over a reboot).

---

### Post by computerandwoodslife on 2012-12-01
> **Bartender said:**
> Whew, I lucked out.  My boss gave me an old D630 that the IT dept. was gonna turn out to pasture.  It has an Intel 4965 chipset and it works just fine.

If the various Broadcom work-arounds don't work, you could always try buying an Intel 4965 chip via eBay or what have you.  I've done that with a coupla laptops.

dont take me wrong it might be old but it is armed with a Intel® Core™2 Duo CPU T7250 @ 2.00GHz × 2 that runs just fine.

---

### Post by computerandwoodslife on 2012-12-02
> **squakie said:**
> If indeed it's a 4311, I had the same problem in a different model but the procedure is the same.  I'm posting this link to my thread as the answer was given there by Wild Man:

[http://ubuntuforums.org/showthread.php?t=2077104](http://ubuntuforums.org/showthread.php?t=2077104)

Thanks that fixed my problem; it was so quickly and easy. Wild Man is the man....


Still thanks to all of you all that answered and helped  
=D>

---

### Post by squakie on 2012-12-02
You're welcome - I figure that when they solved it that easy for me that I needed to pass it along before the thread went on a different path.  Glad it's working for you!

And YES, Wild Man is the man! ;)

---

