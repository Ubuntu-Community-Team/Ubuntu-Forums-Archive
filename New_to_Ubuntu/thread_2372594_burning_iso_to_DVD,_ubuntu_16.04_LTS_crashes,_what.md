---
title: "burning iso to DVD, ubuntu 16.04 LTS crashes, what am I doing wrong?"
date: 2017-09-26
forum: New to Ubuntu
---

### Post by mtjoy747 on 2017-09-26
I downloaded an ISO, I installed Brasareo, ran it, chose the blank DVD-R in the drive, chose the ISO, "sorry Ubuntu has crashed", sent the report, rebooted, tried second time, same result, sent second error report, any ideas on how to fix?

---

### Post by Geoffrey_Arndt on 2017-09-26
Brasero has had it periods of instability over the years.

Instead, a better solution is K3B (although it will pull in kde deps.)    Another thought:   if the machine is capable of usb thumb drive boot, then try out "Etcher" [https://etcher.io/](https://etcher.io/)

---

### Post by ajgreeny on 2017-09-27
If you really prefer DVDs give xfburn a try, it is the CD/DVD burner from Xubuntu and uses GTK libraries just like brasero.

It uses a more reliable background app to do the burning so is less likely to fail and will not pull in masses of KDE libraries that you prefer not to have on the system.

---

### Post by leunam12 on 2017-09-27
Try from the terminal ```
sudo cdrecord -v -dao speed=4 dev=/dev/dvd /path/to/foobar.iso
```replace path/to/foobar.iso with the path to your ISO file

---

### Post by HermanAB on 2017-09-28
Err... you are trying to make install media?  Just copy the ISO file to a USB memory stick using either dd or cat.  It is much easier and quicker.

---

