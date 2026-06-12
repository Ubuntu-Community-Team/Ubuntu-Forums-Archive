---
title: "Broadcom working but settings need re-doing each reboot"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Bennp2000 on 2008-07-29
Hello everyone, thanks for taking the time to read this post (by a newbie :) )
Basically about two years ago my laptop was stolen and replaced by my insurance with something that was pretty rubbish compared to the one that went missing. It's never been fast on XP but recently it's been getting slower and slower, after chatting to a mate I decided to give Ubuntu a go on a dual boot.
The Live CD was a nightmare but the text based installer was a breeze, then the fight began with my Broadcom wireless card and then Network Manager to work with my WEP settings. Both of those are now working (only 2 days later after a lot of googling) but the settings seem to be lost on shutdown.
When I reboot now light is on, on my wireless button. If i go to system>admin>hardware drivers Broadcom B43 wireless driver is shown as enabled but not in use (iwlist scan says device doesn't support scanning). If I then disable then re-enable it I can then turn my wireless on, after that I select my location that I've saved as 'roaming' and everything works well  (including iwlist scan) however its a bit of pain to have to do this. Have I managed to do something wrong while setting all of this up or do I need to write a script to do this on startup ( I think I might struggle with this)...
Thanks for any advice, any outputs that you need I'll supply.
:)

---

### Post by swegner on 2008-08-27
It might be helpful to know more about how you got your network card working in the first place.  Are you using ndiswrapper?  Also, you can check for log messages (System > Administration> System Log) when you boot up or try to connect to a network.  This information is very useful and will help when debugging your problem.

---

