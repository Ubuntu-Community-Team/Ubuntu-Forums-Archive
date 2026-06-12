---
title: "increase mouse speed"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by kckrona on 2012-06-09
My mouse moves too slowly, so I would like to increase its speed. I am not looking for acceleration, since it has no effect when the speed is low.

---

### Post by daslinkard on 2012-06-18
I'm kind of confused by your question....if you're not wanting the acceleration then are you wanting an increase in sensitivity?

---

### Post by duracella on 2012-06-18
If you want to adjust sensitivity:
System settings > Mouse and Touchpad...

There you will be able to set sensitivity under pointer speed...

---

### Post by kckrona on 2012-07-18
> **daslinkard said:**
> I'm kind of confused by your question....if you're not wanting the acceleration then are you wanting an increase in sensitivity?

No, I want to keep the cursor speed as a linear multiple of the mouse speed, and have a higher multiplier.
Example: before the mouse speed increase, I need to move the mouse 6 inches to move across the screen, and moving 6 inches in the same direction will always land me in the same spot, no matter how fast my mouse is moving. After the mouse speed increase, I only need to move 3 inches to move across the screen, and moving 3 inches in the same direction will still always land me in the same spot.
With acceleration, the speed of the mouse matters; that's not what I'm looking for.

---

### Post by NikTh on 2012-07-19
Hi , 
please open a terminal and copy-paste this command from here to your terminal . 
```
synclient MaxSpeed="3.50"
``` 

Tell me , is that you want ?
Thanks

---

### Post by kckrona on 2012-07-19
> **NikTh said:**
> Hi , 
please open a terminal and copy-paste this command from here to your terminal . 
```
synclient MaxSpeed="3.50"
```Tell me , is that you want ?
Thanks

It works great for my touchpad. That's exactly the kind of behavior I'm talking about. :D

Unfortunately, I don't use my touchpad. Is there something similar for the trackpoint and mouse?

---

### Post by NikTh on 2012-07-19
> **kckrona said:**
> It works great for my touchpad. That's exactly the kind of behavior I'm talking about. :D

Unfortunately, I don't use my touchpad. Is there something similar for the trackpoint and mouse?

Hi , 
yes you have right. **Synclient** its for touchpad control. 
**Xset** its for mouse.. 
but before that , do you have any xorg.conf file ? 
Open a terminal and give the results of this command 
```
cat /etc/X11/xorg.conf
```
Thanks

---

### Post by kckrona on 2012-07-19
"cat: /etc/X11/xorg.conf: No such file or directory"

---

### Post by NikTh on 2012-07-20
Hi , 
its ok if you don't have xorg.conf file. 

Open terminal and run this command 
```
xset -q | grep accel
``` 
post the results back here . 
Thanks

---

### Post by kckrona on 2012-07-20
```
kckrona@hometop:~$ xset -q | grep accel
acceleration:  12/5    threshold:  1
```

---

### Post by NikTh on 2012-07-20
Hi , 
try this command 
```
xset m 25/5
``` 
and see if speed meet your needs. 
Thanks

---

### Post by kckrona on 2012-07-21
Sorry, but "xset m 25/5" just adds acceleration, and acceleration is hard for me to handle. I do have acceleration in my previous settings, but it's there as a stopgap and not because I enjoy it.

---

### Post by NikTh on 2012-07-21
> **kckrona said:**
> Sorry, but "xset m 25/5" just adds acceleration, and acceleration is hard for me to handle. I do have acceleration in my previous settings, but it's there as a stopgap and not because I enjoy it.

Hi , 
sorry then. Probably i misunderstood. I thought 
increase mouse speed = acceleration.

---

