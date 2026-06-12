---
title: "xbmcbuntu eden &amp; transmission-daemon"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by jlivin25 on 2012-04-24
Hello All
 
Well its that point where as a relative Linux noob i have to ask for help as google has not been able to help me :( (please bare in mind i really have searched hard and experimented before getting to the point of asking for help as i do try to do it myself first)
 
I have a Acer Revo 3700 on which i am running (very happily) xbmcbuntu Eden (based on ubuntu 11.10).
 
Essentially it is configured to boot automatically into XBMC without showing any desktop environment, however if you choose to you can access this.(which i believe is based on 'openbox')
 
What i am trying to acheive is to have a torrent program start automatically on boot. Previously i had transmission to do this and used the desktop to 'add it to start up programs' and i added the 'minimised' switch so it didn't start with an open window.
 
I can't however replicate this in xbmcbuntu.
 
After a lot of reading i began to understand that i didn't want to use the GUI i needed to have transmission-daemon installed and have this run and access it via the remote client ability.
 
The problem is that as a traditionally GUI based user i'm struggling with correctly identifying how to configure transmission from the command prompt (via ssh)
 
i have successfully installed transmission using sudo apt-get install transmission-daemon.
 
i found the transmission website and followed the instructions there about what to change. ([https://trac.transmissionbt.com/wiki/EditConfigFiles](https://trac.transmissionbt.com/wiki/EditConfigFiles))
 
so i editited the original settings.json in the correct folder (original attached) with the code i believe i need to run transmission-daemon with an alternative speed limit enabled and access capable from my network (on the 192.168.0.* range)
 
i then restarted transmission-daemon using the command listed in the web page above but am blocked access.
 
Deciding to stop there adn see if i could get the daemon to start on boot i followed the instructions here ([https://trac.transmissionbt.com/wiki/Scripts/initd](https://trac.transmissionbt.com/wiki/Scripts/initd)) to place a script in the init.d folder. but it doesn't work.
 
Any ideas what i may have done wrong and how to make it start in boot?
 
I've attached the settings.json that i have 'concocted from the website, the original, and the inid.d transmission.daemon script i created in a zip file
 
Thanks
 
James

---

