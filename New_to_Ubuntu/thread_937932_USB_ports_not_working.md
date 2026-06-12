---
title: "USB ports not working"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Asolepius on 2008-10-04
Hi folks - my first post here and I am not even an absolute beginner as I can't seem to get started! I have installed Ubuntu on a spare PC to get to know it, but none of the 4 USB ports is powered up - they were when the PC was running Win XP. The mouse is USB so interactions are a bit limited to say the least! I have searched this forum and can't find anything about this. You will probably tell me to use a PS2 mouse but any new one you buy these days is USB so I don't have one. The OS boots up OK and responds to the keyboard. Any ideas guys?

---

### Post by scratman on 2008-10-04
On the desktop, hold Alt+F2 and type
```
gnome-terminal
```
and press enter.  Then type
```
lsusb
```
and post the results here.

---

### Post by JAS510 on 2008-10-05
yes same thing goes for me. 

typed lsusb and nothing happened.

any ideas

btw, i'm on gnome safemode.

---

### Post by scratman on 2008-10-05
lsusb will not actually do anything, it just lists what you have got attached to your USB ports

Mine returns this::-
Bus 002 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 001 Device 001: ID 0000:0000  

It will give you some idea of whether the O/S can even see your mouse.

---

### Post by Asolepius on 2008-11-04
Sorry for long delay, I was distracted by major problems on other (Windows) PCs, and holidays! Also this board didn't notify me of replies - probably have to change my profile. Anyway, I have listed the USB ports and all 6 ports are listed but no devices are recognised, eg the RAM stick I have plugged in right now.

---

### Post by Asolepius on 2008-11-04
Sorry, nearly forgot - here is the listing:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I have got the mouse working now using a USB-PS2 adapter. Thus Ubuntu is up and running and looking very impressive - just need to get the whole thing working.

---

