---
title: "Can't get HDMI to show up as an option."
date: 2017-02-09
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-02-09
Ubuntu 16.10 server booting directly to Kodi. It is not activating the HDMI sound card. Results of cat /proc/asound/cards is a single card. HDMI is not an available choice in Kodi. I think I'm missing a module or something. Need assistance to find. This machine boots and plays sound just fine over HDMI with a Kubuntu 16.04 flash drive.

---

### Post by TheFu on 2017-02-11
I think HDMI is part of the video card driver. I'd start by looking there.
[B]
sudo lshw -C video[/B]

Look for the differences between the working (16.04) and non-working (16.10) outputs.

---

