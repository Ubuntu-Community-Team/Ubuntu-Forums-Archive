---
title: "Netflix movies will no longer play in Chrome"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by Thinkintuit on 2015-09-03
Netflix used to work perfectly in Chrome, but I haven't been able to get it to play movies for about the past month. When I go to the Netflix website, it loads normally--I can browse through programs etc.--but if I attempt to play any video, I just see a still from the video (without the spinning red circle that shows it's loading) and after a minute a black screen appears that says "Whoops--something went wrong" with **error code M7083-1013**.

I tried uninstalling and reinstalling Chrome, which didn't help. I followed some instructions [here]("http://askubuntu.com/questions/67047/how-to-uninstall-google-chrome") to purge Chrome, rebooted my computer, reinstalled--no effect. I tried waiting patiently for Chrome updates (I had a similar problem before, and when Chrome was updated, it started working again), but although there have been a few updates to Chrome, the problem remains.

I'm currently running **Ubuntu 15.04**

Not sure if it's relevant but over the same general period of time Steam has not worked properly in the Chrome browser. That is also a source of annoyance, but less so. In case it is relevant here is [a screenshot of what Steam looks like for me now]("https://plus.google.com/110172490080527198738/posts/EqGueDBMNgD"). On Firefox it works normally.

I've searched around the web and on these forums, but I'm not finding anything that seems to match my problem--I've found a number of threads where people had problems running a Netflix app, and the solution given is "Just install Chrome, it works right out of the box!" That used to be true for me, but alas, no longer...

Any help would be greatly appreciated.

---

### Post by NathanRodriguez on 2015-09-03
Have tried Chromium?

---

### Post by Geoffrey_Arndt on 2015-09-03
I don't do Netflix, but I recall reading something about needing HAL (hardware abstraction layer) . . . but it's no longer supported by Ubuntu/Debian/Mint.    But it seems there is still a ppa available that allows for install of HAL.  

[URL="http://blog.terranux.net/2014/04/how-to-get-4od-to-work-on-ubuntu-14-04-trusty/"]http://blog.terranux.net/2014/04/how-to-get-4od-to-work-on-ubuntu-14-04-trusty/
[/URL]
[INDENT]sudo add-apt-repository ppa:mjblenner/ppa-hal
 sudo apt-get update && sudo apt-get install hal




[/INDENT]

---

### Post by monkeybrain20122 on 2015-09-03
Probably your profile is corrupted. In that case reinstalling /purging chrome is not needed and won't do you any good. Close Chrome. Open the file manager at your home. Choose show hidden file from menu or press ctrl + h. Then locate the hidden directory .config (note the '.') , open it and rename the subfolder google-chrome to something like google-chrome-bak Now start Chrome and see if it works. To revert to old profile, close chrome, delete ~/.config/google-chrome and rename google-chrome-bak back to google-chrome.

P.s hal has nothing to do with Chrome or netflix. also netflix doesn't work on Chromium, it is Chrome only.

---

### Post by Thinkintuit on 2015-09-04
Thanks to everyone who responded, and especially monkeybrain20122. It did turn out to be the .config file. Once I renamed that as suggested Netflix was once again working perfectly. Much appreciated! :D

---

