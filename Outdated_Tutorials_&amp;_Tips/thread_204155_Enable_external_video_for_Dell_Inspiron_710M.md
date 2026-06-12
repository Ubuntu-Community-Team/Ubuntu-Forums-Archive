---
title: "Enable external video for Dell Inspiron 710M"
date: 2006-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by falim on 2006-06-26
Hi all, 

After struggling for days, I have finally figured out how to enable the external video for Dell Inspiron 710M with much googling around. Hopefully this will be useful to anyone using the same model. 

Add these under the Device section in the xorg.conf

```

Option    "MonitorLayout" "CRT,LFP"
Option    "Clone" "true"
Option    "DevicePresence" "true"

```

This will enable the external video. However, the output of the video will be the resolution of you screen. To solve this, I set my resolution to 1024x768 when Im using the external LCD and back to native resolution when I'm not using the external video. To enable your native resolution during boot, edit the default file /etc/default/915resolution and set according to the following.

```

Mode=7e

XRESO=1280
YRESO=800

```

If your screen is not running @ native resolution, apt-get 915resolution and search this forum for some help on how to enable the native resolution. I think it will auto work after install. Cant remember what had happen. hehee.

After all this, I do have 1 small problem. I want to use my External LCD using its native resolution which is 1280x1024 but I only have the option up to 1024x768 in GNOME, I haven tried KDE but I believe is the same. Tried playing around with the resolution in 915resolution and xorg.conf but it does not enable the 1240x1024 in my screen resolution selection. Does anyone has any idea how? 

PS: Using i955crt does not work for this model, or at least for me because the the output looks fuzzy.

---

