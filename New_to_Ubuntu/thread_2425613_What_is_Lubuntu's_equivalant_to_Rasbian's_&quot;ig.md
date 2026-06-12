---
title: "What is Lubuntu's equivalant to Rasbian's &quot;ignore_lcd&quot;"
date: 2019-08-27
forum: New to Ubuntu
---

### Post by ioixd on 2019-08-27
I have a Model B Pi that I've recently loaded Lubuntu onto. I have a 7 inch touch screen that doesn't quite work with the Pi the correct way: I need to plug in some extra cables and insert "ignore_lcd=off" into Rasbian's "boot/config.txt" file, or else the screen turns black on start up and I can only access the Pi through an external Android app. In this case, the screen has turned black after start up, and I assume it's a related issue. How can I fix this, specifically through SSH?

---

### Post by guiverc on 2019-08-27
More detail might be needed. What release of Raspbian? and Lubuntu? 

*I think of Raspbian purely in terms of debian, but I need the releases to know what age/versions of kernel/software-stack you are using which will be the differences between the two I believe.*

---

### Post by ioixd on 2019-08-28
None of that actually matters, turns out the bug was non existent. I rebooted my Pi and Lubuntu boots up perfectly.

---

