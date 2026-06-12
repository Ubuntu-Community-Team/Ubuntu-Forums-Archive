---
title: "how to install dell wireless WLAN 1395"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by srikantha2 on 2008-09-22
I installed UBUNTU in my pc


configuration of my pC


XPS M1530--
Dell wireless WLAN 1395

---
I want to know.how to install wireless driver. Wired network is working properly. 


---thank u

---

### Post by willca on 2008-09-23
Nice you got an XPS.

Can you tell what does lspci | grep -i ethernet  or lscpi | grep -i wireless  gives.... I am betting its another Broadcom chip. But anyway... the simplest way is to use the built-in driver installer in the repository (this is if you are using Hardy btw).

sudo apt-get install b43-fwcutter

Just follow the prompts.

Good luck.

---

### Post by wolfen69 on 2008-09-23
check for drivers in system>administration>hardware drivers

---

### Post by TriSwords on 2008-09-23
Hardwire and update Ubuntu, that fixed my problem. The kernel that came with the Live CD didnt work with the wireless, after the update it worked fine.

---

