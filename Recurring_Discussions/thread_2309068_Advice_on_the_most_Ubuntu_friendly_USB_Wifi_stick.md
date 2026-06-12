---
title: "Advice on the most Ubuntu friendly USB Wifi stick"
date: 2016-01-07
forum: Recurring Discussions
---

### Post by hans12345 on 2016-01-07
I am sure this has been posted somewhere, but I cannot find it.

I have various wifi problems (they keep dropping, and on more than one PC) so I want to buy a new USB wifi stick, just so I can eliminate that as a cause of my problems.

Which one (or maybe two) can you recommend?

Thanks

---

### Post by weatherman2 on 2016-01-07
I don't recommend USB WiFi myself for desktop computers.  I prefer to use a wireless ethernet bridge (which you can make out of some wireless routers, especially when they can be configured with Tomato or some other open source firmware).  That way, the desktop computers do not need any wireless drivers, only a basic ethernet driver that is more likely to work than a wireless driver.  Plus, you'd be able to use Wake-On Lan (WOL) to wake up the desktops remotely.

But - that won't necessarily solve your wireless network issues.  They are typically more complex than simply getting a better wireless card, unless your wireless network is reliable with other devices in the same physical location.  You'd also want to look at how the main wireless access point is configured, where it is physically, etc.  If you have a simple USB wireless card now that works in a desktop computer but experiences drops, I'd look at something simple like a USB extension cable that allows you to reposition the USB card slightly to improve reception.

---

### Post by erhollowell on 2016-01-07
I know that most USB WiFi adapters won't work and I have been told that most of this has to do with the Broadcom chipset which is so common not being supported in linux.

I do have a older AirLink usb adapter marked AirLink 101 which does seem to work and has worked on every system I've tried it on. I don't know if those are available anymore. It is marked as AWLL3028 or maybe AWLL302B.

---

### Post by erhollowell on 2016-01-07
I did a search and came up with something which might help you.  [http://blogs.dailynews.com/click/2009/09/20/airlink-101-awll3028-10-usb-wi/](http://blogs.dailynews.com/click/2009/09/20/airlink-101-awll3028-10-usb-wi/)

---

### Post by weatherman2 on 2016-01-07
I've had plenty of USB WiFi adapters work in Ubuntu (including one or two Airlink adapters), but as I said above, I have found the wireless ethernet bridge approach more reliable and easier to use.  This is not a practical option for laptops, however.

I have mostly seen Realtek and Ralink chipsets in the USB adapters, though.

---

### Post by Bucky Ball on 2016-01-07
*Thread moved to **Recurring Discussions**.*

Yes, it has been asked [once or twice]("http://ubuntuforums.org/search.php?searchid=10005309"). (Advanced Search> 'recommend wifi')

You have it back to front. Most wireless dongles do work in Ubuntu nowadays, at least in my experience. Always best to check, though, before uncannily buying one that doesn't. :)

---

### Post by Sweet_Baby_Jamie on 2016-01-08
ThinkPenguin.com has some that use no proprietary software and work well!

---

### Post by kansasnoob on 2016-01-10
I recently tried two from Amazon and both worked well except for one caveat:

[http://www.amazon.com/gp/product/B00S7PO3L2](http://www.amazon.com/gp/product/B00S7PO3L2)

[http://www.amazon.com/gp/product/B004AC0L4Y](http://www.amazon.com/gp/product/B004AC0L4Y)

Sadly that one caveat was a deal breaker. They both "drop out" as soon as the blower in my forced air furnace kicks on :(

I finally broke down and spent about $50 on LAN wiring to avoid further frustration.

---

### Post by Mike_Walsh on 2016-01-12
Hi, hans12345.

I'll make a recommendation, here: one of these little fellers...

[http://uk.tp-link.com/products/details/cat-11_TL-WN725N.html](http://uk.tp-link.com/products/details/cat-11_TL-WN725N.html)

It's a 'nano' design, so you can plug it in and forget about it. Only single-channel, it's true.....but the build quality is second to none, and the range is quite astonishing. Doesn't drop-out, either, once connected. Realtek RTL8188EUS chipset, supported by the '8188eu' kernel driver:-

[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1)

Mine's the version 2, linked from the page above. Support was a wee bit flaky in the early days of 14.04, year before last, but became thoroughly smooth & reliable from about August 2014 onward.....around the time of the first point release. And it's remained that way ever since. It just works.....faultlessly.

Price, around £10UK (approx EU13.50, or thereabouts). I'd recommend this adapter to anybody looking for a wi-fi 'stick' they can 'set-and-forget'.

Hope that helps.

BTW: I'll second weatherman's recommendation of trying the simple first, and use a USB cable to move the wi-fi adapter around first. I've had to do this with a Huawei mobile broadband 'dongle', in order to get a good signal from the cellular network.


Regards,

Mike. ;)

---

### Post by hans12345 on 2016-01-17
Thanks Mike, and you others earlier.

I'll see what I can find locally, but this will be after my winter holiday !

---

