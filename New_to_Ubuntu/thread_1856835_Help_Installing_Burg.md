---
title: "Help Installing Burg"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by AnarkoNinja on 2011-10-09
Hi, I had a quick question for you...
In order to install Burg (to make choosing Windows easier on my wife), you have to install it to your MBR... how do I find out in which partition the MBR is located? 

Thanks in advance!!

---

### Post by ajgreeny on 2011-10-09
If you simply allowed your current grub to install by default, and did not manually change it to some other location, it will be on /dev/sda.  Note sda, not a partition such as sda1 or sda2;  just sda.

To confirm this you can use the **boot-info-script** link in my signature to download and run the script which will tell you near the top of the output RESULTS.txt file.

---

