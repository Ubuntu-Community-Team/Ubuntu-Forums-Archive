---
title: "need audio drivers, help"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-18
I need audio drivers for my laptop...I think. I can't figure out what hardware I have, which driver to install or where to find it. 

Some help troubleshooting would be awesome! I'm totally lost on this one! New to Lubuntu and linux.

---

### Post by jerrrys on 2012-09-18
Open a terminal and enter:

lshw

That should tell the story

---

### Post by Sonoran Desert Rat on 2012-09-18
Big list, is this what is needed?  

       *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1000(size=256) ioport:1880(size=64) memory

---

### Post by jerrrys on 2012-09-18
I don't have any experience with these, but I can point you to:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AC%2797+Audio+Controller&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AC%2797+Audio+Controller&as_qdr=all&sa=Google+Search&lang=en)
[https://www.google.com/search?q=AC%2797+Audio+Controller+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=AC%2797+Audio+Controller+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Hope that helps

---

### Post by Sonoran Desert Rat on 2012-09-18
Thank you. :)

---

### Post by oldos2er on 2012-09-18
Try [http://ubuntuforums.org/showthread.php?t=161193&page=2](http://ubuntuforums.org/showthread.php?t=161193&page=2)

Also [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Sonoran Desert Rat on 2012-09-18
Using jerrrys advice I ended up on this thread, the first link in the first post:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

My speakers were turned off. :-\" Glad I started there, lol. ;)

Thanks for the help !!

---

### Post by Rodney9 on 2012-09-18
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by newb85 on 2012-09-18
Also, please mark this thread as solved.

---

