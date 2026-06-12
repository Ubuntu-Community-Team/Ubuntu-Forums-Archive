---
title: "No More Support for Atheros Cards in Hardware Drivers"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Patrick793 on 2008-11-15
So, I was getting wifi setup on my new install of Intrepid, and I'm not sure if this was to happen. I installed the linux-backports-modules-intrepid-generic, and when I rebooted to disable Support for Atheros 802.11 wireless LAN cards from Hardware Drivers, it was gone.

Everything is working fine though. I am on wireless right now. Support for 5xxx series of Atheros 802.11 wireless LAN cards appears, but not Support for Atheros 802.11 wireless LAN cards.

Is this normal, or is something wrong? Because other than Support for Atheros 802.11 wireless LAN cards being gone, everything is normal.

---

### Post by cariboo on 2008-11-15
This is one of those deals where we say it it works why worry about it. The reason the driver doesn't show up in Hardware drivers is that it is semi-official and hasn't been excepted in the regular repositories yet.

Jim

---

