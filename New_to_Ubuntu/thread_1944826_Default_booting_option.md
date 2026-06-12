---
title: "Default booting option"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-22
i have dual boot(win 7 & ubuntu) in my system.. how to make ubuntu as my default boot option..

---

### Post by mikewhatever on 2012-03-22
Ubuntu should be the default option. Perhaps you could explain how you got to the point that it isn't first. Is it a wubi install?

---

### Post by harimurugan on 2012-03-22
> **mikewhatever said:**
> Ubuntu should be the default option. Perhaps you could explain how you got to the point that it isn't first. Is it a wubi install?

s wubi only..

---

### Post by mikewhatever on 2012-03-22
There is probably an easy way to edit a Windows bootloader config file to make Ubuntu boot by default, and surely, someone will help you with that. I only wanted to point out that if you plan on using Ubuntu for an extended period of time, it would be best to do a proper installation to a dedicated partition. Wubi is intended for test installations or for those who don't use Ubuntu regularly and don't want to bother with partitioning.

---

### Post by mlupton on 2012-03-22
I would advise you to reinstall Ubuntu using the Live CD so that you can have an actual Ubuntu partition on your hard drive. As it is, Wubi is not a "real Ubuntu installation," if you wish to make it your default OS, you will need a full install.

---

### Post by Cheesemill on 2012-03-22
You can use EasyBCD from Windows to edit the Microsoft boot loader.

---

