---
title: "Unable to connect to 802.1x wireless"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by nikhil.nikki on 2008-07-02
I freshly installed Ubuntu 8.04 a few days ago on my laptop after using Ubuntu 7.10. I am unable to connect to my University's 802.1x wireless in Ubuntu 8.04 but I am able to connect to normal wireless networks. Tried searching the forums but could not find the solution. Could anyone help me out connecting to 802.1x wireless from Ubuntu 8.04.

Wireless Security: WPA Enterprise
EAP Type: PEAP
Key Type: Dynamic WEP
Phase2 Type: MSCHAPv2

Thanks for the help in advance

---

### Post by jbrown96 on 2008-07-03
Don't connect to  802.1x network. This is supposed to be only for wired connections that require authentication. You want to connect to "other wireless network". Then choose WPA Enterprise and you can fill out the info from there. I have the same setup at my uni, and it is difficult getting it to consistently work. You might need to disable IPv6 also.

---

