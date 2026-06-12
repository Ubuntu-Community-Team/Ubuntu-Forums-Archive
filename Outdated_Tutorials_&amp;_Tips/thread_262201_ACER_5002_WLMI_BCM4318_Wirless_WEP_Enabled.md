---
title: "ACER 5002 WLMI BCM4318 Wirless WEP Enabled"
date: 2006-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by prince_niceguy on 2006-09-21
While following instruction of using ndiswrapper for the bcm4318 card, I faced a very unusual problem. 

I followed the steps given in this [thread link]("http://ubuntuforums.org/showthread.php?t=190177")

I rebooted my laptop and boot refused to move from "Loading manual drivers...". I started in recovery mode and ndiswrapper was the culprit along with my acer wirless button. If I had the wireless button enabled then the system will hang at ndiswrapper, if I didn't have wirless enabled then system will boot normally.

Once after booting... if I run the installation script twice in the thread given then system will detect my network card and I was able to switch on wirless.

This was quite annoying so I did the following.

1. Download ndiswrapper source from ndiswrapper.sourceforge.net.
2. Installed build essential, gcc and make using synaptic. you can search for them and install. 
3. Installed linux header files for my "uname -r" version of linux.
4. Compiled and did a make of the ndiswrapper.

And I rebooted my laptop... volla... even with the key enabled I was able to start up the system... now the wireless is working super fine...

Just thought would share this :-)...

---

