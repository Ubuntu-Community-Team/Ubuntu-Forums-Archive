---
title: "Why Kubuntu live cd takes more memory than ubuntu?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by sharks on 2008-05-15
I have Kubuntu and ubuntu 8.04 live cds. While Ubuntu takes memory around 270 mb , kubuntu takes around 750 mb. Why this happens?

---

### Post by candtalan on 2008-05-16
I have never looked at memory, but it would possibly be that kubuntu uses KDE which is a larger environment with more ongoing activities and menu options.

---

### Post by shifty_powers on 2008-05-16
well thats what i thought at first, but 500meg is a BIG difference,.....

---

### Post by Golem XIV on 2008-05-16
I'd say you could spark up the System Monitor (in Ubuntu) and ksysguard (in Kubuntu) and look at what's eating the memory in each one.

You can also use the **top** command from the terminal in both flavours.

---

### Post by kerry_s on 2008-05-16
kde is bigger and has more stuff tied together, meaning there's more daemons running then would be on gnome. when kde starts it starts everything kde loading as much into memory as it can.

---

### Post by MONODA on 2008-05-16
they both use close amounts of ram but KDE uses more. The reason why you see such a large difference is because the system monitor in KDE measures the real amount of ram used, including caches while the gnome system moniter does not measure memory caches. You can properly compare them using the top command from the command line, or using the htop command which does not measure caches.

---

