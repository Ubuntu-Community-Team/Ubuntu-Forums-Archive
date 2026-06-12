---
title: "kubuntu crash"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by eric489 on 2008-09-19
hi

I've recently passed from gnome to kde.
Kde worked fine until the pc rebooted automatically and every time it now loads kubuntu, i get an error message (  linux isn't a crashing system like windows ... yeah right ... )

I have hence gone back to gnome and every kde program i try to launch gives me an error in return.

So what's the command to completely remove kde from my system ? 
And can i reinstall it back again ?

Thanks in advance.

---

### Post by Crafty Kisses on 2008-09-19
If you have the system the way you want and just want to remove KDE, do the following:
```
sudo apt-get remove kde
```
That should remove all packages for KDE.

---

### Post by eric489 on 2008-09-19
> **Codename said:**
> If you have the system the way you want and just want to remove KDE, do the following:
```
sudo apt-get remove kde
```
That should remove all packages for KDE.

Thanks, so can i reinstall kde right after again ?

---

### Post by Crafty Kisses on 2008-09-19
Yeah sure you can, just run these following commands:
```
sudo apt-get install kde
sudo apt-get install kde-core
```

---

### Post by eric489 on 2008-09-19
> **Codename said:**
> Yeah sure you can, just run these following commands:
```
sudo apt-get install kde
sudo apt-get install kde-core
```

Eh, small problem.
When typing sudo apt-get remove kde the system tells me that it didn't find the kde package.

:confused:

---

### Post by nowshining on 2008-09-19
then kde-core should work fine or try aptitude search kde

---

