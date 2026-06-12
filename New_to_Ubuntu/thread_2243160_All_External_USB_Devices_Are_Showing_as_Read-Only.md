---
title: "All External USB Devices Are Showing as Read-Only"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by ScooterBoogles on 2014-09-06
Suddenly all 3 of my external Hard drives (250 GB, 1 TB, and 8GB, different manufacturers) are showing as read-only. Why could that be?

It says:

Error while copying to "Device"

The destination is read-only.

---

### Post by ScooterBoogles on 2014-09-06
Ah, I see, I'm suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375)

---

### Post by drpjkurian on 2014-09-07
Hi
Till the bug gets fixed, I can suggest you an alternate pathway. Try
```
sudo nautilus
```
enter your sudo password. A new window will open which allows you to navigate to your external HDD and copy any number of files to it

---

### Post by vasa1 on 2014-09-07
> **drpjkurian said:**
> Hi
Till the bug gets fixed, I can suggest you an alternate pathway. Try
```
sudo nautilus
```
enter your sudo password. A new window will open which allows you to navigate to your external HDD and copy any number of files to it
gksudo maybe better for GUI-apps. There's also something called pkexec but I don't know much about that.

---

### Post by ScooterBoogles on 2014-09-07
Thank you! sudo nautilus seems to be working great. Much obliged.

---

### Post by drpjkurian on 2014-09-08
You are most welcomw

---

