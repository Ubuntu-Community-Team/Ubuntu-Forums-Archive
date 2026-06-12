---
title: "wireless BroadCom BCM4306 cannot connect"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Spline64 on 2008-04-23
Hello again all!

I am trying to connect to my router via the wireless BCM4306 BroadCom corp adapter that was automatically detected by Gutsy Gibbon (7.10) but am having no luck. No matter if I have encryption enabled or not (in the router), it cannot pick up on the network signal. The adapter is on, it scans for the network but cannot connect. It's almost like the drivers are not complete as you can see it in device manager but that is all.

Probably missing a step I assume. Tried the update (sudo apt-get update) which updates, but still doesn't work.

Any ideas??

thanks,
Spline64

---

### Post by spiderbatdad on 2008-04-23
This thread might help: [http://ubuntuforums.org/showthread.php?t=201902&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=BCM4306)

There are many others concerning this card. There seems to be some debate as to whether the restricted driver is the way to go...or ndiswrapper is the way to go. ndisgtk can also be of help for installing the driver.

If you use any of the how-tos for ndiswrapper, you will need to add the word ndiswrapper to your /etc/modules file for your settings to stick...This gets left out all the time for some reason.

---

### Post by Spline64 on 2008-04-23
Thanks!!

I will check it out and let ya know. Was hoping to avoid the ndiswrapper but starting to have so much fun learning / playing with this OS that I can't stop LOL!

thanks again,
Spline64

---

### Post by Spline64 on 2008-04-23
Second step and "Module bcm43xx does not exist in /proc/modules". It did detect the card however (first step).

thanks for the start! 

Spline64

---

### Post by spiderbatdad on 2008-04-23
thats ok...keep going. The command was to remove module.

---

