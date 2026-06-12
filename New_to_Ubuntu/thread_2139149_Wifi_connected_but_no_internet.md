---
title: "Wifi connected but no internet"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Bram89 on 2013-04-26
Hey guys, I upgraded my laptop from 12.10 to 13.04 last night. On 12.10 my wifi and internet worked fine but now I'm on 13.04 it is connected to my Wifi network but when I start up my browser it says that no internet connection is available:confused:
Tried both Chrome and Chromium but to no avail. Does anyone have a solution or idea to solve this?

I currently use dualboot ubuntu-windows7.

any and all answers will be greatly appreciated :)

---

### Post by sanderj on 2013-04-26
I can't help you with Wifi. I can help you with IP problems: Can you the output of:

ifconfig
mtr -nrc2 8.8.8.8

---

