---
title: "protocol suggestion parental control on internet access level for linux router"
date: 2013-08-11
forum: Programming Talk
---

### Post by bart2 on 2013-08-11
So here's the deal

I want to set a ubuntu server (lets say the current LTS release) up as router in my lan (wireless wifi and wired ethernet).
Setting up the right iptables rules shouldn't be a biggie.

I also want to restrain my kids from using the internet too much.
To accomplish this I had in mind to give everyone a personal account and login, wich they should use to be able to have acces to the internet.
The router should then either give them or not give them acces, based on time shedules.

This however, I don't know how to accomplish. Using a captive portal seems way to klunky for something you use on a daily basis.
I read something on wikipedia about PPP and PPPoe, but are those protocols really the ones I'm looking after?

Is there an existing project that achieves something similar?
Is there an implementation of the protocols I'd need, that I could easily adapt to make use from time shedules?

Thanks for your toughts,

Bart


EDIT:
After some more research I'm going to install freeRADIUS ([http://goo.gl/vYXttJ](http://goo.gl/vYXttJ)) on my machine, in combination with a MYSQL database containing the users and their time shedules.

---

### Post by ofnuts on 2013-08-11
I would do what is done the world around on free access points (hotels for guests, businesses for visitors, etc). All network access is locked except HTTP, and the first HTTP use is rerouted to a logon screen. After logon, the rest of the network ports are unlocked for some time. I'll pretty sure you'll find open source software for that.

Another technique that works quite well for kids is "Suddenly, Dad!" and/or showing them that you know (kids) or could know if needed (teenagers).

---

### Post by SeijiSensei on 2013-08-11
If you are comfortable with having all your kids conform to the same time schedule, most routers have software controls to handle this situation.  Take a look in the parental controls section of your router.   If you need to have differential rules, you would need a more sophisticated approach that uses a combination of iptables rules keyed to user names and a cron job that imposes or removes the restrictions by time of day.

---

