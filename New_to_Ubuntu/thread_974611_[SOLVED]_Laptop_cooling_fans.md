---
title: "[SOLVED] Laptop cooling fans"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by sag7392 on 2008-11-07
Hello again,

I have a HP Pavilion zt3000 with a dual boot (Windoze XP/Linux Ubuntu 8.04). It seems that on the Windoze side, the cooling fans will come on from time to time. However on the Linux side, I can't remember my fans ever coming on even after having my laptop on for a few hours. Now the laptop doesn't get hot, but it does get warm. Could it be that the fans are not working on the Linux side based on a lack of firmware being recognized or is Ubuntu easier on the processor and the temperature that starts the fans is not reached?

I tend to stay on the Linux side 95% of the time as well.

Thanks to you all!

---

### Post by rampageoberon on 2008-11-07
I'm not sure about the fans, but you can monitor your cpu temperatures using lm-sensors and adding the icons to your desktop pannel using the following code.

```
sudo aptitude install lm-sensors sensors-applet
```

---

### Post by sag7392 on 2008-11-11
After more research, I found that my laptop doesn't support the lm-sensors & sensors-applets...unless I am doing something incorrectly. When it is loaded and I try to set it up, the applet doesn't find any sensors for it to work. I guess my biggest concern is that fact that my cooling fans are not coming on...I mean my laptop doesn't get hot, but it does get very warm and I don't want to risk the longevity of my laptop. 

Any ideas? Again, the cooling fans activate on the Windoze side.

Thanks to you all!

---

### Post by sag7392 on 2008-11-14
Problem solved...my cooling fans do come on...nothing was needed to be done. I believe that Ubuntu is easier on the processor, therefore the fan doesn't come on that often...another reason I love Linux/Ubuntu!

---

### Post by Ripfox on 2008-11-14
try installing hddtemp and sensors applet and see if that works

---

