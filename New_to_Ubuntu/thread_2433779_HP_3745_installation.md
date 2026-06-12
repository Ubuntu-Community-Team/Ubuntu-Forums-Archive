---
title: "HP 3745 installation"
date: 2019-12-25
forum: New to Ubuntu
---

### Post by symbio2 on 2019-12-25
How do I install HP 3745 printer driver to print by lubuntu?

---

### Post by CelticWarrior on 2019-12-25
First thing to try is installing HPLIP.

---

### Post by symbio2 on 2019-12-25
Thanks for this guide but how do I install this HPLIP? I tried to find it in software but I have found nothing :(

---

### Post by CelticWarrior on 2019-12-25
```
sudo apt install hplip
```

---

### Post by symbio2 on 2019-12-25
sorry I am newbie here so I didnt know how to install it.
Bu I have done. what next?

---

### Post by CelticWarrior on 2019-12-25
Reboot, reconnect the printer, check if it's detected, try to print?

---

### Post by symbio2 on 2019-12-25
I did everything but my lubuntu does not detect anything. Printer is connnected and on.

---

### Post by mörgæs on 2019-12-25
What happens if you enter ```
localhost:631
``` in a browser?

---

### Post by yancek on 2019-12-26
How about reading through the Ubuntu documentation on configuring printers, link below.  Have you gone through all of those steps?  What specifically were the results?  Warnings, error messages?

[https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en](https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en)

---

