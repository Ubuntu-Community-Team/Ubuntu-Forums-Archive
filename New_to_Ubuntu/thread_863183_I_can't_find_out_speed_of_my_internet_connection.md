---
title: "I can't find out speed of my internet connection"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by t0p on 2008-07-18
I connect to the internet via my mobile phone.  I haven't set up a PPP connection or anything like that: my phone is set up so, when I connect it to my computer, the phone detects the link and automagically connects to the net.

When I hover my mouse pointer over the "plug" icon in the bottom right-hand corner of the desktop, it tells me
> wired ethernet connection active: usb0

I look in Network tools, and the connection info is under **Unknown Interface (usb0)**.  It says
> Link speed: not available

Is there another way I can discover the speed of my internet connection?

---

### Post by unutbu on 2008-07-18
You can test your bandwith speed at a site such as one of these:

[http://resources.zdnet.co.uk/speedtest/](http://resources.zdnet.co.uk/speedtest/) (if you are in Britain)
[http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest) (Has a directory of world-wide speedtests)
[http://www.bandwidthplace.com/speedtest/](http://www.bandwidthplace.com/speedtest/)
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

Or you can do it the old fashioned way by finding something large to download (like the [latest linux kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.tar.gz")) and time it with

```
wget URL
```
(wget will tell you KB/s).

---

### Post by t0p on 2008-07-18
**Thanks** for the links unutbu! Most informative!

---

### Post by coffeecat on 2008-07-18
I've become a bit cynical about these speedtest sites. More than once, I've downloaded something big. with firefox showing a really good dl speed. Once the download had finished, I'd gone to [http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html) and the dl speed was reported as much less what I'd just got with firefox. So I'd gone back to FF and downloaded something else and got the original good dl speed. I think the limitation was in the speedtest server, not my BB connection.

> **unutbu said:**
> Or you can do it the old fashioned way by finding something large to download and time it with

```
wget URL
```(wget will tell you KB/s I think).

I like the idea of using wget, but so long as the file wasn't too large. It could work out rather expensive with mobile phone broadband. :wink:

---

### Post by t0p on 2008-07-18
> **coffeecat said:**
> 
I like the idea of using wget, but so long as the file wasn't too large. It could work out rather expensive with mobile phone broadband. :wink:

It depends on what kind of deal you've got with your mobile service provider.  I have got an "unlimited" data allowance.  There's a fair use policy, of course, but in practice it seems like I can up/download as much as I want!

---

### Post by halitech on 2008-07-18
coffeecat - most of the speedtest sites use some form of java so it uses overhead and does slow everything down some so using wget or a download from the web.

---

### Post by coffeecat on 2008-07-18
> **halitech said:**
> coffeecat - most of the speedtest sites use some form of java so it uses overhead and does slow everything down some so using wget or a download from the web.

Thanks for that explanation. Much appreciated. The thinkbroadband site certainly does use Java. This makes me think that these speed test sites are rather pointless, at least when they use software that renders the results meaningless. :roll:

---

