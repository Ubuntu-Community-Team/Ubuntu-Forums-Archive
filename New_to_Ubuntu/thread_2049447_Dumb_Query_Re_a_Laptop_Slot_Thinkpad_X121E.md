---
title: "Dumb Query Re a Laptop Slot Thinkpad X121E"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Andavane on 2012-08-28
When I got my little Thinkpad and saw the slot on the right side I assumed that you just put an SD card in it.
I took the SD card out of my X201i to move data and the size seemed right on the liitle 11" model but it would only go half way in.

Then I download the manual. and look at the right side and see it's a card reader slot. I don't think I have one - how odd one didn't come with the machine! I screenied a bit of te manual and attach it here. What do I need to do to get it to work? What bit do I need to get.

This isn't an ubuntu question but the forum states "for computers in general" so it should be all right.

---

### Post by Mark Phelps on 2012-08-29
IF you're lucky, someone will come along who has used this model laptop and found a driver for it; but more realistically, in general, these card readers do NOT work in Linux.  They often require special drivers which are not available for Linux.

I have a similar problem with my desktop and have only been able to "solve" it by using a card reader with a USB cable.  Recognize that's somewhat clumsy for using with a laptop, but it may be the only thing that will work.

---

### Post by Andavane on 2012-08-29
> **Mark Phelps said:**
> IF you're lucky, someone will come along who has used this model laptop and found a driver for it; but more realistically, in general, these card readers do NOT work in Linux.  They often require special drivers which are not available for Linux.

I have a similar problem with my desktop and have only been able to "solve" it by using a card reader with a USB cable.  Recognize that's somewhat clumsy for using with a laptop, but it may be the only thing that will work.
OK thanks... how odd. I'd always assumed these things 'just worked'... mmm.
However on a mechanical level my card only goes in half way and then stops. Is that correct?
So far I've only tried it with the pc switched off. When it didn't go all the way in, I didn;t switch it on in case I messed up something. IN MY x201 the card rides in smoothly, then it clicks, then to get it out you put in your fingernail and push, it clicks in further (releasing a  catch I guess) before popping out smoothly. Trouble I'd go search it on google, youtube but I don't know what search key I'd enter!

---

### Post by Wim Sturkenboom on 2012-08-29
It's probably normal. I have a couple of laptops / netbooks (not your models) and a SD card goes all the way in in some and only halfway in others.

---

### Post by Andavane on 2012-09-02
> **Wim Sturkenboom said:**
> It's probably normal. ...SD card goes all the way in in some and only halfway in others.

Yup... errr... It works fine, but doesn't go all the way in! 
  Cheers!
[IMG]http://flic.kr/p/d49QMY[/IMG]

---

### Post by coffeecat on 2012-09-02
@Andavane, are you trying out the slot with a SD card or SDHC card? SD cards are generally (always?) less than 4GB and SDHC generally 4GB or more, but the card will tell you whether it's SD or SDHC. If you've been trying with a SDHC card, test the slot with a SD card.

All the 4-5 laptops with SD slots that I've tried work with SD cards in Ubuntu but only some work with SDHC - others don't. I don't know about Thinkpads. It may be that yours won't work with SD cards or SDHC cards, but try both.

Unfortunately, even the USB card readers can be hit and miss with SDHC cards. I have two of those little USB SD card readers, the ones that look a bit like a USB dongle. One works with SDHC cards, the other not. The irony is that the one that came free with a SD card is the one that works.

---

### Post by Andavane on 2012-09-03
> **coffeecat said:**
> @Andavane, are you trying out the slot with a SD card or SDHC card? SD cards are generally (always?) less than 4GB and SDHC generally 4GB or more, but the card will tell you whether it's SD or SDHC. If you've been trying with a SDHC card, test the slot with a SD card.

.....

Unfortunately, even the USB card readers can be hit and miss with SDHC cards. I have two of those little USB SD card readers, the ones that look a bit like a USB dongle. One works with SDHC cards, the other not. The irony is that the one that came free with a SD card is the one that works.
I don't think I've got an SDHC card. Is it the same physical size as SD?
It can't be smaller, surely!?

---

### Post by coffeecat on 2012-09-03
> **Andavane said:**
> I don't think I've got an SDHC card. Is it the same physical size as SD?
It can't be smaller, surely!?

The physically smaller ones are the mini and micro SD cards. SD and SDHC are the same size. On an SDHC, you'll see the SDHC logo. Have a look here:

[http://en.wikipedia.org/wiki/SDHC#SDHC](http://en.wikipedia.org/wiki/SDHC#SDHC)

If you click on that link you'll see an image of a SDHC at top right. The SDHC logo may be much smaller than in that image but an SDHC card will have the SDHC logo and an ordinary SD card will only say SD.

SDXC is something else again, but I have no experience of an SDXC card, but that article explains the differences between the various *SD* cards.

---

### Post by Bartender on 2012-09-03
My (admittedly limited) experience with Ubuntu and laptops has been similar to Mr. Phelps'.  I haven't had any luck with the laptops' built in readers, but a separate USB card reader usually works.

---

### Post by kurt18947 on 2012-09-03
Hmmm, I wonder if some SDHC cards are using the exFAT file system?  exFAT is supposed to be intended for flash devices larger than 4 GB.; it removes the 4 GB. file size limitation of FAT32 and is supposed to have some other advantages.  Fortunately, there is a driver for exFAT in Linux available via a ppa.  I installed it and formatted a flash drive to exFAT in Win7.  The exFAT formatted flash drive would read and write files in Linux.  I don't know that there are any exFAT file utilities for Linux yet but I was able to read and write.  Here's the ppa:

[http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)

---

### Post by Andavane on 2012-09-06
I could've sworn I'd added another reply to this thread, but apparently not. Unless it was in a dream.
Yes it works fine, it just doesn't ride in all the way that's all. Perhaps that's allow for a smaller all. After all I guess IBM is the Great Grand Daddy of computing. OK it says Lenovo, but it's still made and serviced by IBM.
The more toy-like Idea Pads are made by Lenovo though.

---

