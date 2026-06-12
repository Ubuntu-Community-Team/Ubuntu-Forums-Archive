---
title: "Nvidia driver problems"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by gingo3 on 2016-09-01
Hi, I just installed Xubuntu but I don't see the prime profile option in "nvidia x settings" so I can not change the active gpu. How can I change this so I can switch between cpu's
 
Nvidia x server settings: 
[URL="http://i.imgur.com/uHfcHNR.png"]http://i.imgur.com/uHfcHNR.pngNv

[/URL]Drivers:
[http://imgur.com/IQi0HyEl.png](http://imgur.com/IQi0HyEl.png)

Output when I run > lspci -k | grep -EA2 'VGA|3D'

```
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    Subsystem: ASUSTeK Computer Inc. Skylake Integrated Graphics
    Kernel modules: i915_bpo
--
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. GM107M [GeForce GTX 960M]
    Kernel driver in use: nvidia


```

Specs:
```
 CPU
    Intel Core i7 6700HQ @ 2.60GHz  44 °C
    Skylake 14nm Technology
RAM
    16.0GB
Motherboard
    ASUSTeK COMPUTER INC. GL552VW (U3E1)
Graphics
    Generic PnP Monitor (1920x1080@60Hz)
    Intel HD Graphics 530 (ASUStek Computer Inc)
    4095MB NVIDIA GeForce GTX 960M (ASUStek Computer Inc)   50 °C
    ForceWare version: 372.54
    SLI Disabled
```

---

### Post by gingo3 on 2016-09-02
I fixed the problem where I only had a 800x600 resolution using [this]("http://askubuntu.com/questions/744698/video-drivers-not-working-ubuntu-800x600-only-resolution") post. But I still can't change gpu using nvidia settings.

---

### Post by Bucky Ball on 2016-09-02
Please share exactly what you did to fix the problem (link to the post and solution) and then mark the thread as 'solved' using Thread Tools to help others if you wouldn't mind. Thanks. :)

PS: You can attach large images rather than inserting them using 'Go Advanced' or 'Adv Reply' and the paperclip icon.

---

### Post by gingo3 on 2016-09-02
Thanks for telling me I edited the post with the correct post but I still have another problem with switching gpu's.

---

### Post by Bucky Ball on 2016-09-02
Got you. All good, although you'll have more luck if you start a new thread with a title describing the new issue. You've fixed the driver problem. It would improve your chances. Link back to this thread for background if you like. Good luck. :)

---

