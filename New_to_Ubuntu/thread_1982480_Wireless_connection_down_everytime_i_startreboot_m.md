---
title: "Wireless connection down everytime i start/reboot my laptop"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by mvburgos on 2012-05-18
Hello everytime i start or reboot my laptop some connections like wireless and Bluetooth are down, what i do is run the command:

```
sudo rfkill unblock all
``` 

that fixes it until net reboot or start of Ubuntu.

How do i fix this issue permanently?

Thank you in advance

---

### Post by wildmanne39 on 2012-05-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

