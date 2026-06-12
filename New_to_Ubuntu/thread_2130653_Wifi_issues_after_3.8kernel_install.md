---
title: "Wifi issues after 3.8kernel install"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by CamPsych on 2013-03-30
Hi all


Was having issues with crashes from GPU and followed the directions here: [http://ubuntuforums.org/showthread.php?t=2127593](http://ubuntuforums.org/showthread.php?t=2127593) to get that sorted (not sure if completely fixed though). I did a reboot and since have not been able to connect to wireless (have a Broadcom BCM4313 on board). 


Tried another reboot as well as rebooting Modem in addition to forgetting network and starting from scratch but nothing, cycles round and round and then asked for pw over and over. 


No other access to Internet except phone so posting logs may be difficult but willing to do whatever needs to be done.


Running 12.10 on an Acer laptop.

---

### Post by sanderj on 2013-03-30
The link you gave: TL;DR

What was your problem? Error messages? Or Wifi problems? Or ... ?

And what is the problem now? Your title says "Wifi issues" but your post suggest a non-functional system ...

---

### Post by AndyOpie150 on 2013-03-30
Thanks.

---

### Post by wildmanne39 on 2013-03-30
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by CamPsych on 2013-03-31
@sanderj sorry, the issue was a heap of crashes, which seem to have been resolved with the update to 3.8. However directly after that update the wifi is not working properly. It connects for a minute or two and then drops out altogether. Firefox sitting for ages on a single page even when I click off it. 
If I disconnect network then retry it will keep trying until timeout. Other devices are working fine on the same network. 

@wild man. Would love to, however no Internet connection on the Ubuntu computer making any download base commands untenable.

---

### Post by CamPsych on 2013-03-31
OK folks, after a lot of searching and trial and error, the best result that I found was at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues). I did this, wondered why it wouldn't work, but then realised at the last moment that after the upgrade that I had put the password in incorrectly...so all is working now. 

Cheers

---

### Post by wildmanne39 on 2013-03-31
Glad you got it working.

---

