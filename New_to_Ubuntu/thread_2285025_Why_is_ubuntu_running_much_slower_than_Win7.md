---
title: "Why is ubuntu running much slower than Win7?"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by Bj_C on 2015-07-02
Hey all.
I'm relatively new to linux. Im quite attracted the the open source idea.

I run an older laptop, but ubuntu seems to run rather slower than Win7 did. specifically in opening firefox, opening 'files' and loading webpages etc.

All i use my computer for is :
-Listening to music
-watching downloaded videos/movies
-surfing the web
-the odd Youtube vid.

My computer is as follows:
toshiba satellite 
AMD Athlon(tm) X2 Dual-Core QL-60 × 2   1.9ghz
3gb ram
200Gb HD
Im running the latest Ubuntu release. 15.04

Nothing special. Kinda old. But i thought ubuntu would run better than windows? I really don't want to bail back to windows. I really dislike even saying that W word.

Can some please help me?

---

### Post by CantankRus on 2015-07-03
Install this sysinfo script...
```
sudo apt-get install inxi
```

 ...and post your terminal output from
```
inxi -b
```

---

### Post by Kale_Freemon on 2015-07-03
I'm willing to bet that it's an older AMD graphics card without a proper Linux driver. I had an older Satellite too and it had AMD hardware in it. Because of the age of the graphics card, AMD was no longer maintaining the proprietary driver for it. Therefore, I was stuck using the open source driver and it caused Ubuntu to run so slowly while Windows 7 ran like a champ.

---

### Post by mastablasta on 2015-07-03
windows still has better hardware support.

what is your graphics chip? perhaps we can help a bit.

---

### Post by Bj_C on 2015-07-03
> **mastablasta said:**
> windows still has better hardware support.

what is your graphics chip? perhaps we can help a bit.


Sorry guys. Guess i should have included the graphics chip, it says " Gallium 0.4 on AMD RS780"

---

### Post by Geoffrey_Arndt on 2015-07-03
Believe Kale (post #3) is right-on.   So, a possible alternative is to try a lighter "Buntu" version such as Xubuntu or Ubuntu Mate.   Ubuntu Mate is becoming quite a good distro (see here:  [http://news.softpedia.com/news/ubuntu-mate-gets-another-hardware-deal-will-power-the-librebox-mini-pc-485967.shtml](http://news.softpedia.com/news/ubuntu-mate-gets-another-hardware-deal-will-power-the-librebox-mini-pc-485967.shtml) )

By the way, . . BJ,  a really good way (and a fair way) to compare Windows and Ubuntu speed is to do what many others like me and Kale have done, . . . . buy a PC with Ubuntu pre-loaded (see here:   [http://linuxpreloaded.com/](http://linuxpreloaded.com/) )

---

### Post by monkeybrain20122 on 2015-07-03
> **Geoffrey_Arndt said:**
> Believe Kale (post #3) is right-on.   So, a possible alternative is to try a lighter "Buntu" version such as Xubuntu or Ubuntu Mate.   Ubuntu Mate is becoming quite a good distro (see here:  [http://news.softpedia.com/news/ubuntu-mate-gets-another-hardware-deal-will-power-the-librebox-mini-pc-485967.shtml](http://news.softpedia.com/news/ubuntu-mate-gets-another-hardware-deal-will-power-the-librebox-mini-pc-485967.shtml) )

It has nothing to do with being "lighter". The laptop is quite sufficient to run Ubuntu proper, but the card may have some problems with compositing so xubuntu will probably work better.

Alternatively the OP may try upgrade the graphic driver [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by monkeybrain20122 on 2015-07-03
> **Kale_Freemon said:**
> I'm willing to bet that it's an older AMD graphics card without a proper Linux driver. I had an older Satellite too and it had AMD hardware in it. Because of the age of the graphics card, AMD was no longer maintaining the proprietary driver for it. Therefore, I was stuck using the open source driver and it caused Ubuntu to run so slowly while Windows 7 ran like a champ.

Not my experience. Since maybe 12.04 the open source driver always runs smoothly and better than Catalyst except maybe for gaming (I don't do heavy gaming so don't know) or the newest graphic card (my AMD machines are 4-6 years old, have installed Ubuntu even on some older  amd machines that came with XP) But I always use the latest open source driver instead of Ubuntu's stock offer.

---

### Post by Kale_Freemon on 2015-07-03
> **monkeybrain20122 said:**
> Not my experience. Since maybe 12.04 the open source driver always runs smoothly and better than Catalyst except maybe for gaming (I don't do heavy gaming so don't know) or the newest graphic card (my AMD machines are 4-6 years old, have installed Ubuntu even on some older  amd machines that came with XP) But I always use the latest open source driver instead of Ubuntu's stock offer.

My experience was with 14.04 and it was superbly slow. Granted, the machine was quite old, so, this may have been a contributing factor. But regardless, this is one of the reasons why I generally stick to Intel.

---

