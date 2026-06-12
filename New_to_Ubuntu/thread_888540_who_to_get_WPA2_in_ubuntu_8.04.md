---
title: "who to get WPA2 in ubuntu 8.04?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by appoloin on 2008-08-13
hi guys,

my work network runs there wireless on wpa2 encryption but seems like i only have wpa.. how to get wpa2?

---

### Post by brian_p on 2008-08-13
> **appoloin said:**
> hi guys,

my work network runs there wireless on wpa2 encryption but seems like i only have wpa.. how to get wpa2?

wpa requires TKIP and CCMP (AES) is optional. wpa2 requires CCMP (AES) and TKIP is optional. So go ahead and try. You should be able to connect.

---

### Post by ilexius on 2008-08-13
Hi,
what you are looking for is wpasupplicant I think. This should provide WPA2 support, as I read this in the description:
" WPA and WPA2 are methods for securing wireless networks, the former
using IEEE 802.1X, and the latter using IEEE 802.11i. This software
provides key negotiation with the WPA Authenticator, and controls
association with IEEE 802.11i networks."

I'm using gnome NetworkManager for WLAN with WPA2, I can select this from the drop-down menu. But you should be able to connect to WPA2 without any upgrades I think.

Hope this helps!

Cheers,
Thomas

---

### Post by cozmicharlie on 2008-08-13
If ilexius's suggestion does not work (wpa support is iffy in the Network Manager that comes in Hardy) then you could try loading the newest version from the Network Manager maintainer Alexander Sack.  It has better support for wpa2.  I have been using it and it is very stable and works great.  To get the latest version you simply add the commands below and it will automatically upgrade.

Open system>administration>software Sources and click "add".  Add these lines (one at a time).

```
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main

deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main 
```

Reload and close.  The upgrade manager should appear with the upgrades listed and just hit OK.  You may have to reboot I don't remember.

Enjoy

---

### Post by axelsvag on 2008-08-23
Thank you very much for your advice. After two months of searching finally I got my network working.

---

### Post by Radioactiveroach on 2009-04-21
Thank you all so much xD

---

