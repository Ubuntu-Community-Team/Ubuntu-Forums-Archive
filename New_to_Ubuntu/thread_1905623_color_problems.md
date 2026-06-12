---
title: "color problems"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by rwmcewan on 2012-01-07
This is my first time using Ubuntu. I loaded it on my PC and the colors are not acting right. I think the color bit needs to be changed but I don't know how to do this. the colors are smeared and inverted. It is also hard to read text and see icons. Any ideas on what it could be? thanks,

---

### Post by deonis on 2012-01-07
Hi, What is your Ubuntu version and  the producer of your video card ?

---

### Post by rwmcewan on 2012-01-07
Thanks for the reply. 
 
I installed Ubuntu v.11.10
 
My video card, as far as I can tell, is G73M MXM integrated module for graphics.
 
The computer is an HP Touchsmart IQ770 (made in 2007/8) 
 
Let me know if that is not the right name of the video card and I will look further.

---

### Post by deonis on 2012-01-07
Thanks, as far as I can tell it's Nvidia. Please run this in terminal:  /usr/bin/jockey-gtk
Wait until search for drivers will be finished. You should be able to see an additional driver to install. So, just install it and reboot your PC. You should be good to go ...

---

### Post by rwmcewan on 2012-01-07
i followed the steps. It came up with about 6 driver recommendations. I tried to install all of them but it wouldn't take. It says installation of this driver failed. for details look at: /var/log/jockey.log.
 
I will keep trying it. Thanks for the help so far.

---

### Post by deonis on 2012-01-07
also try to logout and login to Unity 2D, I assume that you are using Unity 3D? As for the drivers, I am not sure why would you have 6 drivers for Nvidea... Do you miss some other drivers ? Like Wifi etc?

---

### Post by rwmcewan on 2012-01-07
i'll try it. Thanks, I don't know what to do with this computer. there is a setting somewhere that is throwing this system off.

---

