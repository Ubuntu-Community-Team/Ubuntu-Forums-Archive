---
title: "Lag lag everywhere"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by rahul25 on 2014-10-25
When I load the system and everything boots fine the application takes time to run and in search option I have to wait for the letters to see it takes around 2-3 seconds. My laptop is having core 2 duo processor and 2 gigs of ram

---

### Post by overdrank on 2014-10-25
I see in your other threads you are running it via USB drive. This I believe is the reason for the lag.

---

### Post by rahul25 on 2014-10-25
I know I did it using USB and many people do so and work fine, but I have downloaded it on the hard drive,  I cannot use cd as drive is not working properly,  can I connect it to external USB drive and run it??  Looks like all the problem in installing in the world fell upon me :(

---

### Post by DuckHook on 2014-10-25
> **rahul25 said:**
> ...but I have downloaded it on the hard drive...:(...You have not provided much HW info to go on. However, my hunch is that if your machine is a duo core, then it is relatively old and therefore also has an older GPU. This is likely the cause of what you call "lag", because your system is having a hard time painting your screen in all its 3D glory (Unity no longer comes with a 2D option after 12.04). You can try posting the results of:```
sudo lshw -short | egrep "proc|display|mem"
``````
lspci -v | grep -iA9 vga
```...so that we can better understand what system you have, or, more likely the more fruitful exercise: change to a leaner flavour of 'buntu like Xubuntu or Lubuntu. Both of these lighter flavours get rid of 3D and other bloat for better performance. Your machine is probably capable of Xubuntu. Lubuntu is one of my personal favourites, but new users often find it too spartan.

---

### Post by Mike_Walsh on 2014-10-25
> **rahul25 said:**
> I know I did it using USB and many people do so and work fine, but I have downloaded it on the hard drive,  I cannot use cd as drive is not working properly,  can I connect it to external USB drive and run it??  Looks like all the problem in installing in the world fell upon me :(

I'm running Lubuntu 14.04, installed to a partition on an external USB hard drive, and it runs fine; no lag to speak of at all.

My system is considerably older than yours; 10 yrs old, and running a single-core Athlon 64 with 3 GB of RAM. I'm also dual booting /sda with Ubuntu & Zorin.....and running Xubuntu, Kubuntu & Puppy 'Slacko' each from their own dedicated flash drive. You do expect a certain amount of 'lag' from an install on a flash drive, it's true; but the response time is perfectly acceptable for what I use them for...

I guess it all boils down to what you, personally, feel to be an acceptable response time. It's rather like drag racers , or F1 teams, trying to shave a couple of extra 100/ths or 1000/ths of a second off their times. It's relatively inexpensive to achieve a certain level of response; but to go beyond that point, you have to be prepared to invest serious amounts of time, effort & money into achieving that goal.

Regards,

Mike. ;)

---

### Post by Rob Sayer on 2014-10-26
When I first installed ubuntu it was the 'default' version with the Unity DE.  This was on a relatively modern laptop with an i3 and 4Gb.  It was too slow for me, and you can't speed up Unity with setup like you can with KDE, which that machine now runs.  I'm not surprised you find it slow.

---

