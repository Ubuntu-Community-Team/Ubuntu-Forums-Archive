---
title: "Help with screen"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Killfer on 2013-07-11
Alright, I'm kind of new to Ubuntu (13.04) and I recently installed a game and when I quit the game the screen goes really big and i don't know how to fix it, in fact, not even rebooting the PC will fix it, everything has been gone big. I have some screenshots, I'm sorry for the Spanish version but i went to Spanish forums, I registered and I haven't recieved the confirmation mail yet, It has been already 2 days, and well I'm not that good at English but I was wondering If you could help me:)

Regards, Fernando.

[http://oi44.tinypic.com/u7i3n.jpg](http://oi44.tinypic.com/u7i3n.jpg) 
[http://oi39.tinypic.com/2qw3ip3.jpg](http://oi39.tinypic.com/2qw3ip3.jpg)

---

### Post by newb85 on 2013-07-11
I'm the system settings window, open Displays (monitores) and select the correct resolution.   I have no idea why the game did that. What game is it?

---

### Post by papibe on 2013-07-11
Hi Killfer. Welcome to the forums ):P

It looks like the game changes the screen to a lower resolution, but it fails the return it to what was before.

Try going into **System Configuration -> Displays** to change it back.

I believe in Spanish should be:
```
Configuración del Sistema -> Monitores
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldos2er on 2013-07-11
What game? What video card does your system have?

---

### Post by Killfer on 2013-07-11
The game was Wolfenstein: Enemy Territory, but when i chane the resolution and i click on Apply the screen goes black, my actual resolution is 800 x 600 and when i try to change it it goes black, i have to reboot. I use nVidia GT220 1GB 
[http://oi42.tinypic.com/2yxpvub.jpg](http://oi42.tinypic.com/2yxpvub.jpg)

---

### Post by papibe on 2013-07-11
If you have the Nvidia proprietary driver installed, don't use 'Monitores' but use 'Nvidia X Server Settings' instead.

Regards.

---

### Post by Killfer on 2013-07-11
I downloaded the Nvidia dirvers and it's a .run type, but everytime i open a .run i get the text editor (?) and it's totally blank

---

### Post by papibe on 2013-07-11
I would let that option as a last resort (downloading driver from Nvidia website).

Try to install it from 'Additional Drivers'.

Also, could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by Killfer on 2013-07-11
```
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT216 [GeForce GT 220] [10de:0a20] (rev a2)    Subsystem: Device [196e:0699]
    Kernel driver in use: nouveau



```

---

### Post by papibe on 2013-07-11
Thanks.

I can see that you have a proper Nvidia card, and you are using the open source driver at the moment.

Open 'Additional Drivers' or just 'Drivers' and install the recommended Nvidia proprietary driver.

Then restart your machine.

Let us know how it goes.
Regards.

---

