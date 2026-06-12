---
title: "XFI sound cards in 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by bgast1 on 2008-11-01
I had used Linux solely for months but went back to windows because I could never get my Creative Soundblaster Xfi Extreme Gamer card to work in Ubuntu yet. Does it work in 8.10? I have downloaded it, burned it, and would like to install it, but not unless I can get my Xfi card to work.

---

### Post by Stex on 2008-11-01
Have you tried testing it?
Just pop in the ubuntu CD and reboot your computer, you can launch the Live CD mode to test if your sound card works without having to install ubuntu.

---

### Post by bgast1 on 2008-11-01
I am booted up into Ubuntu now. Nope, no sound. I can use my onboard sound though, but not without unplugging my xfi sound card and plugging into my onboard sound. There are things that I can do like getting a cable plug my headphones in but like most of you I would prefer an OS that works completely with my hardware. I have been trying to search for a way to make it work because I just noticed that there already is a thread here where someone is complaining about crackling noise when watching video. 

Is there a way to test with the Live CD prior to installation?

---

### Post by rsambuca on 2008-11-01
Creative Labs and linux support is fairly spotty, but I believe they did make a driver for that card, however it is 64bit only.  Try using the Ubuntu 64bit liveCD.

---

### Post by bgast1 on 2008-11-01
My system is 32bit. Does that matter? I know some people have had luck with OSS, but I have no experience with OSS and the learning curve would probably be steep even if I found instructions on how. But even if it is steep, I am willing to try to learn.

---

### Post by rsambuca on 2008-11-01
Ah.  If you have a 32bit CPU, then you can't run a 64bit OS.  Sorry, but I'm not much help on this one.

---

### Post by bgast1 on 2008-11-01
Thats ok you've helped a lot in the past:)

---

### Post by oldsoundguy on 2008-11-01
Creative still thinks that Linux will "go away"

Turtle Beach, on the other hand even hosts a FAQ and a Q&A section for Linux on it's home site.

Now, just who should we support here?

I am in the process of dumping all (that is 5) Creative set-ups. (including an X-FI Xtreme. Have to sell some crud on eBay to raise the bucks .. but it will get done!

---

### Post by bgast1 on 2008-11-03
Anyone know how to get this card working?

---

### Post by cdean on 2008-11-05
I recommend looking at this thread for answers:

[http://ohioloco.ubuntuforums.org/showthread.php?t=870001](http://ohioloco.ubuntuforums.org/showthread.php?t=870001)

It's for Hardy, but it's a start.

I'll tell you this straight up: X-Fi on Linux is a pain in the ***. The official driver requires a kernel recompile (non-trivial, but not too hard, even for a newb). The sound quality will be somewhat spotty, still.

You might be better off with the OSS driver for now until the ALSA driver is stable. Details are available at that aforementioned post.

---

### Post by pfunkman on 2008-11-06
New drivers released today. See here:

[http://ubuntuforums.org/showthread.php?t=870001&page=4post=37](http://ubuntuforums.org/showthread.php?t=870001&page=4post=37)

---

### Post by rsambuca on 2008-11-06
Hope is on the horizon!  Creative Labs has decided to open-source the X-Fi Driver under a GNU GPLv2 license.  It may take a month or two, but this is definitely fantastic news for X-Fi users.

---

### Post by gazzadtfan on 2008-11-12
I saw this link on the forum and tried to install the new drivers for the X-Fi but unfortunately I didn't have any luck. When I reboot it halts at "Installing Manual Drivers". Thats as far as I get. Luckily I'm dual-booting and can get online to the forum using Vista. Does anyone have any ideas? How long should I wait at the prompt when it says about the manual drivers? Is the only alternative a re install?

gazza

---

