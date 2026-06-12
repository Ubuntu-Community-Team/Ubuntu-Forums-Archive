---
title: "wlan0 interfance gone"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by noorez on 2008-10-27
I wanted to try the ndiswrapper for my wireless card to get better support for wpa. However, after following some instructions I seemed to have lost my wlan0 interface!....It is even not listed in the gnome-device-manager....and it is not in /etc/network/interfaces

I think it happened when I did this: /etc/modules.conf:
    alias wlan0 ndiswrapper
....
How do I get wlan0 back? 

any ideas?

---

