---
title: "Wine not working as fast."
date: 2014-11-25
forum: New to Ubuntu
---

### Post by alexfurnell94 on 2014-11-25
Hello all I'm new to this forum. Anyway, I can't help but notice that my computer seems to struggle with games on Wine even though it is far more than capable on Win7. My computer can easily play Red Faction Guerrilla on Windows but on Wine it somewhat seems to struggle a bit. I have a GTX-660 and I7 CPU, can anyone shed any light on this please? Thanks :).

---

### Post by sandyd on 2014-11-25
> **alexfurnell94 said:**
> Hello all I'm new to this forum. Anyway, I can't help but notice that my computer seems to struggle with games on Wine even though it is far more than capable on Win7. My computer can easily play Red Faction Guerrilla on Windows but on Wine it somewhat seems to struggle a bit. I have a GTX-660 and I7 CPU, can anyone shed any light on this please? Thanks :).
Hi, and welcome to the forums :)

Have you installed the proprietary drivers for your card using the Additional Drivers Utility?
They may offer higher performance than the included open source nouveau driver.

*Side Note*
A lot of times, you cannot expect WINE to run software/games as well as Windows does - mainly because it isn't Windows. Software and games are sort of a hit/miss depending on the particular game/application. As such, if you have the disk space, a Dual Boot between Windows/Linux may be optimal for your setup, as it allows for the switching between Windows and Linux. If it is possible, finding equivalent linux-native applications to replace windows applications will allow you to use Linux at full speed.

That being said, [Red Faction Guerrilla has a Silver entry on WineHQ]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=10386")

---

### Post by alexfurnell94 on 2014-11-25
Thanks.

I was sort of expecting something like this to happen, but at the same time was also expecting it to be faster. I did think that Wine wouldn't run certain games as fast, especially Red Faction Guerrilla. In the meantime I'll just experiment with it and see what works and hopefully, it'll be even better than on Windows. I always use my Nvidia drivers and never change from it. I'm guessing the proprietary drivers are the one's that are installed with Linux right?

---

### Post by sandyd on 2014-11-26
> **alexfurnell94 said:**
> Thanks.

I was sort of expecting something like this to happen, but at the same time was also expecting it to be faster. I did think that Wine wouldn't run certain games as fast, especially Red Faction Guerrilla. In the meantime I'll just experiment with it and see what works and hopefully, it'll be even better than on Windows. I always use my Nvidia drivers and never change from it. I'm guessing the proprietary drivers are the one's that are installed with Linux right?

No, by default, Ubuntu uses open source drivers, you will have to activate the Proprietary drivers in Additional Drivers.

---

