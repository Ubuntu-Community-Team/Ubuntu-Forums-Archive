---
title: "Can't create launcher"
date: 2018-11-30
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-11-30
I can't seem to make a program launcher for jupyter or anaconda3, which don't install into the menu. They also don't show up on the program bar so I can't drag them to the menu. When I try 

```
lxshortcut -o ~/Desktop/myLauncher
```
and click on the desktop launcher, it just opens in leafpad.

I also saw I could edit the program file in pcmanfm to get a launcher, but there is no edit button in my version for some reason.

---

### Post by cybervigilante on 2018-11-30
Okay, solved. The file lxshortcut made had to have the .desktop extension, which I didn't put on, and be made executable.

---

