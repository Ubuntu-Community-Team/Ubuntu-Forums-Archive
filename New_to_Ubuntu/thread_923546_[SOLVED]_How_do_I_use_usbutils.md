---
title: "[SOLVED] How do I use usbutils?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-09-18
I'm sure that it usually just "works on its own", but if i wanted to use it to actually view every USB device I have connect, what would I enter into terminal?

---

### Post by szymon_g on 2008-09-18
lsusb :?

---

### Post by Titan8990 on 2008-09-18
This command lists connected USB devices:

lsusb

---

### Post by bobnutfield on 2008-09-18
If you want complete information, including power, speed, etc. from all devices, type:

> sudo lsusb -v

---

### Post by whoscheesemine on 2008-09-18
thanks guys, SOLVED!

may seem pointless, but i'm sure the keywords used in this topic will be helpful to someone searching the forums in the future

---

