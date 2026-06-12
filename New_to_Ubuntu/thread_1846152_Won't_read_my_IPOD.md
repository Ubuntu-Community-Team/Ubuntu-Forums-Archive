---
title: "Won't read my IPOD"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by Cubanicous on 2011-09-18
So i plugged in my ipod via the USB cable in Natty Wharl. And I can't find it anywhere in system. Are they any drivers I need to install for the Ipod for ubuntu to read the Ipod?

---

### Post by dniMretsaM on 2011-09-18
First, what iPod?

---

### Post by Cubanicous on 2011-09-18
IPOD classic

---

### Post by dniMretsaM on 2011-09-18
Aare you getting any error messages? What programs are you trying to sync with?

---

### Post by Cubanicous on 2011-09-18
No error messages. Trying to use it in Banshee. I can't find the Ipod at all in the directory nothing happens when I plug in the USB

---

### Post by owiknowi on 2011-09-18
same problems here with my ipod classic and ubuntu.
sometimes it helps with such devices to set them to 'usb host' (or they have a dedicated usb host port like iaudio), connect to usb and then switch on.

will try it tomorrow with mint and pardus 2011.1 if the problem is not solved by then ;)

---

### Post by dniMretsaM on 2011-09-18
Do you have usbmuxd installed? If not, search for it in the Software Center or run this in Terminal:
```
sudo apt-get update
sudo apt-get install usbmuxd
```

That might help.

---

### Post by owiknowi on 2011-09-19
connected my ipod and it showed up like an usb storage device (pardus kurumsal 2 and pardus 2011.1), without having to install any additional drivers or sum such.
it didn't came up with an u10.04.2 installation on another pc, though.

aditional info 15:00
connected it to a pc running mint 9 (ubuntu 10.04 based) and it automatically opened the ipod with rythmbox (0.12.8 ), and even better, it showed its content!
apple has its own way of storing music on their devices, so you'll need some extra software to add music or read what's stored on it.

---

### Post by Cubanicous on 2011-09-19
It worked finally! I think what happened is that my ipod froze up, because once I unplugged the USB from the computer, the screen on the ipod still read "Do not disconnect" and after 8 hours the damn thing lost battery power. So I plugged it in this morning and Banshee reads the damn thing. So problem solved.  

Thanks to all for your help. It is greatly appreciated.

---

