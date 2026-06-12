---
title: "Drivers for nVidia G102m"
date: 2015-01-02
forum: New to Ubuntu
---

### Post by Nikola_Jovanovic on 2015-01-02
This is my first post on ubutuforums, yey! Would love to be under some other circumstances, but it doesn't matter. So, here we go.

I installed Ubuntu 14.10 yesterday so that I could test if my laptop performance is lowered because of the OS (Windows 8.1). I use it mainly for playing some older games, you can't do anything better with g102m anyways :P.  Firstly, I downloaded drivers from offical website, couldn't install it said it was some error. Then I oppened Additional Drivers and downloaded the first one from the list. Now my question, do I have newest drivers? Or I have to download it from the website? 

Thanks in advance! (Can't set a picture for some reason, here is the link)
[URL="http://tinypic.com/r/1znn2ux/8"]http://tinypic.com/r/1znn2ux/8


[/URL]

---

### Post by sandyd on 2015-01-02
> **Nikola_Jovanovic said:**
> This is my first post on ubutuforums, yey! Would love to be under some other circumstances, but it doesn't matter. So, here we go.

I installed Ubuntu 14.10 yesterday so that I could test if my laptop performance is lowered because of the OS (Windows 8.1). I use it mainly for playing some older games, you can't do anything better with g102m anyways :P.  Firstly, I downloaded drivers from offical website, couldn't install it said it was some error. Then I oppened Additional Drivers and downloaded the first one from the list. Now my question, do I have newest drivers? Or I have to download it from the website? 

Thanks in advance! (Can't set a picture for some reason, here is the link)
[URL="http://tinypic.com/r/1znn2ux/8"]http://tinypic.com/r/1znn2ux/8


[/URL]

Its best to use the one in the Additional Drivers dialog, as the version there has been tested to be compatible with Ubuntu.
Basically, if the card works with the drivers in the Additional Drivers dialog, it is best to leave it as is, as drivers installed manually from the nvidia site will break on certain updates and require you to do redo part of the installation. When installed using the Additional Drivers dialog, Ubuntu ensures that the driver does not break on updates. See [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) for details.

---

