---
title: "What's up with my internet connection?  Synaptic and Transmission issues"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by gatesdrovme2it on 2012-03-29
Hi all, I have this weird thing going on in Ubuntu 11.10.  When I open synaptic pm and hit reload, it says:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Also I noticed a very strange thing with transmission.  My torrents will up/download fine for maybe 2 seconds, then they will blink to "0 up, 0 down" like it is stalled.  They they start, then stop again and again and again.  

Are these issues related to each other?  I'm totally new to Linux so please use small words and speak slowly.  LOL

BTW, my internet acts fine both with wired and wireless connections.  I mean pages load fine apparently.

---

### Post by oklokl on 2012-03-29
sudo apt-get install qbittorrent

Transmission => I gave up long ago.

---

### Post by zombifier25 on 2012-03-29
That isn't very helpful isn't it?

For Synaptic, try using the Main Server. Open Software Source, select Main Server right in the first tab.
For Transmission... well, it's hard to tell. Torrents can get messy at times, especially if it's not a popular torrent.

---

### Post by gatesdrovme2it on 2012-03-29
Thanks zombifier; I tried different servers but no luck.  Also I have maybe 40 torrents going right now so it's not like all of them are funky.  I think the start/stop thing isn't because there is no data available on the network otherwise it would be just plain 0 up/ 0 down not the weird oscillation like it's doing.

---

### Post by gatesdrovme2it on 2012-03-29
I should also mention that in the couple months that I've had transmission working it has never done this before.  I've downloaded many hundreds of gigs with no issues.

---

### Post by gatesdrovme2it on 2012-03-30
Anyone?

---

