---
title: "ath9k wireless no fix"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Lumbeast on 2011-09-13
I have literally gone to every website and tried everything possible to fix these slow download speeds and it will not work. I have tried the power management thing, the kernel upgrade and that "options nohwcrypt" thing and none of them work. Please help

---

### Post by futralistic on 2011-09-13
This is what worked for me. 

Enter this in a terminal.

sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf


Then reboot from the same terminal.

sudo reboot


After the reboot everything worked perfect.

---

