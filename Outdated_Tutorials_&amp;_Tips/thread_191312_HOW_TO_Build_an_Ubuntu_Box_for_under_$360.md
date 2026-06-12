---
title: "HOW TO: Build an Ubuntu Box for under $360"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by spyke01 on 2006-06-07
Hey guys and gals, i thought id share my research with you for a really nice ubuntu desktop that you can build yourself for under $360 dollars. This isn't a crap computer made from cheap parts, most of these parts are name-brand or from companies you can trust. 

Before we start looking lets set our requirements. Below is a list of what i wanted with room for upgades, you can use this or make your own, this is just a guide not a you-have-to-do-it-this-way-or-it-won't-work tutorial!

**_Our Requirements_**
**Micro ATX (M-ATX) Case -** I wanted the computer to be small yet powerful, I want to be able to put it on top of a desk and it not take up the entire thing.

**AMD Powered -** I trust AMD and i find them to be made really well, also since we're going the M-ATX way we'll need low heat output. I want at least a sempron with the possibility of at least an athlon 64.

**MATX Motherboard(M-ATX MB) -** For the board i chose to only stay with the few companies i trust(Asus, Abit, MSI, Biostar, Gigabit, and Foxconn) i wanted to be able to use at least a sempron because theyre cheap and powerful enough for most people. Semprons come in socket 754 and 939, but an opteron 64 and X2 also use 939, the FX does too. I also needed an onboard video card because of the size constraints, I've always used nVidia and nothing but nVidia(also it works great in *nix).

**Optical drive -** I've used lots of brands of drives, but I've found BenQ to be cheap in price but ecellent in quality, id like to stick with them on this project if possible. Most of our small M-ATX cases only have space for 1 optical drive, that means we'll need to have a combo drive or a dvd-rw drive.

**Hard Drives (hdd) -** Everyone has their preferred and hated brands of hard drives, my preffered is Western Digital (WD). I've always used them, they have a great warranty (I've pulled many dead drives from systems of yore that are still under warranty and WD replaced them, sometimes even for larger capacity ones). My hated brand is Maxtor plain and simply because of crappy or no jumper diagrams. SATA 3G/s is fastly growing to be the norm for hard drives, and they're constantly getting cheaper too, I'd like to stick with this if the price is decent. For size we'll need at least 40GBs but 80GBs are usually pretty close in price so we'll be on the look out.

**Memory (mem) -** The brand on this isn't going to matter too much, just no really off brand stuff. We're looking for 512MB-1GB to start with, this'll keep our price low and the system will run great.

**Operating System (OS) -** Ubuntu(Dapper Drake) of course!!! 

**_The Research_**
Ok for online shopping I like to use TigerDirect.com or NewEgg.com they're both great companies and have good return policies and lots of reviews. I usually find NewEgg to be better for hardware and Tiger to be better on monitors. Sometimes I'll use Geeks.com for keyboards and mice, so keep all of these in mind.

For this tutorial I'll use only NewEgg, mainly because like i said their hardware is good yet cheap in price. lets first start with our case, this will let us know what kind of parts we'll need(are we going to need a slim drive? a notebook hdd? can we have a floppy? slim memory? extra power supply? special heatsink?). Ok so lets go looking around at the different ones, make sure to read through the reviews, these help alot when choosing items. I found a nice one for $44.99 so lets put that aside(i'll list each part with links later on). Looks like our case will let us have 1 normal optical, a normal hdd, normal sized memory, comes with a power  supply, only downfall is no floppy drive; Ubuntu doesn't need one to run the install, window$ does however so pick up a USB floppy if you plan on running a dual boot system(keep in mind that you'll have to install window$ first).

Next on our list is our MB, were sticking with M-ATX here, and socket 939, we get a few choices and start looking around and come across a nice Foxconn MB for only $58.99. It's got everything we need, 4 memory slots, onboard Geforce 6100 video, SATA ports, and can take up to the FX processor. Downside: no semprons!(this turned out to be good because newegg wasn't carrying any more semprons at the time)

Ok now our motherboard lets us utilize a SATA hdd and and we can handle up to 4GB memory our lan isn't gigabit, but if you spend some more money I'm sure you'll be able to find a nice one. **Sometimes you'll even find some reviews letting you know that the board is a good linux board.**

the processor page was my next stop, i narrowed my search down to the 939 processors, and lo and behold, no semprons! Oh well, the Athlon 64 3000+ was reasonably priced and if I'm not mistaken, the same speed so we'll go with it.

Ok for the hdd i chose to look at both 40 and 80 GB hdds as well as IDE and SATA 3GB/s. Since I only use WD we'll be going with them, ok looks like the 80Gb is only $5 more than 40GB and SATA 3GB/s is about $1 more than IDE so I'll be choosing a WD 80GB 3GB/s SATA hdd.

Ok now for our optical drive, our case only gives us one space so I'll be looking into a combo drive. After looking around I found a nice Lite-on one(they only had OEM BenQ drives-30 day warranty). 

Ok now onto the last part; memory. Our board is letting us use DDR400 PC3200 memory, so let's start looking around. I started with 512MB, but 1GB wasn't too much more so i chose to go with it instead. I found a stick of Rosewill(they do keyboards, mice, cases, memory, and more) for pretty cheap, but they went out of stock the next day and i was forced to go with Wintec.

**_the Parts I Chose and Their Prices_**
**Case: ** [Athenatech A202BB.L220 Black Steel M-ATX Case w/ 220W Power Supply](http://www.newegg.com/Product/Product.asp?Item=N82E16811190049) [color=red]$44.99[/color]
**Motherboard: **  [Foxconn 6100K8MA-RS Socket 939 NVIDIA GeForce 6100 Micro ATX AMD Motherboard](http://www.newegg.com/Product/Product.asp?Item=N82E16813186085) [color=red]$58.99[/color]
**Processor: ** [AMD 64 3000+ Skt 939 Processor](http://www.newegg.com/Product/Product.asp?Item=N82E16819103537) [color=red]$106.00[/color]
**Memory: ** [WINTEC AMPO 512MB 184-Pin DDR SDRAM Unbuffered DDR 400](http://www.newegg.com/Product/Product.asp?Item=N82E16820161615) 2 x $37.99 = [color=red]$75.98[/color]
**Hard Drive: ** [Western Digital Caviar SE WD800JD 80GB 7200 RPM 8MB Cache SATA 3.0Gb/s Hard Drive](http://www.newegg.com/Product/Product.asp?Item=N82E16822135106) [color=red]$45.99[/color]
**Optical Drive: ** [Black Lite-On Combo Drive](http://www.newegg.com/Product/Product.asp?Item=N82E16827106992) [color=red]$26.00[/color]

**TOTAL: [color=red]$357.95[/color]** 

**_Extras_**
A few extras in case you need them.
**Keyboard: ** [Rosewill Multimedia Keyboard](http://www.newegg.com/Product/Product.asp?Item=N82E16823201018) [color=red]$4.99[/color]
**Mouse: ** [Lighted 2 Tone Mouse](http://www.newegg.com/Product/Product.asp?Item=N82E16826147001) [color=red]$4.36[/color]
**Flat Panel Monitor: ** [AOpen 19" LCD w/ built-in speakers](http://www.newegg.com/Product/Product.asp?Item=N82E16824174033) [color=red]$196.99[/color]

**TOTAL: [color=red]$564.29[/color]** 


**_Conclusion_**
Now we've got to add shipping on top of this, but this is still a great way to make an affordable system for just Ubuntu. If you have any questions on replacement options, feel free to ask. I hope that this will help a lot of people who are afraid to wipe their system or mess with partitions and can afford a price of under $360.00.


**_Notes_**
**Hardware Gurus -** If you know for a fact that any of these parts will not worjk in Ubuntu please notify and i will find a replacement.
**Monitors -** TigerDirect.com has extremely good prices on flat panels, make sure to check them out before just buying any other one

---

### Post by eeried on 2007-02-14
Thanks for your research spyke01. What would be great is if you could tell us if this mobo works with Ubuntu or how you make it work.

That's the main thing. I'd be glad to buy this card whih has all I need but I've read about problems here. No one has said if they've been solved.

---

