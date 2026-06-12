---
title: "Comparison of rtorrent and transmissionbt: I need some explanations"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by aimpau on 2008-09-26
I have been comparing the latest stable release for both rtorrent and transmission and here's what I've observed:

First, just to be clear: I love both.
Now, transmission definitely reports that I have DL speeds of upto 40KBps which is very excellent. However, it takes a full 11mins to download a 8MB of a single file and it's the "Have" label in the details, not just the verified. In contrast, rtorrent RARELY gives me a reading of 40KBps, but gives me around 20 - 35 KBps. However, it downloaded 20MB of the same file in just 11mins.

Here are my settings:
Actually, I have almost the same settings for both and I didn't just tried it once but well over 10 times for each client with that same single file. Now, I know transmission has no DHT but I disabled DHT in my rtorrent. Also, I disabled port forwarding for both. Both allow encryption incoming and outgoing as well as unencrypted. Both have peer exchange.

I'm really stumped. I've tried researching but I can't seem to find any explanation on this. I like transmission's GUI but I kinda wish it has the "speed" rtorrent.

---

### Post by Xiong Chiamiov on 2008-09-28
40 KBps is not that great.  500 is decent, although it depends on the swarm, of course.

I don't think rtorrent has DHT enabled in the version in the ubuntu repos, since it's not in the one in the main Arch repos.

It's probably just a difference in which peers decided to connect to you and such.

---

### Post by sloggerkhan on 2008-09-28
Have you tried deluge? [Http://www.deluge-torrent.org](Http://www.deluge-torrent.org) 
It's my favorite, but if you like rtorrent, it might be better. Deluge is a bit more featureful than transmission, though.

---

### Post by Nepherte on 2008-09-28
I have some mixed feelings for rtorrent as well. It's a great program but the download speed is on the low side. The version in the ubuntu repositories has DHT. Though the last time, when I forwarded the necessary ports, I got 1.37MB/s down. Very strange since I can get that speed with for example deluge, without forwarding ports.

---

