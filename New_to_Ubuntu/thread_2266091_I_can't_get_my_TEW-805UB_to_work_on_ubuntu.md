---
title: "I can't get my TEW-805UB to work on ubuntu"
date: 2015-02-19
forum: New to Ubuntu
---

### Post by Kenneth_Boxall on 2015-02-19
[URL="http://www.trendnet.com/products/proddetail.asp?prod=100_TEW-805UB"]

http://www.trendnet.com/products/proddetail.asp?prod=100_TEW-805UB[/URL]

there is no linux driver I get that I tried using many troubleshooting via-google and this website. I used everything from manually installing ndiswrapper to wine.

so I have used gksu set-up ndiswrapper so it would be in applications then I used the Windows 64-bit drivers to install
When I check the driver is says it is present aswell as the hardware.

When I couldn't get this to work out for me I attempted manually making a wifi which of course without the USB looking for a signal did not do anything.

I attempted to install Trendnet's Wireless Configuration Utility through wine but wine just closes the moment it opens so that didn't work. Anytime I looked this up people just turn up their noses at anyone posting saying "Look for linux alternatives don't expect wine to open your windows programs" So I'm not sure why I see that so often maybe it's just linux fanboys hating on anyone using windows based programs via-linux.

anyways. If anyone can help that would be awesome I'll try to watch for replies and copy/paste and answer anyone with questions.

I am currently using my laptop to share it's net connection via-ethernet cord so I can't access the internet just haven't gotten the USB wi-fi to work yet in linux (It works on Windows)

I am using Windows 7 and unbuntu 64-bit and I made sure the driver was 64-bit windows 7. After downloading the software and drivers via-Trendnet's site the driver for Windows 7 64-bit is netrtwlanu.inf

---

### Post by Mike_Walsh on 2015-02-19
Hallo.

I'm no expert in this kind of thing, I'll quite cheerfully admit. However, this link may be of some interest:-

[http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/](http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/)

Of course, this WAS dated 9 months ago. It's quite possible this has been included into the kernel by now. The RTL8812AU chipset is apparently used extensively by most modern wi-fi adapters, so I would be surprised if it WASN'T included by now. The kernel has gone from 3.13-0.24 to the current 3.13-0.45 in those 9 months; and any day now, we should be migrating to the 3.16 kernel.....

Worth a try, anyway. Don't ever be afraid of the terminal; it's capable of much more than the rest of the system put together, sometimes.


Regards,

Mike. ;)

---

### Post by Kenneth_Boxall on 2015-02-19
Great news Mike, you fixed my problem after 24 hours of tinkering on all angles :P I will make this Solved. <3

---

### Post by Mike_Walsh on 2015-02-20
> **Kenneth_Boxall said:**
> Great news Mike, you fixed my problem after 24 hours of tinkering on all angles :P I will make this Solved. <3

Oh, that's great. Glad to hear it; wi-fi & networking is NOT my strong point, like I said. To be honest, it's a method I've never had to use myself (thankfully, my network connections have always just 'worked'!).....but if it's helped to get you up-and-running, then that WAS, after all, the whole point of the excercise.

Have fun!


Regards,

Mike. :)

---

