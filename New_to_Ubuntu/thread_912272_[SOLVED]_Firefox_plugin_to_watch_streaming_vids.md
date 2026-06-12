---
title: "[SOLVED] Firefox plugin to watch streaming vids"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-06
I'm running Linux Mint. I'm trying to watch this, for example, [channel]("http://wwitv.com/portal.htm?http://wwitv.com/television/index.html?http://wwitv.com/tv_channels/b1920.htm"). When I try to watch it, though, it says I need to install missing plugins, and when I click on it, it says "unknown plugin (video/x-ms-asf).

I have flash, vlc, ubuntu restricted extras, etc. I don't get what the problem is.

---

### Post by mikewhatever on 2008-09-06
It works for me with Media Player Connectivity:
[https://addons.mozilla.org/firefox/addon/446](https://addons.mozilla.org/firefox/addon/446)

---

### Post by wolfen69 on 2008-09-06
it works for me with the mozilla vlc plugin. make sure to remove totem-mozilla first and any others.

---

### Post by AndyCooll on 2008-09-06
It works fine for me with the default totem-mozilla plugin (you can install totem-vlc or totem-mplayer if you prefer, but it shouldn't be necessary). 

For me, when I do a new Ubuntu install I usually start by opening up Totem and attempting to play a standard video. It then says that it needs to download some codecs which I then select and let it do. After that whenever I play a video in Firefox it just works.

I think in effect I've installed the gstreamer good, bad and ugly codecs. You can always check and make sure they've been installed.

:cool:

---

