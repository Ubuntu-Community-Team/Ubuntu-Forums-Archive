---
title: "bluetooth wireless mx laser on restart"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by RogerKorby on 2008-09-18
Hi :)

I was doing some reading on similar issues but i couldent find anything exact that would fix it.

my problem is when i start ubuntu it shows the bluetooth logo in the topbar but my mouse will not work at all ... to make it work i have to remove the bluetooth usb device and reinsert it into the same usb port and the bluetooth logo dissapears and then the mouse instantly starts to work 



any help would be great :) thanks

---

### Post by snarebear on 2008-09-18
From my understanding, when you reinsert you bluetooth dongle while already booted up, you set bluetooth to "emulation mode". It's possible that you just haven't paired your devices yet. After booting up, with the dongle already plugged in, go to system>preferences>bluetooth and pair your devices by clicking on 'Input service' and clicking 'Add'.

---

### Post by RogerKorby on 2008-09-19
Fixed all i did was take off bluetooth in the services and after reboot it worked fine because it loaded it as usb mouse i guess

---

