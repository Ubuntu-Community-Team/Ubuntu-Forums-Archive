---
title: "Software Updater taking hours to perform... Is this normal?"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by neotrader29 on 2017-11-14
Hello. I installed Ubuntu yesterday. I have no previous experience with Linux. About 2 hours ago I started an update through "software updater", it downloaded the update and asked to restart the computer. Since then, the opening "Ubuntu with the running five dots below it" image is showing up and nothing else happens. Is this normal? Or is it frozen? If so, what should I do?

---

### Post by VMC on 2017-11-14
I've had such problems in the past. I had to turn off IPv6 for my updates to work correctly. Read this article:
[https://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade](https://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade)

---

### Post by Impavidus on 2017-11-14
First it downloads the upgrade, then it installs the upgrade and then it asks you to reboot (if necessary for this upgrade). Most likely the upgrade included a kernel upgrade, as that's usually the reason to ask you to reboot. Can you use the grub menu to select an older kernel? It may work and give you at least a working system. But I'm not so familiar with these "fails to boot" errors.

---

