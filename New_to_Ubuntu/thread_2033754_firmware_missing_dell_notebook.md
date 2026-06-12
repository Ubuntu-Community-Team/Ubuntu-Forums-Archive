---
title: "firmware missing dell notebook"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by zakuan96x on 2012-07-26
[CENTER]what should we do if our laptop did not detect wireless 
the problem is firmware missing 
im so sad :([/CENTER]

---

### Post by wildmanne39 on 2012-07-26
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

