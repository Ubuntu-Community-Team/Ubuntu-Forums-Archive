---
title: "How to enable polling for network card in ubuntu?"
date: 2011-03-11
forum: Programming Talk
---

### Post by vaibhaviitd on 2011-03-11
Hi all,

Network interface card is by default interrupt driven.
I want to enable polling support for network interface card in ubuntu. 
Its based on 2.6.32 linux kernel.
I am not able to find for any module option in kernel menuconfig.
Can anyone please help me to sort it out?

Thanks in advance..

---

### Post by Zugzwang on 2011-03-11
Apparently, it's not supported by every network card driver.

Look here for one particular card: [http://www.cyberciti.biz/faq/rhel-centos-fedora-debian-configure-rx-polling-mode/](http://www.cyberciti.biz/faq/rhel-centos-fedora-debian-configure-rx-polling-mode/)

I would suggest that you find out which network device you have (use the dmesg command in the terminal), and surf the web to see whether what you want to do is actually supported. If you don't find andthing, get the kernel source and just "grep" for your polling mode.

---

### Post by vaibhaviitd on 2011-03-11
Thanks for reply.
My Network card is based on Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01).
It supports NAPI (Polling).
I tried to find the polling option in kernel menuconfig, but it was not there.
Is there any other way to do it?

---

