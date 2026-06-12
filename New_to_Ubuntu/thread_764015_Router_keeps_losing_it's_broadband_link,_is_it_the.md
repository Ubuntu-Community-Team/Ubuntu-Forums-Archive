---
title: "Router keeps losing it's broadband link, is it the isp or my pc."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by philinux on 2008-04-23
Any help appreciated. No error messages in messages.log. It auto reconnects by the way within a few seconds.

It's a Siemens Gigaset SE587

---

### Post by TeoBigusGeekus on 2008-04-23
Overheating perhaps?
Mine does the same sometimes, it's a LevelOne.

---

### Post by riven0 on 2008-04-23
Which service do you have? I've got Verizon DSL and I've got the same problem. After 3 years of service with no problems, it suddenly disconnects out of the blue. I've also got static on my phone, which is causing the problem. I've tracked it down to an outside line. Most likely, it's cut, but Verizon is being lazy about fixing it. 


BTW, have you also checked your syslog, /var/log/syslog, for problems?

---

### Post by Cypher on 2008-04-23
Are you losing your connection between the PC and router, or router and ISP?

---

### Post by philinux on 2008-04-23
> **Cypher said:**
> Are you losing your connection between the PC and router, or router and ISP?

Thanks for all replies. It's losing it between the router and the ISp.

It's warm but not hot.

---

### Post by eriqjaffe on 2008-04-23
> **philinux said:**
> It's losing it between the router and the ISp.The chances of it being your PC are pretty much zero, then.

You could try replacing the cable between the modem and router, and see if conditions improve.

---

### Post by Cypher on 2008-04-23
Is this a recent thing or has it always done this? If you're losing your connection to the ISP, the first thing to do is to call them up and have them run a diag on their side to the modem. They can tell you if the modem is having issues.

---

### Post by philinux on 2008-04-23
> **Cypher said:**
> Is this a recent thing or has it always done this? If you're losing your connection to the ISP, the first thing to do is to call them up and have them run a diag on their side to the modem. They can tell you if the modem is having issues.

It's only really been doing it lately. I switched to tiscali max and it think it started then. But the dropouts have got more frequent.

---

### Post by Golem XIV on 2008-04-23
Maybe your DHCP lease is expiring and the reassigning of a new IP is going slowly?  The DHCP refresh should be in the router logs, however.

---

### Post by JamieKG on 2008-04-23
> **philinux said:**
> It's only really been doing it lately. I switched to tiscali max and it think it started then. But the dropouts have got more frequent.

Have a look at you adsl stats in you router unless your are on a cable connection

---

### Post by shad0w_walker on 2008-04-23
My personal suggestion would be ring up tiscali and ask if they can check your line. Also going through any troubleshooting they recommend would probably be a good idea just to clear out the usual suspects.

---

### Post by forestpixie on 2008-04-23
Spent about 6 years on the phone to Tiscali today (at least it seemed like it :) ) - for my mum - she had a similar problem - it would cut out and then reconnect. The time between reconnects got longer and longer and then finally it wouldn't. It was all at their end, they did a line check, changed some setting and it was fine - at least I haven't had another phone call so I assume it's still OK.

Funnily I phoned them on Sunday to get prices rather than do it online - got through to someone in sales - 

"how can I help"
I'm looking to change my ISP
"Oh I'm sorry we sell the internet can we help you with that"

---

