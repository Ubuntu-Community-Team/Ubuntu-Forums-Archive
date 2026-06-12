---
title: "How to gain speed"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-24
Hello, I'm using HP Pavilion dv4000, Intel Pentium M 1.83 GHz, 1 GB RAM. I notice that everytime download torrent (using DELUGE, awesome speed!), my other activity (firefox, thunderbird etc) will slow down (not responsive as before torrent running). This is absolutely not Ubuntu problem because I also experienced this on XP. However, does anyone know how to tweak my system to at least gain some speed (no noticeable slow down).

---

### Post by Sam Lars on 2008-05-24
I've found that the easiest speed to saturate is your upload speed.  If you use all of your upload bandwidth, loading pages or anything online will take much longer.  Depending on how much you have, try to leave 10 or 15 KB (that's bytes, not bits) of bandwidth open if you plan on doing anything online while it's running.

---

### Post by kostkon on 2008-05-24
> **Sam Lars said:**
> I've found that the easiest speed to saturate is your upload speed.  If you use all of your upload bandwidth, loading pages or anything online will take much longer.  Depending on how much you have, try to leave 10 or 15 KB (that's bytes, not bits) of bandwidth open if you plan on doing anything online while it's running.
+1
That's really what happens. Leave at least 10KB/s for you and you should be fine.

---

### Post by MrWES on 2008-05-24
Also, I don't know what kind of router you're using, or even if you are using one. I'm using a Linksys and I upgraded the firmware to Tomato, which has a couple of great features...like turning up the power on the wireless connection and a fantastic QoS (Quality of Service) scheme.

You can read more about it here:

[http://www.polarcloud.com/tomato]("http://www.polarcloud.com/tomato")

If you have a linksys router, WRT54G/WRT54GS/WRT54GLjust make sure it's supported by checking the version number

Bill

---

### Post by hyperair on 2008-05-24
Take a note of your download and upload rates in Deluge. Then right click on the icon and set the maximum download and upload rates to 5-10kbps less than whatever you took note of just now. If the problem persists, keep reducing it.

---

### Post by wariskampar on 2008-05-24
@Sam Lar; how do we know how much bandwidth we have? Can you show me which one should I alter. Sorry if my question is too stupid for you but I really dont know. Btw, the screenshot was taken after I tried alter some Upload Bandwidth figure. Dont know whether it is correct or not

@MrWES; I'm using Linksys (WRT54GC) and already know about Tomato thing. Anyway, as my question imply, I'm mediocre user so advance setting will not benefit me much:)

---

### Post by Sam Lars on 2008-05-24
[http://www.speedtest.net/](http://www.speedtest.net/)
There are more out there if you want to search Google.  Whatever it tells you for your upload speed, divide it by 8.  That's your theoretical max.  Leave about 10 KB/s and set your limit for the rest of KB/s.
For example, my connection was about 120 kbit/s off that site, which means I have about 15 KB/s after dividing by 8.  I set my limit to 5 KB/s to leave bandwidth for other things.

---

### Post by lazydesi on 2008-05-24
> **wariskampar said:**
> @Sam Lar; how do we know how much bandwidth we have? Can you show me which one should I alter. Sorry if my question is too stupid for you but I really dont know. Btw, the screenshot was taken after I tried alter some Upload Bandwidth figure. Dont know whether it is correct or not

@MrWES; I'm using Linksys (WRT54GC) and already know about Tomato thing. Anyway, as my question imply, I'm mediocre user so advance setting will not benefit me much:)

out of area , what is the appilication that will show network, processor status in that screenshot?

---

### Post by kk0sse54 on 2008-05-24
> out of area , what is the appilication that will show network, processor status in that screenshot?


conky. go into the terminal and type ```
sudo apt-get install conky
``` in order to get it. Check out the conky post in the community cafe, I believe it's in there, where people post a lot of really cool conky setups so that it shows different things with different colors or different positions on the screen.

---

