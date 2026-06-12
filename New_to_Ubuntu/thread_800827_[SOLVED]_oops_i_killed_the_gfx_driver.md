---
title: "[SOLVED] oops i killed the gfx driver"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by monkspeed on 2008-05-20
please help, i went into system > administration > screens & Graphics and changed the graphics driver from Intel i810 to 945 (i have a laptop with i believe Intel 945GM graphics hardware)
after i logged out, all i get is a black dos screen and this:

* Starting NTP server ntpd [ok]
* Starting anac(h)ronistic cron anacron [ok]
* Starting deferred execution scheduler atd [ok]
* Starting periodic command scheduler crond [ok]
* Checking battery state... [ok]
* Running local boot scripts (/etc/rc.local) [ok]

and thats it, nothing else, no desktop, nothing.

If someone could please help me get it back to the i810 driver for now and maybe tell me how to go about putting the correct gfx driver on i would be most greatful.

Thanks.

---

### Post by monkspeed on 2008-05-20
solved ~ i typed 

sudo dpkg-reconfigure -phigh xserver-xorg

into the recovery console and restarted.

---

