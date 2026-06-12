---
title: "Broadcom Wi-Fi problem on 19.04"
date: 2019-07-01
forum: New to Ubuntu
---

### Post by petarbg on 2019-07-01
Hello guys, 

I'm new to Ubuntu. When I tried to install 19.04 directly in "Settings" I didn't have Wi-Fi option at all. What I did is, I installed the 18.04.2 LTS and it automatically detected my Wi-Fi and from there I updated to 18.10 and afterwards to 19.04.

Is there a way I can enable the Wi-Fi without going through so many upgrades, since I would like to be able to just install the latest version? If I connect the laptop to the ethernet cable, will it automatically download drivers or I must do something else?

---

### Post by geoff07 on 2019-07-02
It may simply be that the driver is not enabled. Go to Software and Updates/Additional Drivers. See if the driver is listed. If it is, select it. It won't be initially selected because it isn't an open-source program. If it isn't you need:

sudo apt-get install bcmwl-kernel-source [this works with mine, depending on your model of card it might be different for you.

That gets and installs it. May take a while.

---

