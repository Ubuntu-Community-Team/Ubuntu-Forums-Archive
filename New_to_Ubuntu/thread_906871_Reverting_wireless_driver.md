---
title: "Reverting wireless driver"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by noorez on 2008-08-31
I was having a bit of trouble with wireless internet on my laptop. The problem was that whenever I lost a wireless signal, I had to do a /etc/init.d/networking restart to get it back. So I tried the Ndiswrapper to use the windows xp driver of my wireless card. But it seems to have made things worse as I can't even connect to a wireless network anymore even though wicd detects one. (I can connect in windows). Using the GUI tool I removed the driver that I added but how do I make sure that I cleared everything.

---

### Post by pi.boy.travis on 2008-08-31
Run this in a Terminal:

sudo apt-get autoremove

This will eliminate any unused dependencies, libraries, etc.

Hope this is what you where looking for!

---

### Post by noorez on 2008-09-01
Nope, I think you misunderstood my question.

This is what is happening now, using the ndiswrapper gui util, I removed the wireless driver. I then did a modprobe -r ndiswrapper to remove it from the kernel. Now the wlan0 device doesn't even show up!

How do I get it back to the default settings so that ubuntu will use the driver it was using before when I first installed it on my laptop without ndiswrapper?

---

