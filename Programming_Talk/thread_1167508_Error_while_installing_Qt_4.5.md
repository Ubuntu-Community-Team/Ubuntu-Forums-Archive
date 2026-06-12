---
title: "Error while installing Qt 4.5"
date: 2009-05-22
forum: Programming Talk
---

### Post by thinhhoang on 2009-05-22
Hi guys! Using Ubuntu is so interesting, so I decided to start programming with Qt 4.5. Unfortunately, when I was trying these commands: 

chmod a+x qt-sdk-linux-x86-opensource-2009.02.bin
./qt-sdk-linux-x86-opensource-2009.02.bin


It threw me an error: No such file or directory. How can I come through this? Thanks for your help.

---

### Post by krazyd on 2009-05-23
qt 4.5 is  available in the repositories. Try ```
sudo apt-get install libqt4-dev
```

---

