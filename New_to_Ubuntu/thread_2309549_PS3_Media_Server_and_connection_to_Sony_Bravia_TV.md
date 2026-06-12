---
title: "PS3 Media Server and connection to Sony Bravia TV"
date: 2016-01-11
forum: New to Ubuntu
---

### Post by andyriome2 on 2016-01-11
Hi

I have installed PS3 Media Server on my Ubuntu 15.10 desktop and added a connection to my MyBookWorld NAS drive. Restarting the PS3 Server and the tick went green and said the connection was successful. The other configuration I did was to go into the renderer folder and create a new config file for my Sony Bravia TV (KDL32W5810) as it is not listed. Turning on my TV, and going to the Home and selecting Video, I could not see the PS3 Media Server listed as an icon, but my NAS folder is.

Is there something else I need to do with Ubuntu and/or with the PS3 Media Server to get this working and stream video content from Ubuntu/Mybookworld to my TV?

---

### Post by SeijiSensei on 2016-01-11
As I recall PS3 Mediaserver uses DLNA which means the television would need a network connection to see it.

Can you just connect the TV directly to the Ubuntu box with HDMI?  Then you can play the files with SMPlayer or something similar.

---

### Post by andyriome2 on 2016-01-11
The PS Media Server would have a network connection by virtue of the Ubuntu box being connected to my Network Router and this is how my Ubuntu box can see my NAS and equally the NAS can see my TV.

However, there is a problem that the TV and the Ubuntu are in two completely different rooms and it won't be possible to connect them with a cable of a massive length

---

### Post by SeijiSensei on 2016-01-12
I realize the Ubuntu box is on the network, but does the TV itself also have a network connection on the same subnet?  There's a diagram on page 54 of [http://pdf.crse.com/manuals/ADJ5100121.pdf](http://pdf.crse.com/manuals/ADJ5100121.pdf) that shows the TV connected to a router via its Ethernet port.

---

