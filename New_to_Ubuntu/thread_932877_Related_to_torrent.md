---
title: "Related to torrent ?????"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Urvish on 2008-09-28
How can I increase my torrent downloading speed in UBUNTU 8.04 ????
(I have internet with speed 1-2 MBPS) PLZ help me

---

### Post by PocketDog on 2008-09-28
The best thing to do (apart from right-clicking a download and choosing 'ask tracker for more peers') is try a different client and see if that helps. Deluge is popular (I haven't tried it) or Azureus for something almost infinitely configurable. There's also rTorrent which people have reported getting good speeds with, but it has no GUI so give it a miss if you're not comfortable with the command line

---

### Post by Locke_99GS on 2008-09-28
Setup port forwarding - or use Deluge, which can make a lot of connections, even without proper port forwarding.

---

### Post by hyper_ch on 2008-09-29
run UPnP... limit the upload to about 90% of your max upload speed. Make sure you have at least 10kb/s left for upload - especially when you also use DHT....

---

### Post by Tom--d on 2008-09-29
I had this problem.
Move the port to something like 53539 (its just made up. You can have port 1-65000odd, I dont know how many there are but its like 60k) and grab yourself a static IP and on your router, forward your port on your ip.

Your speeds will become faster, at lot faster.
No need for uploading.. well, I don't >.> and still get high speeds :D

Just FYI, I use Transmission, the latest one.
If your router has UPnP, Transmission should forward the port for you. Only if your router has UPnP. Same with other bittorrent clients.

---

### Post by kpkeerthi on 2008-09-29
> **Tom--d said:**
> 
No need for uploading.. well, I don't >.> and still get high speeds :D


Thats stealing :) Torrents survive by sharing bytes mutually among the peers. If you download using torrents, you should give back something, if not all, in return. 

Not all trackers allow zero uploads. Some trackers may stop your downloads if they find that you are not giving back sufficiently (by disallowing uploads).

---

### Post by Tom--d on 2008-09-29
> **kpkeerthi said:**
> Thats stealing :) Torrents survive by sharing bytes mutually among the peers. If you download using torrents, you should give back something, if not all, in return. 

Not all trackers allow zero uploads. Some trackers may stop your downloads if they find that you are not giving back sufficiently (by disallowing uploads).

I know. I get good speeds, im not complaining :p

I share on Linux distros.

---

### Post by rsambuca on 2008-09-29
Most security experts recommend turning off uPNP and manually forwarding your required ports.

---

