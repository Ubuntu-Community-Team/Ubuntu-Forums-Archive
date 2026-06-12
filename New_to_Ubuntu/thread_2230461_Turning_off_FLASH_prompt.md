---
title: "Turning off FLASH prompt"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by Bewildered_Bob on 2014-06-19
Lubuntu 14.04 was successfully installed but now it prompts every few seconds offering to install FLASH which i prefer NOT to install now. How can the annoying prompts be stopped forever ??

========================
Remember i'm a v-e-r-y NEWBIE.
========================

Thanx.
Bewildered & Bothered Bob

---

### Post by Impavidus on 2014-06-19
One possibility is that you, via the Lubuntu installer by selecting to install restricted software, installed a package called **flashplugin-installer**. If this package failed to download and install flash it will periodically prompt you to try again.

Open the software centre and search for **flashplugin-installer**. If it has been set as installed, uninstall.

---

### Post by Bewildered_Bob on 2014-06-20
Hello Impavidus: i searched "all categories" for flashplugin-installer but it was not found. Anything else i can try ?  Thanx.

Bewildered

---

### Post by Impavidus on 2014-06-20
I don't know why it isn't found (it shows up when I type the name in the search window in the upper right corner, although it appears under it's less technical name of Adobe Flash-plug-in), but you can also check flash's status via the terminal:```
dpkg --list flash*
```

---

