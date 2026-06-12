---
title: "NVIDIA messed up"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by dynosis on 2012-06-27
i have 12.04, itried in vain to reinstall v173. now i have no drivers or i don't know what happened. my screen is off to the right, i can't see the dash anymore.
please help. i want to go back the way it was when i fisrt installed 12,04 i think with nouveau drivers??
thanks

---

### Post by jmfal on 2012-06-27
You should be able to move the screen back with the controls on you monitor..

---

### Post by papibe on 2012-06-27
Hi dynosis.

Boot into recovery mode, and run these commands:
```
sudo apt-get remove nvidia-*

sudo rm /etc/X11/xorg.conf
```
Next time you restart your machine, you should be using the nouveau driver.

Tell us how it goes.
Regards.

---

### Post by firekage on 2012-06-27
> **papibe said:**
> Hi dynosis.

Boot into recovery mode, and run these commands:
```
sudo apt-get remove nvidia-*

sudo rm /etc/X11/xorg.conf
```**Next time you restart your machine, you should be using the nouveau driver.**

Tell us how it goes.
Regards.

Or he would not if he had removed nouveau in order to install nvidia.

---

### Post by dynosis on 2012-06-27
thank you for reponses, i tried  your suggestions but to no avail. now i am only in text mode. says broken pipe. i tried reinstalling nouveau many times no go. if i knew this version 12.04 had bugs with nvidia would not have touched a thing. 
thank again. i think i will reinstall.

---

