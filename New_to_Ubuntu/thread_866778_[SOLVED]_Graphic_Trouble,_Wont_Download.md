---
title: "[SOLVED] Graphic Trouble, Wont Download"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by brudfix on 2008-07-22
Hi,

My Hardware drivers  says that Nvidia Accelerated card can be enabled, but when i press enable and it try to download i get the Message 

[CENTER][B]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_amd64.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_amd64.deb)
  404 Not Found[/B][/CENTER]

What is wrong then?

---

### Post by Sbarton on 2008-07-22
Have you gone to System/Administration/Hardware Drivers and enabled it from there?
regards

---

### Post by brudfix on 2008-07-22
Yes when i do that i get the wrong message again:(

---

### Post by Ryadt on 2008-07-22
Try updaing your system.
Type in terminal```
sudo apt-get update
```
then```
sudo apt-get upgrade
```
After upgrading retry enabling the driver.

---

### Post by Sbarton on 2008-07-22
System/Administration/Software sources, under the Ubuntu Software tab are the top 4 boxes ticked? if not tick(select) any not ticked.
regards

---

### Post by brudfix on 2008-07-22
Now it did work, thank you very much Ryadt:)

---

### Post by Ryadt on 2008-07-22
Your welcome..:)
Can you please mark the threat as solved..

---

