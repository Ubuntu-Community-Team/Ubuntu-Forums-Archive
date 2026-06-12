---
title: "Ram in Mint Daryna"
date: 2008-09-07
forum: Other OS Talk
---

### Post by j_dog on 2008-09-07
I have 4 gb of Ram on dual channel. Why does it only show up as 3.2 gb ?

---

### Post by tdrusk on 2008-09-07
> **j_dog said:**
> I have 4 gb of Ram on dual channel. Why does it only show up as 3.2 gb ?
Hmm... this may be related to you maybe having a 64 bit processor. Mint only supports 32 bit processors. Operating systems for 32 bit processors only support up to 4 gigs. Why it isn't showing 4 gigs is beyond me...

Test this by running 64 bit Ubuntu and running
```
free
```
in the terminal.

---

### Post by kdorf on 2008-09-07
The top portion of the memory range is reserved for accessing things like video card memory, so you will never be able to use the full 4 gigabytes.

---

### Post by molom on 2008-09-08
Thats normal. All 32bit OS's do that when they have a standard kernel.
Read this for more info - [http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

