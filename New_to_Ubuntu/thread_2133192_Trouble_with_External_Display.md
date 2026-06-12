---
title: "Trouble with External Display"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Donkey666 on 2013-04-07
hi guys i have a eee pc x101ch with hdmi and ubuntu 12.4 , when i connect my laptop to my 32 inch samsung tv and ask it to display on the tv i get this message 

requested position/size for CRTC 63 is outside the allowed limit: position=(1024, 0), size=(1280, 720), maximum=(2048, 2048)

I have looked and looked and dont know what to do can anyone please help me :)

Also have tried changing the displays bu evenon the biggest setting i have it still does not work ? 

Please help think the wife will kill me if i dont get it woking

---

### Post by cuby on 2013-04-07
The graphic adapter is from nvidia or ati? are you using the proprietary aplications or the one in settings->displays ?
Try to use the proprietary ones.

---

### Post by Donkey666 on 2013-04-07
sorry i dont know what the graphics adapter is and sorry again but can you recomend a proprietary one ?

---

### Post by cuby on 2013-04-09
Just for curiosity, to find the display adapter, go to the command line and type:
```
lspci | grep VGA
```
You will get something like (this is my card):
05:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

To install the drivers you only need to go to:
System settings->Software & Updates, then in the "Additional Drivers" tab if you have either Nvidia or ATI, chose the newer version

---

