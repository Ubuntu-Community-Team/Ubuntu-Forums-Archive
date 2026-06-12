---
title: "Connected to network but internet does not work"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by Lizardwithhat on 2012-07-04
Having problem getting online, when I connect to **any** WiFi or Ethernet the internet connection does not work, it says connected to ... but there is no internet, what is interesting that on the network I can go to directories and other files on the network server, Chromium and Firefox give an error 105 but also plugins don't download and the weather can't update but Ubuntu says it is connected and in network manager I do see that the computer is receiving network information in network manager, it is a 10.04 lts usb and it worked yesterday and today when i turned it on it won't, different computers and restarts etc. (usual stuff) does not work. :(

---

### Post by wildmanne39 on 2012-07-04
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

