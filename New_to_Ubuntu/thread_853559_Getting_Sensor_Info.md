---
title: "Getting Sensor Info?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by uzzo2 on 2008-07-08
hello all, i installed the sensors applet from synaptic and put them on the panel. but i can't tell which one's which, if you right click and go to preferences>sensors the only thing in that panel is libsensors. running ubuntu 8.04, thanks in advance.

---

### Post by tjwoosta on 2008-07-08
first install lm-sensors

```
sudo apt-get install lm-sensors
```

then do this

```
sudo sensors-detect
```

then just say yes to all the questions it asks

then reboot and add the sesors-applet to the panel

then right click the applet and choose preferences 

then click the sensors tab 
(there should be one for each core of your processor and one for your harddisk)

---

### Post by uzzo2 on 2008-07-08
> **tjwoosta said:**
> first install lm-sensors

```
sudo apt-get install lm-sensors
```

then do this

```
sudo sensors-detect
```

then just say yes to all the questions it asks

then reboot and add the sesors-applet to the panel

then right click the applet and choose preferences 

then click the sensors tab 
(there should be one for each core of your processor and one for your harddisk)

thanks, i've already done all that but when you click preferences>sensors the only thing showing in the panel is libsensors, no individual sensor info.

---

### Post by tjwoosta on 2008-07-08
have you tried clicking on that little arrow beside libsensors?

---

### Post by uzzo2 on 2008-07-08
> **tjwoosta said:**
> have you tried clicking on that little arrow beside libsensors?
ok, did that, the applications listed are in0 through in8 and are not enabled. then, fans 1,2 and 3 also not enabled, and temp 1,2 and 3 those are enabled. that's what shows on the top of the panel temp 1,2 and 3 but i have no way of knowing what sensors they are.

---

