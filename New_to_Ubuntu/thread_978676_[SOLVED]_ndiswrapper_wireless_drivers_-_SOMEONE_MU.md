---
title: "[SOLVED] ndiswrapper wireless drivers - SOMEONE MUST HAVE THEM!"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Liametc on 2008-11-11
as i found out last night, the repository of ndiswrapper windows drivers has gone down. I have been trying to install my edimax wireless card for a while now. When i finally plugged it in properly (my bad) i installed the ralink rt2860 drivers successfully. BUT i cannot log into the internet, apparently its due to these drivers not supporting the security settings. i would just turn these off but i am sharing the router with my housemates and they probably dont want me messing with it! 

apparently the answer lies with installing the drivers using ndiswrapper, but the server is down! 

basically im asking for anyone who downloaded the rt2860 windows drivers before the ndiswrapper site went down to make it available so i can finally unplug my 15m rj45 cable thats running through my house!

and while im at it if people have other drivers,  why not make it available too. we're a community at the end of the day, we should be helping each other out.

---

### Post by mapes12 on 2008-11-11
Seems OK to me:

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

You can also install GUI front end: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) which is available from Applications>Add/Remove

And this may help: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by Liametc on 2008-11-11
no i mean the drivers not the program

i cant remember the repository address as im on a different computer now but if you search for the drivers on google the links dont work

thanks anyway

---

### Post by phidia on 2008-11-11
If you just google rt2860 windows driver or better yet .inf you will find many download possibilities.

There's one of many sites [here]("http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/Ralink-RT2860-RT2890-PCI-Driver-1030.shtml").

---

### Post by mapes12 on 2008-11-11
This any good. The download links seem to work: [http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)

---

### Post by Liametc on 2008-11-11
unfortunately that driver is the one that doesnt like security. 

i basically need the .inf .sys and .cat files that ndiswrapper use to install the drivers. i have looked on torrents and other webpages but they are all liked to the same file and it doesnt want to download. 

sorry to be a nuisance but thanks for helping :cool:

---

### Post by phidia on 2008-11-11
> **Liametc said:**
> unfortunately that driver is the one that doesnt like security. 

i basically need the .inf .sys and .cat files that ndiswrapper use to install the drivers. i have looked on torrents and other webpages but they are all liked to the same file and it doesnt want to download. 

sorry to be a nuisance but thanks for helping :cool:

Are you sure it's the driver that doesn't like security? Setting up connection to a protected network can be tricky. You should check out the Ubuntu wiki on secure networks or the forums for how tos.
I would provide a link but there's so much lag with the forums that I can't.

---

### Post by Steve1961 on 2008-11-11
Is this what you're after?

These are rt2860 windows drivers that I'm using with ndiswrapper on my eeepc, and they work fine with wpa security

---

### Post by Liametc on 2008-11-12
FINALLY ive got it working. i managed to find the windows driver files. they were in a 7-zip format so when i finally downloaded the 7z program i was able to do it. i did nothing differnent to when i downloaded the old driver and it logged me into the internet straigt away. so i think that the ralink linux drivers dont like the security settings.

thanx guys for the help. it was useful cheers :)

---

