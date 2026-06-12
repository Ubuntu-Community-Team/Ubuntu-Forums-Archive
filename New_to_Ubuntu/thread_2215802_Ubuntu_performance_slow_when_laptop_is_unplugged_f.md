---
title: "Ubuntu performance slow when laptop is unplugged from AC"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by 884kmFE on 2014-04-08
I've been googling this for months now and couldn't find an answer.

Laptop becomes slow in every aspect when I unplugg it from charger and then rapidly fast when I plug it back in.
I'm using samsung ativ 6 notebook, dual booting with windows 8.1 (the issue doesn't occur on windows 8.1).

Any ideas?

Ubuntu version is 12.04

---

### Post by buzzingrobot on 2014-04-08
Laptops often have BIOS settings that can be toggled to draw less current when the battery is in use, prolonging the session.  The tradeoff is things can run a bit slower.

Also, check you power management settings in Ubuntu.  Perhaps you've set them to be more conservative in Win8.

---

### Post by 884kmFE on 2014-04-08
I installed cpufreq and it set cpu-cores to work "ondemand" now ubuntu becomes slow for a certain amount of time then fast again (when charger is unplugged).
Checked some settings in BIOS just in case, they seemed fine (I don't want to set settings on high-performance to kill battery life).

Note: First time when installed ubuntu everything worked fine (with or without charger). 
Battery usually lasts longer on windows 8.1 (I had it even for 7 hours once).
Also never changed any settings in BIOS regarding power managment to screw things over. xd

---

