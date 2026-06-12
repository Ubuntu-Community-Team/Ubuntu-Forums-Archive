---
title: "General wifi Glitchyness since Upgrading to Artful"
date: 2018-02-22
forum: New to Ubuntu
---

### Post by holsten on 2018-02-22
Hi hi,

I have been using Ubuntu for last 6 months - very new to Linux. I recently upgraded from Zesty to Artful. I have a VPN installed, and when I turn off the VPN in order to access certain repos, my access to the internet is lost. A friend of mine tried to get around this by adding google nameservers to / etc / resolv.conf 8.8.8.8, 8.8.4.4, which worked at the time, but since I've had issues switching from vpn to non-vpn wifi.

One thing I have done which helped was:

sudo dpkg-reconfigure resolvconf

Say yes to "prepare /etc/resolve.conf for dynamic updates?"

sudo reboot

But still having issues switching between vpn and non-vpn. Also my connection to my wifi hotspot on my phone is totally not working - again it appears like I am connected on the networking centre, but when I try open web pages, it's as if I'm not connected at all.

Very grateful for any help/advice you can give :D

---

