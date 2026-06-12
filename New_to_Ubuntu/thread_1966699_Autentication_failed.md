---
title: "Autentication failed"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Ralf069 on 2012-04-27
hi, i already installed Ubuntu 12.04 yesterday, but i have problems guys i hope you can help me please, the 1st problem i have is that my internet conection is slow, slowest than windows, and that is weird, cause i have a 5mb conection, and my other problem is that i can't enter to emesene, pidgin or emphaty, it says Autentication failed, i hope you can help me guys.... thanks and have a great day!!!

---

### Post by codingman on 2012-04-27
Does it give you an error message? Oh, and this forum is for Quantal, not Precise, Precise is now every forum except the +1 forum ;).

---

### Post by nothingspecial on 2012-04-27
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by wildmanne39 on 2012-04-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mobisallen on 2012-04-28
i can b due to the compatibility of the device with the software. u must check the system requirement before updating or installing new device, because when u install a new software or update then it also contains the new features. may b your device can not installs that new features properly and if it installs then also it is slow due to the over burden on your memory. the second thing is this, that the software u installed or updated is not properly installed. ist check the system requirements then install again,

---

