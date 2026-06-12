---
title: "How to Disable Location on Firefox?"
date: 2016-06-28
forum: Programming Talk
---

### Post by llTheSoldierll on 2016-06-28
hi

I want to disable location on Firefox (I guess I also did this by following this);


[LIST]
[*]In the URL bar, type about:config 
[*]Type geo.enabled 
[*]Double click on the *geo.enabled* preference 
[*]Location-Aware Browsing is now disabled 
[/LIST]
 
However when I search something from google it shows me still my location as in the picture. 
How can I correct this? Can it be related with the Gmail account? If yes, how can I stop it?

[URL="https://drive.google.com/open?id=0B01FrxAS8WR-QVVHWHZDTHV5c3c"]https://drive.google.com/open?id=0B01FrxAS8WR-QVVHWHZDTHV5c3c
[/URL]

---

### Post by &amp;KyT$0P# on 2016-06-28
Google uses GeoIP not the location API.  The only way you can do anything about it is to use something like a proxy or VPN of some sort, however by doing that you are potentially giving up significant security...

EDIT And just to be clear, this (GeoIP) has nothing to do with Firefox, it's way more low level than that.  It's just the nature of the Internet.

---

### Post by spjackson on 2016-06-28
Welcome to the forums. The image shows that Google has estimated your location from your internet (IP) address. You could avoid this by using a proxy or tor. Oops, too slow.

---

### Post by llTheSoldierll on 2016-06-30
Hi again,

I've been trying to setup Proxy or VPN since you said and no more a tutorial for watching or reading behind. 
Unfortunately, I couldn't setup them yet.

And not Proxy but VPN is looked like need to be paid. Do you know any way to setup them?

- Thanks

---

