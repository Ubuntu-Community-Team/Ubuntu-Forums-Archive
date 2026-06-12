---
title: "ubuntu software centre not working"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by krisli_hyland on 2013-10-20
when I type software-center in the terminal it say command not found wll not open at all in the default web browser

---

### Post by Impavidus on 2013-10-20
Typing **software-center** in the terminal should work. Make sure you didn't make a typo. In the default installation (with Unity) you should be able to search for it in the dash, in other flavours it should be in the menu. If all else fails, try reinstalling the software centre:```
sudo apt-get --reinstall install software-center
```Maybe you broke it somehow.

---

