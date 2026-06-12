---
title: "Random Shutdowns? And backing up xorg"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by dgbearcat on 2008-04-22
I am running the latest version on 8.04, and was delighted to find that my standby and hibernate worked perfectly.

However, recently I've noticed that it just randomly has started shutting down, with X going away and just seeing a few warnings fly by before it shuts down. 

I tried a recovery, but all that seemed to do was to reset all of my config to default and make my terminal apparently cease working with any usable speed (takes forever to do anything, about 10 seconds to tell me that something isn't a command. I tried emerald --replace about 5 minutes ago, and the prompt still hasn't come up, and nothing has happened).

I saw somewhere that it may be that my BIOS is doing it because it's getting too hot, but I didn't see anything in my startup settings to change that. 

Was wondering if anyone had any ideas on this, and also if they could tell me how to back up my xorg so that I can reload it if this happens again, or let me know if it may be automatically backed up and if it's around somewhere.

---

### Post by Hospadar on 2008-04-22
well what exactly are you talking about backing up your xorg?  If you're talking about your xorg.conf (the configuration file for X), you can back that up with something like ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` which would copy it to "xorg.conf.backup" and if something went funny you could copy it back.

But I'm not sure that's what you're really asking about.  The only time your xorg.conf is changed is when you change it, and I don't think it would have anything to do with reboots.  It's possible it is a heat problem, you may want to look into some hardware temp monitors like "lm-sensors" (install it from synaptic) and take a look at what kind of temp your cpu is running at.  I'm not totally sure how to use lm-sensors, but you can probably figure out with a little googling.

---

### Post by aimpau on 2008-04-22
Check your Bios, probably your CPU is overclocked through jumperless technology.

---

### Post by dgbearcat on 2008-04-22
Yeah, I wanted to back up the conf file, but I wasn't sure where it was. I'm still pretty noobish, although I'm slowly learning. Doesn't the conf file contain things like what your settings are overall? Things like programs that load on sessions, your display options, etc?

For some reason, lm-sensors doesn't seem to find any kind of sensors on my board, so I guess I'll have to settle for "damn, my comp is feeling kinda hot".

---

### Post by Vic Morgan on 2008-04-22
Hi, I hope that it's OK to add this (related) query. I've been having all sorts of problem with installing my Nvidia drivers, but it now seems that the configuration is not being saved over reboot. When I run the Nvidia configuration utility and select the 'save configuration' button it says that it cannot create a new X config backup. Why would this be? I've generated so many backup files that I've deleted the lot and now only have xorg.conf. Is this a script problem?
By the way dgbearcat you can look at your file with 'vim /etc/X11/xorg.conf'.

---

