---
title: "Dell wireless connection for a huge n00b"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by rash and curious on 2008-06-20
I just set up a psudoboot version of Ubuntu (using wubi 8.04) on my Dell latitude D610 and predictably I haven't been able to get my wireless internet to function.  My ethernet connection works flawlessly, but since this is a laptop and I spend most of my time away from that connection, wireless is somewhat key.  

I've been all over this forum and some other sources (links at the bottom of the post), but I haven't been able to find anything that seems to work.  Part of this might just be my complete Linux illiteracy, and I was hoping someone might be able to just distill the basics down for me or suggest a simpler fix. 

I'm looking forward to learning linux by just fiddling around with it, but without the internet...

Thanks for your help

PS:  My wireless card is a Broadcom BCM4318 (according to terminal).

Guides I've tried to understand/implement:

[http://ubuntuforums.org/search.php?searchid=43322688](http://ubuntuforums.org/search.php?searchid=43322688)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

[https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)

---

### Post by fatality_uk on 2008-06-20
This is a more recent page that might help.
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D)

---

### Post by rash and curious on 2008-06-20
Ok, follow up question.  How do I actually go about downloading this driver?

---

### Post by darylo on 2008-07-13
I'm in same boat.   just installed 8.04.1 on my dell d610 and everything seems to work dandy but not the wifi.  

Once difference is that i have the Intel Pro wireless 2200bg wireless NIC.

the wireless card light is on in windows but not ubuntu.  

Ubuntu does not seem to recognize the wireless card.  

will be following this thread to see if there is solution.. will let you know if i find one.

---

### Post by halitech on 2008-07-13
can you post the output of

```
lsusb
```

---

### Post by TSS on 2008-07-13
Try this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Someone has gotten it working using your computer. S/he said:
> 
I have a Dell Lattitude D610 with the following wireless device according to lspci : Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02). The only thing working for me was the last part, i did have to compile the ndiswrapper...and reboot. But it works now!

They might have a slightly different card then you, but the guide works for basically all Broadcom cards.  It even gives you the links you need to download the drivers.

---

### Post by lionel47 on 2008-08-19
> **darylo said:**
> I'm in same boat.   just installed 8.04.1 on my dell d610 and everything seems to work dandy but not the wifi.  

Once difference is that i have the Intel Pro wireless 2200bg wireless NIC.

the wireless card light is on in windows but not ubuntu.  

Ubuntu does not seem to recognize the wireless card.  

will be following this thread to see if there is solution.. will let you know if i find one.

I spent all weekend trying to get my D610 wireless to work and it was a bust.  Is there any way to bring it back to the way it worked in Gutsy?

Or maybe someone has a fix for this now?

---

