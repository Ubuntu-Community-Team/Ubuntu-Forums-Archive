---
title: "Screen Brightness setting"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by uilliam on 2013-01-28
Hey
At completely random times my screen starts flickering between dark and bright, the meter comes up in the top hand corner as if i'm changing it myself but i'm not. Any ideas?
Thanks.

---

### Post by Toz on 2013-01-28
Can you provide some more information about your computer? 

1. The make and model.

2. The video card that you have and driver that is installed. Open a terminal window, type in the following command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```
...(enter your password when asked)

3. Your kernel boot line:
```
cat /proc/cmdline
```

---

### Post by ckunzler on 2013-01-29
has anything been spilled on the keyboard?

---

