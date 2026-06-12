---
title: "how can i add all sensors for GNOME Sensors Applet 2.2.7?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-10
Hi, I've installed GNOME Sensors Applet by
```
 sudo apt install libsensors-applet-plugin0 sensors-applet lm-sensors libsensors4
```.
I can now monitor how hot my CPU gets. But how can I add all the other sensors, like fan speed, hddtemp. See [http://sensors-applet.sourceforge.net/images/screenshots/004-sensors-prefs.jpg](http://sensors-applet.sourceforge.net/images/screenshots/004-sensors-prefs.jpg) for others.
Thanks.

---

### Post by alex2e1gzy on 2012-04-14
To setup your sensors run
```
 
sudo sensors-detect

```
 
I use *xsensor* to view my temps and *psensor* to graph them.

---

