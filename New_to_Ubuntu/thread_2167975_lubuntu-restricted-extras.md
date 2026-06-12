---
title: "lubuntu-restricted-extras"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by jamesfbays on 2013-08-15
Using Lubuntu 13.04, I cannot find the restricted extras in the Lubuntu Software Center nor in the Synaptic Package Manager. I also tried sudo apt-get lubuntu-restricted-extras and sudo apt-get lubuntu-restricted-install lubuntu-restricted-extras from the XTerm with no luck. Please help. I want to watch Youtube. Thanks. :)

---

### Post by ibjsb4 on 2013-08-15
Try

```
sudo apt-get update
```

Then see if it shows up

---

### Post by vasa1 on 2013-08-15
Which software sources have you enabled? What you want is in "multiverse". If that is enabled, you should see lubuntu-restricted-extras.

> Package: lubuntu-restricted-extras
Priority: optional
Section: **multiverse**/metapackages


To see what is enabled, click on Menu, Preferences, Software and Updates. There, make sure that "Software restricted by copyright ..." is **ticked**.

Run **sudo apt-get update**. You should then be able to install lubuntu-restricted-extras.

---

### Post by jamesfbays on 2013-08-15
Thanks guys.

---

