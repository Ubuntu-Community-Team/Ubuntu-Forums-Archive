---
title: "opensource offline Skyhook/WPS client in Python?"
date: 2009-03-20
forum: Programming Talk
---

### Post by inportb on 2009-03-20
I'm writing one of those and I'm wondering if anyone's interested in having some fun with it or if it's been done already.

Yes, I have read the FAQ; I'm just not sure if this is the right place to post... if not, please move it, m'kay? :)

So... [Skyhook]("http://en.wikipedia.org/wiki/Skyhook_Wireless") is a proprietary technology that takes the BSSID's of the WiFi stations near you and returns your geographic coordinates. The mechanism is pretty basic: they send wardrivers all over to collect BSSID's, signal strengths, and coordinates... and then compile the data into a huge database. This saves power, gives you a faster fix on your location, and works well where GPS sucks (within buildings, in densely-populated areas). But best of all, this gives WiFi-only devices (like your laptop) a positioning mechanism. Neat, eh?

Google has something similar.

There're some major issues with these proprietary services:
1. they move slowly, since they depend on hired wardrivers
2. they're not available offline, so you have to be online... hardly useful while on the go (except smartphones with data service)

I figured that an opensource alternative would fix both problems:
1. we could do the wardriving ourselves and share data
2. because we have all the data/algorithms without restriction, we could perform the calculations offline

What do you think?

---

### Post by inportb on 2009-04-05
Well, the overwhelming response is very nice ;)

Eh, here're some links if you're interested in this stuff...
The software itself: [http://www.110mb.com/forum/empty-t43412.0.html](http://www.110mb.com/forum/empty-t43412.0.html)
A simple application: [http://www.110mb.com/forum/general-chat/empty-t44817.0.html](http://www.110mb.com/forum/general-chat/empty-t44817.0.html)

---

