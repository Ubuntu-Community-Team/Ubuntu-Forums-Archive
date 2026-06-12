---
title: "No sound on internet but can hear audio"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by odwyerda on 2008-05-01
I cannot hear sound on my Firefox but I can play mp3's and the like and hear them no problem.

When I installed HH it was the other way around. What I did was get my sound card driver

hda-intel

and reinstall it using Ubuntu wiki help page Alsa drivers and the likes,


How do I get them both to work

```
lspci -v
``` give my sound card is working

Help this is frustrating fixing one for the other sound to go!

---

### Post by artir on 2008-05-01
You have to install libflashsupport
You will be able to hear sound from flash, but firefox will crash.
To avoid this, follow this tutorial:
[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html]("http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html")

This issue is caused by an incompatibility between pulseaudio and flash. they are working on that..

---

### Post by odwyerda on 2008-05-01
Ok , I was just about to delete this thread because after I deleted my desktop and reinstalled it it now works grand.

Should I still do what u say to make sure its permanently ok?

---

