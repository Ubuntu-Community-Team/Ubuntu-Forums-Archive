---
title: "Remote Desktop &amp; bVNC Android app"
date: 2016-02-20
forum: New to Ubuntu
---

### Post by Qbi_Wan on 2016-02-20
Hi. I'm interested in using app mentioned above, but[ instructions for Ubuntu]("https://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop") are based on v 7.10 (Gutsy Gibbon) which had settings option "Remote Desktop". I couldn't find it 12.04 so I have googled it (actually duckduckgo-ed it) & I tried to use [these instructions]("http://c-nergy.be/blog/?p=5305"). Didn't work out. What can I do to access mu Ubuntu desktop with this app?

---

### Post by newbie-user on 2016-02-22
Don't get confused with VNC and RDP. The bVNC app will only do VNC connections, so you have to have a VNC server running on your Ubuntu box. There are a number of VNC servers to choose from: tightvncserver, vino, etc. A list can be found here: [https://help.ubuntu.com/community/VNC/Servers]("https://help.ubuntu.com/community/VNC/Servers")

If you want to use RDP, you'll need to install xrdp on your Ubuntu box, and then you'll need an RDP client for your Android device.

---

