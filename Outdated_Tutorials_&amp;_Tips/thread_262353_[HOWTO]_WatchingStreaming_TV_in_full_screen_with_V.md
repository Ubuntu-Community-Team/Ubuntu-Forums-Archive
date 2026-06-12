---
title: "[HOWTO] Watching/Streaming TV in full screen with VLC"
date: 2006-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Green_Star on 2006-09-21
We can watch TV using VLC, this is easy way and you can do this if you have trouble configuring Mythtv. 

VLC->File ->Open Capture Device.. ->Select 'PVR' tab

Device = /dev/video0
remaining all leave as default. click 'ok' and enjoy your tv in VLC. 

If you want to change the channel use following command in other terminal. '#' is your channel number.
> ivtv-tune -c # -d /dev/video0
By the way using this we can even stream the tv to other computer. Check the 'Stream Output' box and click the 'Settings' button in PVR tab.

For more details go the following link
[http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html)


-cheers

---

