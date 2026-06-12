---
title: "printer installation problems"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by dittto1 on 2013-12-31
I have been trying to install my Brother MFC 490cw printer. I downloaded the driver with the instructions for installing it using the terminal but over and over again it says that it cannot find the file. Any help would be appreciated. Thanks in advance

---

### Post by ajgreeny on 2013-12-31
More details please of the exact actions you have taken, the names of downloaded files, where you have them at the moment, and how you are trying to install them.

---

### Post by manudo on 2013-12-31
It says that you need the **ia32-libs** or **lib32stdc++** first, just type ```
sudo apt-get install lib32stdc++
``` or ```
sudo apt-get install ia32-libs
```
Then you install the .deb file you've downloded, in this case it have to be [this one]("http://www.brother.com/pub/bsc/linux/dlf/mfc490cwlpr-1.1.2-2.i386.deb").
Then use dpkg, example: ```
sudo dpkg -i mfc490cwlpr-1.1.2-2.i386.deb
```

Just wondering, that printer can be connected in USB or by a Wireless network, can be configured as generic printer in CUPS ([http://localhost:631](http://localhost:631)), but it's a multifunctional printer, it scans, try the first method then tell us if it work, that file that the installer is looking for may be that packages that are not installed, I guess.

---

