---
title: "hardware sensor indicator simple question"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by werty2010 on 2012-05-07
i followed the instruction from this [site]("http://askubuntu.com/questions/30334/what-application-indicators-are-available") running this command:
```
cd /tmp ; arch=$(uname -p) ; if [[ "$arch" = "x86_64" ]] ; then wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_amd64.deb ; else wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_i386.deb ; fi ; chmod +x /tmp/indicator-sensors_0.1-1* ; sudo dpkg -i /tmp/indicator-sensors_0.1-1*
```at first look it seems to work ok
my question is: since i have an i3-370m processor shouldn't the indicator show 2 separate temperatures instead of one?
maybe it shows the average of both,but i cannot be sure

---

### Post by Cheesemill on 2012-05-07
You don't have 2 separate CPU's, you only have one CPU with 2 processing cores which all live on the same piece of silicon together with the temperature sensor.

As these are all fractions of a millimetre apart they are all at the same temperature.

---

### Post by werty2010 on 2012-05-07
thank you
one more thing:
my cpu usually runs at about 50 celcius,is this low/normal/high?

---

### Post by Paqman on 2012-05-07
> **werty2010 said:**
> 
my cpu usually runs at about 50 celcius,is this low/normal/high?

That's fine for a laptop.

---

### Post by werty2010 on 2012-05-07
i noticed that even when my GPU temperature is above 70 C the fan is always at 30%.
why is that?

---

### Post by DaveMcC on 2012-05-07
> **werty2010 said:**
> i followed the instruction from this [site]("http://askubuntu.com/questions/30334/what-application-indicators-are-available") running this command:
```
cd /tmp ; arch=$(uname -p) ; if [[ "$arch" = "x86_64" ]] ; then wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_amd64.deb ; else wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_i386.deb ; fi ; chmod +x /tmp/indicator-sensors_0.1-1* ; sudo dpkg -i /tmp/indicator-sensors_0.1-1*
```at first look it seems to work ok
my question is: since i have an i3-370m processor shouldn't the indicator show 2 separate temperatures instead of one?
maybe it shows the average of both,but i cannot be sure

Yes you are right, but also wrong
My old Athlon X2 showed up as two, but the new X4 shows as one.

The 2 cores can run at different temps, but the over all temp is more important, ie if the fan breaks or clogs up over time "which it will"

Dave

---

### Post by Paqman on 2012-05-07
> **werty2010 said:**
> i noticed that even when my GPU temperature is above 70 C the fan is always at 30%.
why is that?

What part are you wondering about? As long as the chip isn't getting hotter and hotter then the fan is going as fast as it needs to.

---

### Post by werty2010 on 2012-05-07
> **Paqman said:**
> What part are you wondering about? As long as the chip isn't getting hotter and hotter then the fan is going as fast as it needs to.

i mean the GPU fan should "turn" faster when the GPU is getting hotter
what would be normally the point of heat that the fan speed should increase?

---

### Post by Paqman on 2012-05-07
Ah, sorry, didn't notice it was a GPU fan. Is it the stock one that came with the card, or one you added yourself?

---

### Post by werty2010 on 2012-05-07
the stock one

---

### Post by Paqman on 2012-05-08
Well, I would have thought the fan would be in a closed feedback loop with the temperature sensor on the card, but it's obviously just running at a constant speed for some reason. Are you able to get it to ramp up if you stress test the card?

---

### Post by werty2010 on 2012-05-08
i tried it but no,it remains steady on 30%

---

