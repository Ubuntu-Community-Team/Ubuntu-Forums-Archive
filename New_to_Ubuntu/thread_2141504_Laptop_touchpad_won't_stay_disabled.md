---
title: "Laptop touchpad won't stay disabled"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by dondiego2 on 2013-05-02
I have an ASUS laptop. I can set the touchpad to disabled in the BIOS then sometime later it becomes active again. I reboot, check BIOS and it still disabled, Ubuntu boots up and it stays disabled for a while and then becomes active all of a sudden. How do I stop this? I use a usb wireless mouse.

---

### Post by Isamu715 on 2013-05-03
Run this in a terminal:
```
sudo rmmod psmouse
```
This should disable touchpad completely. If it works for you create a file called *disable-touchpad* (you can call it whatever you want) with the following contents in */etc/modprobe.d/*:
```
# /etc/modprobe.d/disable-touchpad
blacklist psmouse
```
This will make your touchpad persistently disabled. If you want to enable it run:
```
sudo modprobe psmouse
```
And remove the */etc/modprobe.d/disable-touchpad* file.

---

### Post by dondiego2 on 2013-05-03
Thanks! That worked.
To create the file do I just use an editor and type it exactly as shown?
To run it I just type the name in the terminal?

---

### Post by Isamu715 on 2013-05-04
> To create the file do I just use an editor and type it exactly as shown?
Yes, just note that you'll need to run the editor with root privileges (for ex. *gksudo gedit*). You can also do it with these two commands:
```
sudo su
echo "blacklist psmouse" > /etc/modprobe.d/disable-touchpad.conf
```
This will create the file you need with contents already in place.

---

### Post by dondiego2 on 2013-05-04
Thank you very much!
I'm all Ubuntu on this laptop now. No more Windows. 
So it's gret to have this forum!

---

