---
title: "Fixed sound for Realtek ALC880 in 12.04"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by agemini68 on 2013-04-26
It took me a week to finally find the answer to this problem and it is pretty easy. In the terminal, type "alsamixer". When the panel comes up, press F6 to select sound card. Change from generic, to whatever is listed under that then reboot. When you go into sound settings, it will change from "dummy" to "analog output built in audio"

---

