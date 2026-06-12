---
title: "GFX Card"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by jayfisher on 2008-11-24
ATI 9550 Pro... Compatibility with ubuntu and compiz.
i know its a preety old card but unfortunatly i have a APG slot so i have a limited choice. but im just looking for something to run compiz nicely and video streaming. Opinions Appreciated.

Jayfisher

---

### Post by go_beep_yourself on 2008-11-24
It was really tricky to get my brother's ati card working in Linux. I used the alternate nongui installer because I had been using that to setup raid and the open source driver didn't work with his ati card anyways. After getting Ubuntu installed, immediately after loading the splash screen, his screen went completely white when Ubuntu would try starting the graphics, so, I booted it into single user mode (known as recovery mode in Ubuntu), removed gdm login manager so the graphics wouldnt try to automatically start, went back to runlevel 2, installed the ssh server. Then, from my computer, I logged into his with ssh X forwarding so I could run a gui app called jockey-gtk that I needed to install the ati driver. I told you it was tricky. After that, the graphics would work and I installed gdm back on his computer. You are usually much safer to go with Nvidia cards in Linux.

---

### Post by go_beep_yourself on 2008-11-24
P.S. I don't know about that ATI card specifically but you can look here to see what other Ubuntu user's experiences have been with it.

[http://www.google.com/search?q=site%3Aubuntuforums.org+ATI+9550+Pro&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=site%3Aubuntuforums.org+ATI+9550+Pro&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by jayfisher on 2008-11-24
Pfft, my on board GFX wont work so i buy a new one and that wont either. Thats just my luck O.o

---

### Post by go_beep_yourself on 2008-11-25
> **jayfisher said:**
> Pfft, my on board GFX wont work so i buy a new one and that wont either. Thats just my luck O.o

Are they both ATI? I suggest getting a Nvidia GFX card next time or trading yours for one. Also, did you try searching the forums to see if anyone else got the same model of ATI card working and how they did it?

---

### Post by Izek on 2008-11-25
I've had bad experiences with my ATI Radeon HD 3200 (Integrated) on Ubuntu 8.10 so I suggest NVIDIA like many people will probably suggest. Though the bug I reported about how fglrx hangs a lot with compiz/etc. has now managed to get to confirmed status. Many people seem to have problems with certain NVIDIA cards as well, I suggest looking around before going out and buying one.

---

### Post by go_beep_yourself on 2008-11-25
> **Izek said:**
> Many people seem to have problems with certain NVIDIA cards as well, I suggest looking around before going out and buying one.

I'm having no problems at all with my Nvidia 8800 gts. Everything works great. I think it's only really old models of Nvidia cards that had problems.

---

### Post by Cracauer on 2008-11-25
This card is old enough that you don't need the binary drivers. I'll do with just Xorg and DRI. Should run pretty much fine.

---

