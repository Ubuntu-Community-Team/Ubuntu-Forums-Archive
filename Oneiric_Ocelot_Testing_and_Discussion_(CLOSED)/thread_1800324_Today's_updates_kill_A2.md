---
title: "Today's updates kill A2"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tajreed on 2011-07-08
At log-in, will not load Ubuntu, Gnome or Unity2d. Recovery mode is a no-go. Script ends with something regarding the bios. No problems seen in the script. Any chance to recover without reinstalling-takes forever on this Aspire laptop.

---

### Post by garvinrick4 on 2011-07-08
> **tajreed said:**
> At log-in, will not load Ubuntu, Gnome or Unity2d. Recovery mode is a no-go. Script ends with something regarding the bios. No problems seen in the script. Any chance to recover without reinstalling-takes forever on this Aspire laptop.

If you can get to a tty try to restart lightdm
```
sudo service lightdm restart
```Now see if you can boot:

---

