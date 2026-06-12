---
title: "ubuntu installation ideas"
date: 2020-09-18
forum: New to Ubuntu
---

### Post by ziywang50 on 2020-09-18
Hi,

I try to install dual boot ubuntu on my Lenovo ideapad flex, which is automatically installed windows 10 when I bought it. My computer is using UEFI-GPT. I formatted a USB drive using Rufus, then used an iso image of ubuntu 20.04. After I tried to install, I got a message saying intel RST is present on my computer. Since I am using intel RST, I read this post: [https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347). After reading, I am wondering what kind of computers will have the problem of windows would not boot. I have heard that if there is RAID opened on the computer, then it will likely not boot. Is this sentence correct? Also, have anybody use Lenovo computers? I am new to this. 

Best,
Ziyue Wang

---

### Post by CelticWarrior on 2020-09-18
Welcome.

Install AHCI support in Windows.
Change the setting in UEFI to AHCI.
Done.

---

