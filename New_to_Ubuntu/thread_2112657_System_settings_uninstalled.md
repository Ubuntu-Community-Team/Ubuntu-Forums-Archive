---
title: "System settings uninstalled?"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Jake Sweeney on 2013-02-05
Hello everybody :)

I've recently installed the Cinnamon desktop environment on my Ubuntu 12.04 netbook and realised that my computer can't handle it.

After realising this I did the command:
```
sudo apt-get autoremove cinnamon -y
```
subsequently, it has also removed my system settings from "System Tools" (I am using Gnome).

Is there  package that I can install to get this back?

Thanks.

---

### Post by omeomi on 2013-02-05
If I remember correctly the package for that is gnome-control-center, so this should bring it back
```
sudo apt-get install gnome-control-center
```

---

### Post by Jake Sweeney on 2013-02-06
I've entered that command into the terminal and it says:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-control-center is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

So it IS installed, I just can't find it in the Gnome menu
](*,)

---

### Post by ObsidianArkmow on 2013-02-06
Have you tried...

> sudo apt-get update && apt-get install ubuntu-desktop

...?

---

### Post by deadflowr on 2013-02-06
> **ObsidianArkmow said:**
> Have you tried...



...?

Your command using the && treats it as two separate commands so you'll need a sudo for the second command or else it will result in a permission denied.

To the OP, have you looked in the alacarte(aka main menu) to see if system settings has been unchecked, it'll in system tools, but not in either administration or preferences just system tools.

---

