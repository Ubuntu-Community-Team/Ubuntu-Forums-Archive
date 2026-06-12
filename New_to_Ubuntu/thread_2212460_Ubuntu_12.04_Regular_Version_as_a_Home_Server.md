---
title: "Ubuntu 12.04 Regular Version as a Home Server"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by scottyinfrisco on 2014-03-21
I would like to run 12.04 regular version as the OS for my home server.  I'd like to keep the possibility to use it as an extra computer. I was planning on RAID 5 and starting with 3 X 3TB HDD.  I would like to run the OS from a USB.  Does that sound good/smart? I am open to suggestions, and I am fairly handy with this stuff, just by no means an expert.  Simple is better in my mind. Thanks

---

### Post by 7sbaV8Kt5PTh on 2014-03-21
Hi, Scotty.  I did this exact thing, with smaller HDD's.  It was OK for a while, but I started using it more as a computer and less as a server.  It was amazingly slow.  So I put in a smaller HDD to put the OS on, and had the other drives in raid 0.  It ran much better and dished out movies while running normal operations just fine.

---

### Post by scottyinfrisco on 2014-03-21
That was my other option. Getting a small SSD and running the OS from there. Why raid 0? I don't fully understand the raid choices.  I plan to use this for photo storage, music storage, and movie storage.  Eventually running Plex as a streaming media center. Would raid 0 be a better choice over raid 5 for this?

---

### Post by 7sbaV8Kt5PTh on 2014-03-21
You can run raid 5 (parity) or raid 0 (striped).  I am running 0 for speed and I'm not worried about failure.  With raid 5, you can recover from a failed drive MUCH easier, just put the new drive in and let the array rebuild itself.  You probably don't need the raid 0 speed unless a) you have a lot of drives and b) need to make things as fast as possible.  On my smaller array (4 drives), I have raid 5, and it works just fine, even for gaming.

---

