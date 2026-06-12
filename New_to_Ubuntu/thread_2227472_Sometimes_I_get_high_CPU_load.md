---
title: "Sometimes I get high CPU load"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by watt2 on 2014-06-02
Hello everyone.

I noticed that sometimes when browsing (with other processes  in the background), I get very high CPU load for the browser process  (over 100%) so the computer becomes really slow. I tried switching from  Firefox (with just a few extensions) to Chromium, but same thing  happens without me visiting graphics-intense sites, flash sites or  anything like that. It is not related to the number of tabs. I also noticed python or node (when running "make")  produce the same high CPU load from time to time so this is not  necessarily browser-related. 

Closing all the applications (and have no weird CPU usage displayed), my computer is still very slow. I have to reboot in order to restore performance.


  When I only have a browser open, it doesn't seem to happen and everything is fine in Windows 7. I switched from unity to gnome3 with no effect.


  Specs: lenovo w510 (4gb RAM, i7 q820 @ 1.73) + up to date Ubuntu 14.04 64bit. 

Printscreen: 
[IMG]http://i.imgur.com/8MZJNKC.png[/IMG]

  
Do you guys have any idea why this might happen? Please let me know if there's other info you need.

  
Thanks!

---

### Post by philinux on 2014-06-02
Have you enable the nvidia driver?

---

### Post by watt2 on 2014-06-02
Thanks for the reply, philinux.

Yes, I am using the recommended driver for my device: 
*using nvidia binary driver - version 331.38 from nvidia-331 (proprietary, tested).*

---

### Post by philinux on 2014-06-02
Might be worth trying both without nvidia driver I.e use nouveax and the nvidia updates version.

---

### Post by watt2 on 2014-06-11
Tried switching to these drivers but no change:
- nvidia binary driver - version 331.38 from nvidia-331-updates (proprietary)
- x.org x server - nouveau display driver from xserver-xorg-video-nouveau (open source)

Any other idea?

---

### Post by watt2 on 2014-06-17
This is driving me crazy, making me switch back to Windows instead.

My CPU usage is at this moment: 
52% firefox with 3 tabs
25% vlc playing an online radio
13% htop

Why are these taking so much CPU ?

---

### Post by johan18 on 2014-08-04
I have pretty much the same set up W510 Same  i7 q820 @ 1.73 and 14.04 64bit and the same NVIDA 311.38. I have 12 gigs of ram though I don't know if that is the difference but may be try a different build? A fresh install of X/Lubuntu 14.04? It sounds crummy though. Try messing with the F1 menu on boot? There might be some options there that could help. Good luck! And don't give up!

---

