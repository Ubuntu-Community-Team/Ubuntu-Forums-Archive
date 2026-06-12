---
title: "resolution keeps resetting after restart or cold boot"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by navic101 on 2008-06-23
Hi guys,

left a thread yesterday because i foolishly decided to try an old graphics card out to see what the display was like. This did not work out and went back to my on-board graphics which is an NVidea 7 series. 

I have hardy heron by the way

The display resoloution was terrible even though i had no problems the first time installing the NVidea drivers.

The advice i was given was to press escape several times on boot up click fix x-server and boot. Which sorts out the resolution and altering there of until i reboot again and it reverts back to the horrible size again. Worse than the default drivers in unbuntu. Is there any way of ensuring the resolution stays at what i want it to? When i re-boot only only has 2 display settings. I think for some reason the driver settings are not being remembered.

Any help would be really apprieciated

---

### Post by NT4usB on 2008-06-23
First, Look at System>Administration>Hardware Drivers... Is nvidia checked?

Next,
```
sudo nvidia-settings
``` should bring up a screen you can configure the display and make it stick.

Next option:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Next option, try [Envy]("http://albertomilone.com/nvidia_scripts1.html")
Read the [faqs]("http://albertomilone.com/envyfaq.html") first

---

