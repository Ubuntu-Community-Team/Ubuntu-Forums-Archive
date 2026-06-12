---
title: "Ubuntu to do list app missing after upgrading to 23.04"
date: 2023-04-21
forum: New to Ubuntu
---

### Post by dilhan-chandrasiri on 2023-04-21
Hello,

Anyone experiencing this issue of to do list app is missing after upgrading to Ubuntu 23.04? 

I have upgraded my Ubuntu 22.04 LTS today to 22.10 and then to 23.04 and noticed to do list app is not there anymore.

---

### Post by bimblesticks on 2023-04-21
Have not upgraded to lunar personally, but after checking the package database, `gnome-todo` was renamed to `endeavour`. Here's the version of the package in Lunar: [https://packages.ubuntu.com/lunar/endeavour](https://packages.ubuntu.com/lunar/endeavour)

Try `sudo apt install endeavour`

---

### Post by dilhan-chandrasiri on 2023-04-21
Thank you very much. I installed it.

---

