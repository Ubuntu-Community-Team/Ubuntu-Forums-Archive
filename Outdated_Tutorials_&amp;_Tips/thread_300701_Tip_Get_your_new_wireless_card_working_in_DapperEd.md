---
title: "Tip: Get your *new* wireless card working in Dapper/Edgy"
date: 2006-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by neocookie on 2006-11-16
So, this one had me stumped when I got my new laptop with WiFi built-in. 

Before even booting into the Windows Media Centre Edition that was bundled in, I wiped the machine and threw Dapper on it. Everything worked swell, apart from WiFi. 

I headed over to the Ubuntu Wiki and checked out the instructions for WiFi: installed NDisWrapper, found the PCI ID of my card, found the manufacturer, "retrieved the Windows driver corresponding to my chipset" from [the list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)... tried a few actuall... still didn't work.

Then I tried the driver on the CD that came with my laptop. Worked first time.

So, my tip: when installing a Wireless card, install ndiswrapper and **try the driver on the CD first**! Might seem obvious to some, but the wiki doesn't mention it, so I'd guess many new ubuntu users don't think to try.

---

