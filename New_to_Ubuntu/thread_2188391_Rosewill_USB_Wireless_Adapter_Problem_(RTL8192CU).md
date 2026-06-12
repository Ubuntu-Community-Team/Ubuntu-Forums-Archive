---
title: "Rosewill USB Wireless Adapter Problem (RTL8192CU)"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by palmgrower on 2013-11-17
I have 2 Rosewill USB wifi adapters, RNX-N150 (N 150mbps) and RNX-N250 (N 300). The former works well, but the latter drops connection every 5 minutes and when browser gets closed. Found RTL8192CU-FIXES for Ubuntu 13.10 here
[https://github/com/pvaret/rtl8192cu-fixes](https://github/com/pvaret/rtl8192cu-fixes) (Just copy and paste commands in terminal)
Two minor changes from the installation instructions are:
sudo apt-get install git (this first, before everything) and
"depmod -a" gave "permission denied". But now I am connected for about an hour.

---

