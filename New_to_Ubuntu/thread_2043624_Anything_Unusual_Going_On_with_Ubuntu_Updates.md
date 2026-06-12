---
title: "Anything Unusual Going On with Ubuntu Updates?"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by GregA on 2012-08-17
For the first time in 5 or more years, the standard update process (am running Kubuntu 12.4x), . . . resulted on one machine (desktop) losing Flash capability, and the other (a laptop) losing wireless connectivity.

On the desktop, after 30-40 minutes from update finish, I received an update (light bulb) in my panel,  indicating flash didn't install - - and by accepting the prompt, a terminal window initiated a manual update - - which did complete the flash update download & install.

On the lappie, which is a very Linux friendly Acer with all Intel coms and graphics   -- - the proper networking packages were not updated, totally hosing my wireless.   As I didn't have a lot customized on this machine, I did a quick re-install of Kubuntu 12.4 from the original live CD.    All functionality was restored.    But, as before, the package/update manager (muon) indicates not all is normal (all updates are not "auto installable").

Anyone else running inti this?

---

### Post by QIII on 2012-08-17
Not I, but you are not the first to mention this.

Were you offered a partial upgrade?

---

### Post by GregA on 2012-08-17
Just a short update:   I think the reason the "system updates" were problematic was due to:
.
a)   Lots of package updates (100+)
b)   Slow connection speed (60-100 kbps) due to primetime congestion, and limited network bandwith
c)   Non-optimal download server assignment 

All above resulted in a partial update.   This is especially true of the laptop with the broken networking.   

As of this morning, all is good.   I updated the laptop during lull hours 9am Central Time (US) - - download speeds ranged from 400 to 1200 kbps.   Still, Flash didn't download & update until I accepted a system notice (thereby initiating non-gui retrieval and install of Flash) - - strange, compared to past updates.

Anyway, final lessons learned for me is to examine network speed and congestion before initiating system updates.

---

### Post by oldfred on 2012-08-17
Are you using the main server or one of the mirrors? 

This pings so it may not be best download, but often is better. I find two or three that seem faster at most times.

System, Administration, Update Manager. Click on settings button on bottom left and in first tab - Ubuntu Software is a combo box on site used to update. Click on combo box and choose other. Then Select Best Server.

---

