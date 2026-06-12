---
title: "need help installing HP LaserJet Pro M225dw AIO printer"
date: 2018-11-27
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2018-11-27
Just upgraded from UM 16.04 (under which I had this printer installed) to UM 18.04.1. Have tried to reinstall the printer using Wifi and ethernet. It seems to find the printer, but after many repeated configuration attempts, no printing occurs. 

Assistance needed please. What info can I provide? Thanks.

HP Pavilion P7-1000 with 8GB RAM

---

### Post by Autodave on 2018-11-27
Upgrading from one version to another rarely works well.  I learned a long time ago to only use the LTS releases and to always do clean installs.  You can backup everything you need to keep to an external source and then do a clean install.

Hint: have your printer on when you do the install: it shoul;d find it and install everything that you will need.  Mine did that installing 18.04: found it wirelessly and enabled everything including scanning functions.  Quite a surprise!

---

### Post by Odyssey1942 on 2018-11-27
Thanks and I agree. In fact I did a clean install. Guess my "upgraded" was confusing. Meant it as going to a newer version.

---

### Post by Odyssey1942 on 2018-11-27
Stumbled across this on YouTube. 

```
sudo apt-get install hplip-gui

```
Magic! Worked a charm on the printer and all is good.

---

