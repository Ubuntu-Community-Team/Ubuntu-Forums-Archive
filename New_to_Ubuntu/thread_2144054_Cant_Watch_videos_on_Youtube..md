---
title: "Cant Watch videos on Youtube."
date: 2013-05-10
forum: New to Ubuntu
---

### Post by nsync on 2013-05-10
i am new on ubuntu and started using it yesterday. i really need help because i can ony play low quality videos on youtube.. i also installed Adobe Flash player to because youtube wanted me to and after installing i still cant play videos and everytime i browse videos on youtube and come up clicking a video it says ; ADOBE FLASH PLAYER IS REQUIRED FOR VIDEO PLAYBACK.. and i am sure that i installed flash player using Ubuntu Software center.. can someone help? :confused:

---

### Post by zombifier25 on 2013-05-11
Type this command in a terminal:
```
sudo apt-get install --reinstall flashplugin-installer
```
It reinstalls Flash. It's possible the Flash plugin is not downloaded fully.

---

### Post by alhefner on 2013-05-11
Go to this comprehensive "How to" and do what it says. [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

It takes some time to complete but, once it's done, your video problems should clear right up...

---

