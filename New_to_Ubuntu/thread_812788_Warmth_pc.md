---
title: "Warmth pc"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by HaemoLacria on 2008-05-30
How can I easily see what the warmth of my pc is? My pc is about 8 years old and I replaced the 250w fan with an 300w. The roster feels warm very quick but I'm not sure if it's alright or not

---

### Post by Promaster91 on 2008-05-30
More info [here]("http://www.xawk.com/ubuntu-cpu-temperature.html").

---

### Post by Cato2 on 2008-05-30
Assuming you are on Ubuntu not Kubuntu - open a terminal to install the following packages: ```
sudo apt-get install lm-sensors sensors-applet
sudo sensors-detect
```
lm-sensors is the main package, sensors-applet is the GUI frontend.  Sensors-detect configures lm-sensors - as long as it seems to detect your hardware, let it modify the modules loaded at startup.

Also, have a look for hddtemp which shows you hard disk temperatures and is supported by sensors-applet it seems.

For a full HOWTO, see [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto) and [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

