---
title: "Graphics Card Recommendations"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by pdb61 on 2013-01-12
Hi

I have install Ubuntu 12.10 onto my old Dell Dimensions 2400.

Default installation shows no icons after logging in. Google indicates others with a similar experience. I was able to get up and running using LXDE in place of Unity.

My novice interpretation at this point is that is appears to be related to my graphics card (an on-board Intel 82845G). 

I intend to buy a new graphics card and was looking for recommendations (it needs to be a PCI card / not PCIe). Aany thoughts welcomed.

Thanks

Pete

---

### Post by pqwoerituytrueiwoq on 2013-01-12
what is your power supply rated for?
should be 200 or 250w
[http://www.amazon.com/EVGA-GeForce-Express-Graphics-01G-P3-1302-LR/dp/B0049MPQA4/ref=sr_1_1?s=electronics&ie=UTF8&qid=1358012331&sr=1-1&keywords=8400GS](http://www.amazon.com/EVGA-GeForce-Express-Graphics-01G-P3-1302-LR/dp/B0049MPQA4/ref=sr_1_1?s=electronics&ie=UTF8&qid=1358012331&sr=1-1&keywords=8400GS)
a new power supply may be necessary to handle the increased power demand, here are some calculators
[http://extreme.outervision.com/psucalculatorlite.jsp](http://extreme.outervision.com/psucalculatorlite.jsp)
[http://images10.newegg.com/BizIntell/tool/psucalc/index.html?name=Power-Supply-Wattage-Calculator](http://images10.newegg.com/BizIntell/tool/psucalc/index.html?name=Power-Supply-Wattage-Calculator)

---

### Post by Cheesemill on 2013-01-12
PCI video cards haven't been manufactured for years now so there isn't really a choice, you'll just have to get whatever you can find (although if it's an ATI card it probably isn't worth getting).

Are you sure your motherboard doesn't have an AGP slot? If it does you may still be able to find cards for sale.

---

### Post by sudodus on 2013-01-12
Before buying a new graphics card, we should also discuss other parts of your hardware. Is the following link describing your hardware?

[[COLOR="Red"]http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4505-3118_7-30824846.html[/COLOR]]("http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4505-3118_7-30824846.html")

Particularly, what is your cpu and ram?

I think you will not get good performance with 'vanilla' Ubuntu or Kubuntu. You need a lighter desktop environment, Lubuntu or Xubuntu. 

Also I think that you need at least 1 GB of RAM for anything above Lubuntu. Also Lubuntu will benefit a lot if you increase the RAM to the maximum 2 GB.

With at least 1 GB of RAM and a new graphics card, your machine will probably be nice. You might be able to get a used graphics card.

---

### Post by pdb61 on 2013-01-12
Thanks very much for all the responses.

The CPU is an Intel Pentium 4, 2.20Ghz with 512 KB integrated cache and I have 1 GB of DDR SDRAM installed.

I would be happy to upgrade my RAM to 2GB and even upgrade the processor and (if necessary) my power supply. 

I recognize that even when upgraded the machine will not impress but it feels too early to put it to rest!

Lubuntu is an option for me but would appreciate guidance on the graphics card. Happy to buy second hand (which looks like my only option).

Thanks

---

### Post by Mark Phelps on 2013-01-12
One reason to avoid ATI cards is that those old enough to still be available on PCI cards are not going to be supported well in Linux.

ATI dropped Linux support for the X-series (e.g., x1650) cards a few years ago, then this summer, they dropped support for ther HD 2x/3x/4x series cards.

Anything you buy using PCI cards is most likely an x-series -- which will relegate you to using the default Radeon drivers -- which, if all you do is typical desktop 2D work (web browsing, office work, video/picture/audio entertainment, is probably going to be OK.  But, trying to watch high-def DVDs or Blue-rays may not work well, and any 3D games are out of the question.

---

### Post by pdb61 on 2013-01-12
My aim for this machine is to provide an entry level platform from which I can explore the world of Ubuntu/Linux. I would be happy to operate operate without access to high powered graphics for the moment.

That said, I would like to get the best out of an old machine. Does anyone have a favorite PCI graphics card? (no AGP slot or PCIe capability on the DD 2400).

Avoid ATI but would it be possible for someone to narrow the choice down a little for me? 

Thanks.

---

### Post by sudodus on 2013-01-12
The support for old nvidia cards/chips is better.

You have an intel chip, and Ubuntu (linux) works well with intel chips. The chip may not be very powerful, but at least you can expect, that it does well within its limits with Ubuntu.

---

### Post by pdb61 on 2013-01-13
In summary, I had installed Ubuntu 12.10 on my Dell Dimensions 2400. When logging in Unity presented itself with no Launcher icons bar.

Following suggestions earlier in this thread, I 

1. Updated my box to 2Gb RAM from 1 Gb

2. Bought and installed a Nvidia GeForce 6200 card.

3. Installed the driver with 

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current 

4. Rebooted

and I can now see the Launcher when logging into Ubuntu/Unity :D

Thanks for all the input.

---

