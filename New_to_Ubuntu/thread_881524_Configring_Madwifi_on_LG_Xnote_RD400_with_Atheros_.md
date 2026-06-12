---
title: "Configring Madwifi on LG Xnote RD400 with Atheros wifi card"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Ranjeet Verma on 2008-08-06
My regards to everybody who is associated with Ubuntu.
I started fresh recently enjoying it and soon i m going to became addicted to it.

Anyway my request is to help me with wifi setting notebook got inbuild card which i think is Atheros. I am able to connect internet by network card but not by wifi. 
Tried some thing with madwifi as instructed by others in forurm but i guess problem is i m not able to configure it properly and got struck in between kindly guide me step by step as i m new

Thankx

with Regards
Ranjeet verma:)

---

### Post by nicedude on 2008-08-11
I have looked into your problem as I am a bit of a madwifi buff and thought I could easily troubleshoot this for you and get you on the right track. But I found out you more than likely don't have an Atheros based chipset in your laptop and therefor the madwifi drivers are not what you need.

IF THIS IS YOUR LAPTOP THEN I THINK I AM RIGHT
[http://www.cyberindian.net/2007/11/01/lg-xnote-rd400-notebook-pc/](http://www.cyberindian.net/2007/11/01/lg-xnote-rd400-notebook-pc/)

Then you have a Intel Pro Wireless 3945ABG which is I believe based on a broadcom chipset but should be supported with linux pretty easily. I would recommend looking here in the forums for threads on broadcom chipset wifi as well as Intel Pro Wireless 3945ABG here is the one on the broadcom chipset which should be what you need

[http://ubuntuforums.org/showthread.php?t=779754&highlight=Intel+Pro+Wireless](http://ubuntuforums.org/showthread.php?t=779754&highlight=Intel+Pro+Wireless)

If the broadcom drivers for linux don't work well enough in your case then you can always use "ndiswrapper" which will let you use a Windows based driver for your wifi adapter while in linux. Although I would say first try to use the linux native driver then ndiswrapper as last resort, just me since I don't like the idea of needing a windows driver in linux if at all possible to solve another way :-)

Hope this gets you headed in the right direction and welcome to Ubuntu.

nicedude

---

