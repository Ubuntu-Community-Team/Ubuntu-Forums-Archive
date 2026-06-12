---
title: "Radeon driver"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Slim1950 on 2008-11-17
I am a very frustrated beginner. Perhaps I have been asking for help in the wrong forum.. I have a 9200 series ATI video card. I have tried for days to learn from what I am reading, and I am going in circles. 

Would someone please be willing to exchange MSN info with me, so that they can walk me through the process and be done with it? This business of waiting for a day for an answer, then finding out the guy misunderstood me, or vide versa.. at this rate is is going to take me a week..

Unless you can point me to a web based sure-fire dummies guide to installing the right driver...

Please. We'll exchange MSN info in private messaging..

---

### Post by w4ett on 2008-11-18
The RV280 GPU Cards....AMD/ATI 9200/9200SE Cards are supported by the open source driver only.  AMD/ATI have dropped driver support for the legacy cards before the 9500 series.

In other words, if you are trying to manually install restricted drivers for your card, I can understand your frustration.  Using the open source driver, you  will have 3D support however, with 800FPS or so.  Compiz Fusion and Google Earth are usable, but gaming is entirely another question.

If you have attempted to install fglrx manually, you will have to purge that attempted install, and revert to the xorg driver.

Hope this answers you question.

---

### Post by Slim1950 on 2008-11-18
I have gone to the package manager and uninstalled every file with fglrx in it.

Does the OPen Source driver automatically get installed? Am I already using the open source driver then? How do I check whether I am using the open source driver? Where do I find it?

I am soon going to give up on this (because if the open source radeon driver is already driving this graphics card, it really sucks).

I am looking at something modest, but will this card handle Ubuntu 8.10.. 
Sparkle GeForce 8500 GT / 512MB DDR2 / SLI Ready / PCI Express / DVI / VGA / HDTV / Video Card
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3145095&Sku=S15-8500](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3145095&Sku=S15-8500)

---

### Post by w4ett on 2008-11-18
> I am looking at something modest, but will this card handle Ubuntu 8.10..
Sparkle GeForce 8500 GT / 512MB DDR2 / SLI Ready / PCI Express / DVI / VGA / HDTV / Video Card
[http://www.tigerdirect.ca/applicatio...5&Sku=S15](http://www.tigerdirect.ca/applicatio...5&Sku=S15)

The 8500 Nvidia is well supported....IMHO it is a good choice considering price/performance.

On the subject of the xorg-driver-ati.....what can I say.....it does provide modest 3D capability, but considering that ATI/AMD still supports the 9200 in Windows, I find it's shameful that they do not still support a linux driver for those cards that are still available retail.

---

### Post by Slim1950 on 2008-11-19
Oops. I bought the 8500 series, brought it home and realized, I don't have a PCI Express slot in my machine.
Hmm, my computer must be a dinosaaur. DO they still make AGP cards?

---

### Post by w4ett on 2008-11-19
Don't know where you are on the globe but look here: [http://www.pricewatch.com/video_cards/agp_512mb.htm](http://www.pricewatch.com/video_cards/agp_512mb.htm)

You can find some good deals there.

---

