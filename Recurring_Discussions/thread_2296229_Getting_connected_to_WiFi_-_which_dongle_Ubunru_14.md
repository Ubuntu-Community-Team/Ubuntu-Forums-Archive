---
title: "Getting connected to WiFi - which dongle Ubunru 14.04"
date: 2015-09-24
forum: Recurring Discussions
---

### Post by Tim036 on 2015-09-24
I used to be able to buy wifi dongles, little ones, which just worked out of the box 

but all the recent ones no longer do that.

I'm in the UK

Does anyone know of seller that sell linux friendly dongles ?

A very frustrated,

Tim

---

### Post by kurt18947 on 2015-09-24
If you just want "plug it in and it works", my experience is good with Trendnet TEW-649UB. H/W ver.1.0r. It uses Realtek's 8192**SU** chipset which seems to be not very common. Speed is rated as 300 down/150 up. Another adapter I've had good success with is Netgear WNA1100 which uses an Atheros 9271 chipset. If you'd prefer a nano-sized adapter, I've had good luck with Edimax EW-7811Un but it is not plug & play, at least not reliably. The Edimax uses a RealTek 8188CUs chipset. Other readily available adapters use RealTek 8192CU chipset which also are not plug & play. They work but not reliably. There is a patched Realtek driver available here:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

The last time I used this it worked perfectly and the resulting driver was full speed and stable. I've done a hardware refresh recently and now have mostly Intel WiFi so haven't used that github fix recently. It was just updated so I assume it still works. To use the github repository I just copy/paste each line in sequence. As you may have gathered, it's about the chipset, not the manufacturer or model in penguin land.

---

### Post by monkeybrain20122 on 2015-09-24
I  got a few over the years, all work out of the box without any research. I have given some away and others are broken now since they are kind of cheap so I can't tell you the brand and models, I bought them kind of randomly, just picked the cheapest.  I think based on the forum posts here maybe just a few you need to avoid like Netgear. I have seen some from TP-Link that explicitly say on the box that they support Linux, but are a bit pricey (about 25CAD,  or $16 U.S.D, but work out to a bit more with taxes I got the cheap ones for about 10 CAD)

---

### Post by kurt18947 on 2015-09-24
A caution about "works with Linux". It may very well work but it may not work *easily* with linux, particularly for someone unfamiliar with building drivers from source. I tossed a couple adapters when starting out because following the directions did not yield a working driver. In hindsight I should have just put them in a drawer and native support would have likely appeared in a few months. Purchasing an adapter from thinkpenguin.com, purchasing an adapter that has gotten good reviews here, or purchasing an adapter that's been on the market for 1 year+. Having been on the market for a period of time is no guarantee but it increases the odds of it working IMO.

---

### Post by Tim036 on 2015-09-24
Its just Ubuntu 14.04 I'm concerned with regarding 'working' out of the box dongles.

I found it strange that a lot worked just fine 2 years ago and now most don't.

Many thanks to everyone who has responded !

Any more experiences very welcome !

:  )))

Tim

---

### Post by monkeybrain20122 on 2015-09-24
Here I found a super cheap Tp-Link 150Mbps Nano USB adapter. Works out of the box, plug and play. But it is not very powerful, I used it only for downloading the wireless driver for my laptop (broadcom card) since I have no access to wired internet.

---

### Post by Tim036 on 2015-09-25
Many thanks !   I'll get one of those !

Brilliant !

:D:D:D

Tim

---

### Post by Bucky Ball on 2015-09-25
*Thread moved to **Recurring Discussions**.*

---

### Post by mörgæs on 2015-09-25
> **Tim036 said:**
> Its just Ubuntu 14.04 I'm concerned with regarding 'working' out of the box dongles.

Then 15.04 is worth trying.

---

### Post by kurt18947 on 2015-09-26
> **Tim036 said:**
> Many thanks !   I'll get one of those !

Brilliant !

:D:D:D

Tim

A word of caution, at least one of the newer TP-Link adapters are not plug'n'play. The nano adapters - wikidevi shows 2 versions - both require some work. From wikidevi.com:

[CENTER] **TP-LINK** TL-WN725N** v1** 
 [/CENTER]
 [CENTER] **EAN: **6935364050719 ([UPC DB]("http://www.upcdatabase.com/item/6935364050719"), [On eBay]("http://www.ebay.com/sch/i.html?_nkw=6935364050719&_sacat=0&_from=R40"))
**Country of manuf.: **China 
 **Interface: USB** 
 
 **USB 2.0**
**Connector: **Male A
**Form factor tags: **nano dongle 
 
 **ID: **[0bda:8176]("http://usb-ids.gowdy.us/read/UD/0bda/8176") ([[COLOR=red]20 addl. devices[/COLOR]]("http://wikidevi.com/wiki/Special:Ask?title=Special%3AAsk&q=%5B%5BVendor+ID::0bda%5D%5D+%5B%5BDevice+ID::8176%5D%5D&po=%3FInterface%0D%0A%3FForm+factor=FF%0D%0A%3FInterface+connector+type=USB+conn.%0D%0A%3FFCC+ID%0D%0A%3FManuf%0D%0A%3FManuf+product+model=Manuf.+mdl%0D%0A%3FVendor+ID%0D%0A%3FDevice+ID%0D%0A%3FChip1+model%0D%0A%3FChip2+model%0D%0A%3FChip3+model%0D%0A%3FSupported+802dot11+protocols=PHY+modes%0D%0A%3FMIMO+config%0D%0A%3FOUI%0D%0A%3FEstimated+year+of+release=Est.+year&eq=yes&p%5Bformat%5D=broadtable&order%5B0%5D=ASC&sort_num=&order_num=ASC&p%5Blimit%5D=500&p%5Boffset%5D=&p%5Blink%5D=all&p%5Bsort%5D=&p%5Bheaders%5D=show&p%5Bmainlabel%5D=&p%5Bintro%5D=&p%5Boutro%5D=&p%5Bsearchlabel%5D=%E2%80%A6+further+results&p%5Bdefault%5D=&p%5Bclass%5D=sortable+wikitable+smwtable"))
Windows: **USB\VID_0BDA&PID_8176** 
 
 **FCC ID:** [TE7WN725N]("https://fcc.io/TE7/WN725N")
**Industry Canada ID:**  8853A-WN725N

 [/CENTER]
 [CENTER] **WI1 chip1:** **Realtek** RTL8188CUS
[/CENTER]
  **Probable Linux driver**
[**[COLOR=green]rtl8192cu[/COLOR]**]("http://wireless.kernel.org/en/users/Drivers/rtl819x") ([**[COLOR=magenta]in backports[/COLOR]**]("https://backports.wiki.kernel.org/index.php/Main_Page")

[SIZE=3]This one should work with pvaret's github fix I mentioned above, it's the same chip as the little Edimax. V2 of the same model OTOH
[/SIZE]
[CENTER] **TP-LINK** TL-WN725N** v2** 
 [/CENTER]
 [CENTER] **FCC approval date: **02 April 2013
**Country of manuf.: **China 
 **Interface: USB** 
 
 **USB 2.0**
**Connector: **Male A
**Form factor tags: **nano dongle 
 
 **ID: **[0bda:8179]("http://usb-ids.gowdy.us/read/UD/0bda/8179") ([[COLOR=red]2 addl. devices[/COLOR]]("http://wikidevi.com/wiki/Special:Ask?title=Special%3AAsk&q=%5B%5BVendor+ID::0bda%5D%5D+%5B%5BDevice+ID::8179%5D%5D&po=%3FInterface%0D%0A%3FForm+factor=FF%0D%0A%3FInterface+connector+type=USB+conn.%0D%0A%3FFCC+ID%0D%0A%3FManuf%0D%0A%3FManuf+product+model=Manuf.+mdl%0D%0A%3FVendor+ID%0D%0A%3FDevice+ID%0D%0A%3FChip1+model%0D%0A%3FChip2+model%0D%0A%3FChip3+model%0D%0A%3FSupported+802dot11+protocols=PHY+modes%0D%0A%3FMIMO+config%0D%0A%3FOUI%0D%0A%3FEstimated+year+of+release=Est.+year&eq=yes&p%5Bformat%5D=broadtable&order%5B0%5D=ASC&sort_num=&order_num=ASC&p%5Blimit%5D=500&p%5Boffset%5D=&p%5Blink%5D=all&p%5Bsort%5D=&p%5Bheaders%5D=show&p%5Bmainlabel%5D=&p%5Bintro%5D=&p%5Boutro%5D=&p%5Bsearchlabel%5D=%E2%80%A6+further+results&p%5Bdefault%5D=&p%5Bclass%5D=sortable+wikitable+smwtable"))
Windows: **USB\VID_0BDA&PID_8179** 
 
 **FCC ID:** [TE7WN725N]("https://fcc.io/TE7/WN725N")
**Industry Canada ID:**  8853A-WN725N

 [/CENTER]
 [CENTER] **WI1 chip1:** **Realtek** RTL8188EUS
[/CENTER]
  **Probable Linux driver**
[**[COLOR=brown]8188eu[/COLOR]**]("https://github.com/lwfinger/rtl8188eu") (vendor driver)
**[precompiled binary driver for the RPi (Raspbian)]("http://www.raspberrypi.org/phpBB3/viewtopic.php?f=26&t=29752&p=342506")**
[B][USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")


[/B][SIZE=3]I really would have no idea what to expect here. I suspect it would be a 'educational' to get this working[/SIZE][SIZE=3].

It comes down to doing homework and paying attention to model and sometimes version numbers from each manufacturer. 

[/SIZE]

---

### Post by Mike_Walsh on 2015-09-29
In actual fact, the TP-Link WN725N ([COLOR=#ff0000]v.2[/COLOR]) **does **work OOTB. I've been using one since the early days of 14.04. It was a bit buggy to begin with (i.e. not being recognised unless you applied the pvaret GitHub 'fix'), but since the first point release it has worked flawlessly.

It's continued to work through 14.04.2 & 14.04.3, and also works perfectly with Xubuntu 14.04.3. I use it with my 13-yr old Dell Inspiron 1100, which didn't come with a pre-installed wireless card (unlike its big brother, the 5100, which did.)

I suspect the problems stemmed from support (or lack of, at the time) for the 'r8188eu' module.

Hope that helps.


Regards,

Mike. ;)

---

### Post by kurt18947 on 2015-09-29
That's good to know Mike, thanks. Getting plug 'n' play AC speed chipsets should be a boon to those reliant on WiFi. Since discovering MoCA wired networking I've fallen behind the wireless scene.

---

### Post by Mike_Walsh on 2015-09-30
Thankfully, I'm **not **reliant on it..! We've recently got optical fibre broadband to our front door here in the UK, and my PC uses Ethernet. The 1100 is Mum's old one, which she replaced with an Inspiron 15R about 4 years ago.

I've just always loved playing with 'old' tech (bit of a 'dinosaur', me..!) I rescued the 1100; it was going off to the local charity shop. I bought the TP-Link adapter a couple of years ago, and have used it through XP, Trusty (Ubuntu & Xubuntu), and currently, a kennel-full of 'Puppies'. Works with everything I've thrown at it, although it occasionly needs the odd 'tweak' performing on its behalf.....

On the whole, it gets more use during the summer than anything else.....sitting outside on a nice evening. And the best bit about it is the fact of its being a 'nano' design; it's so tiny you can leave it plugged in, and forget about it...no worries about breaking it off, or damaging it. I'm happy with it; it works very well.


Regards,

Mike. :)

---

### Post by Tim036 on 2015-10-04
I've ordered an Edimax dongle also the TP-Link one worked aok as long as it was in place when boot the PC up from cold.

Many thanks every one !

Looks like I need to go to 'Recurring Discussions' !

Tim

---

### Post by Mike_Walsh on 2015-10-04
> **Tim036 said:**
> I've ordered an Edimax dongle also the TP-Link one worked aok as long as it was in place when boot the PC up from cold.

That is the **one** thing you need to remember when using a wireless dongle with** any **flavour of Linux.

You plug it in BEFORE boot.....and you just don't bother to touch it **ever **again. Leave it where it is.....it'll work just fine. Mine has been plugged into the side of the old Dell for over **three** years.....


Regards,

Mike. ;)

---

