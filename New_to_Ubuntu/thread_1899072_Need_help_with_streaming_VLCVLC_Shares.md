---
title: "Need help with streaming VLC/VLC Shares"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by EddieNYC on 2011-12-22
Hi all.

Ive been having a few issues trying to get to stream (externally) via VLC-SHARES.

I can access the Dashboard both internal to my network and external as well but am having errors when attempting to open a stream either from a PC or from my Android.

I have setup port forwarding in my router for other applications with no problem but it seems to me like the VLC SHARES is not listening in on the ports designated because I am checking via open port check tool and they are still coming up CLOSED.

Is there anyone that can help me get this to work as I have automated media downloading and can stream internal via my LAN but would like be able to stream when I am away from home.

ON a side note....

I know I can do this from VLC Player but for some reason I can't get VLC Player to open after installing it. Thats a different topic though.....

---

### Post by Ximarx on 2012-01-05
Ports are (default): 
80 for gui
5554 for streaming using rtsp protocol (for android)
8081 for streaming using http protocol (and rtmpdump)

Check your params if you changed it in 

[http://localhost/vlc-shares/outputs](http://localhost/vlc-shares/outputs)

---

