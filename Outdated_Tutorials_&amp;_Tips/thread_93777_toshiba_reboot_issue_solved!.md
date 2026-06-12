---
title: "toshiba reboot issue solved!"
date: 2005-11-22
forum: Outdated Tutorials &amp; Tips
---

### Post by depp on 2005-11-22
After long time testing, i found, the issue with reboot on my toshiba a100 is caused by "ipw2100" module, the wireless module. What i should do before i reboot is, remove it!:D  
So just type:
```
sudo modprobe -r ipw2100
```
It's also necessary to do a hibernate. I'm not sure if it's also the case with ipw2200 toshiba laptops, just have a try!
Hope it helps!;)

---

### Post by depp on 2005-11-23
for some additional tweak, check this thread [http://ubuntuforums.org/showthread.php?t=75314&page=5]("http://ubuntuforums.org/showthread.php?t=75314&page=5")

---

