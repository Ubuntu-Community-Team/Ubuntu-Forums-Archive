---
title: "Migrating bookshop system from Visual DBase"
date: 2007-07-31
forum: Programming Talk
---

### Post by novymir on 2007-07-31
I'm currently researching bringing a bookshop out of the eighties and into the web-enabled and free software world. The shop is currently using an ancient custom built Visual DBase 5 system (actually a slightly upgraded terminal-based DBase 3 for DOS program running in version 5). The new system should be able to power the our website catalogue either by an easy export process, or by actually using the same product database as the shop computers.

I'd be very appreciative if anyone has any suggestions of how to move to a new system. I'm toying with a few ideas...

1. Import the database to MySQL and completely re-write the front end, as well as all the data manipulation code. Most work, but possibly the best end result.

2. Use some compatible language (ie Clipper) and use the current code with a little modification. As I understand it, DBase uses the Clipper language, so I assume it would be possible to use modify the current code to make it talk with MySQL, and then design a new frontend. I've had a brief look at systems such as Harbour, but would rather go with something free. Dollybase seems to be dead, sadly, as that would have been the path of least resistance. With this option we generally keep the code in a similar state to the old code, and as the shop owner has spent the past 20 years programming with DBase, something similar would keep him happy.

3. Import the data into a completely new system, such as TinyERP or something similar. Benefits are that it interfaces with our Zencart website, and involves little coding. But importing our current data would be very hard, I suspect.

Any suggestions shall engender my eternal gratitude!

Max Wilcox

---

### Post by pmasiar on 2007-07-31
If you like  TinyERP's inventory and sales modules, go with it. Change will be pain, but it will be good for next 20 years :-) 

I abandoned Clipper 15 years ago as obsolete, I am surprised there are still "dead-enders" :-) using it. TinyERP is also better use of your time: learning something marketable and new, not digging yourself deeper into the hole.

TinyERP is based on solid technology - TurboGears. I don't know about your timeframe, and if TinyERP plans to upgrade to coming TGv2.0 (based on Pylons), but many people have apps and are married to TGv1.0, you should be safe. And even if you want to upgrade later, your data are safely in MySQL, you are changing front-end only.

TinyERP is written in Python, it is easy and obvious enough so owner can learn to do little changes here and there. Because it uses decent object-relation mapper, it is not as hard as web-based front-end for a database was 3 years ago. Also templating system should be far superior to what you have now. One smart thing I like in TurboGears is templating: instead of reinventing dumb half-language, uses python! So again, it is easy for a beginner to make small customization in presentation layer.

Data conversion will be hard - because dBase is far from SQL compatible. But data are data - dump them into text, and load them. If you have time and resources, try reconversion: convert to MySQL, and then back, and compare if you got back all and correctly.

This big change is good time to change internal shop policies and workflows, to make them closer to TinyERP defaults, if it makes sense.

---

### Post by novymir on 2007-08-09
Many thanks for the suggestion! TinyERP was the one I looked at most as a potential candidate, and seems to be the best supported and most actively developed of the FOSS ERP etc programs that I've seen. The default interface leaves a little to be desired in my opinion, but it looks like developments with the web client and the unstable version are rapidly fixing that concern.

Thanks again for the comments!

Max Wilcox

---

