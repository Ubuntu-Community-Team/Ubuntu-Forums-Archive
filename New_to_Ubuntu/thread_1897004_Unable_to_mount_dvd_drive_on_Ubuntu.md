---
title: "Unable to mount dvd drive on Ubuntu"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by ask_ on 2011-12-18
Hello,

I am using an LUbuntu 11.10 on an HP pc.

The system is not detecting my dvdrw drive. It is a sony dvdrw.

When the system boots, in boot menu the device is listed as '3rd Slave'.

Is this the reason why Ubuntu is not detecting it?

Do we have to connect the device as 'master'? And how does one go about doing it?

Oddly enough, when I opened the cabinet, the dvd drive is connected to 'master' wire, but still bootmenu is showing it as 'slave' (not to mention ubuntu isn't detecing it at all), what am I missing here?

P.S :- please move the thread to apt subforum if it isn't suited here.

---

### Post by TeoBigusGeekus on 2011-12-18
You have to adjust the jumpers:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph03792&lc=en&cc=uk&dlc=en]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph03792&lc=en&cc=uk&dlc=en")

---

### Post by ask_ on 2011-12-18
> **TeoBigusGeekus said:**
> You have to adjust the jumpers:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph03792&lc=en&cc=uk&dlc=en]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph03792&lc=en&cc=uk&dlc=en")

Thanks,I did some changes with the jumpers,
now in boot menu, dvd drive is listed as '3rd master',earlier it was '3rd slave'. Is this a progress?If yes, can I mount the dvd drive now? If yes, how should I proceed next?

---

### Post by TeoBigusGeekus on 2011-12-18
> **ask_ said:**
> Thanks,I did some changes with the jumpers,
now in boot menu, dvd drive is listed as '3rd master',earlier it was '3rd slave'. Is this a progress?If yes, can I mount the dvd drive now? If yes, how should I proceed next?

Try and see how it goes.

---

### Post by ask_ on 2011-12-18
It is working. Thanks for the help.

Mine is a Sony DVD drive, able to play SONY dvds properly. But unable to do so with dvds of other manufacturers. Perhaps this is an issue with the dvd drive. This was the case since my Windows-XP days on this PC. 

Since I had asked about mounting DVD-drive on Ubuntu, the issue pertaining to this thread is solved. Hence, I thank you and mark this thread as solved.


Why the drive won't play other manufacturers DVDs , I will ask perhaps in another thread in the distant future(I guess I will have to update drivers or something). For now I am satisfied.

---

