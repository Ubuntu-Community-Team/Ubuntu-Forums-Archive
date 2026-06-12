---
title: "[SOLVED] Duel boot Kbuntu and Ubuntu"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by old-codger on 2008-08-29
Can you duel boot Kbuntu and Ubuntu on the same hard disc? Will it have a menu to choose which one you want at boot up with? I tried to install Ubuntu with Kbuntu and at boot up got an error 18 ( I think it was 18). Tried to reinstall and it kept saying partition failed. Had to use gparted live to fix things. Thanks old-codger

---

### Post by Bachstelze on 2008-08-29
You can, but there's not much point in doing so. Just install *kubuntu-desktop* in your Ubuntu, and you will be able to use both (you choose which one you want to start at the login screen).

---

### Post by Swenghk on 2008-08-29
You can dual-boot, and when you start up, on the login screen, in the lower left-hand corner select, "Select Session", but I would advise against it as it will clutter your menus with KDE applications and GNOME applications.

---

### Post by old-codger on 2008-08-29
Thanks, I have been using Dapper for the last three years and tried the Kbuntu live disc and just wanted to try it a little more. May install it for a while to see how I like it. Thanks again old-codger

---

### Post by nothingspecial on 2008-08-29
This is really annoying if you do it,but

```
sudo apt-get install kubuntu-desktop
```

or if you`re using kubuntu already - 

```
sudo apt-get install ubuntu-desktop
```

You can then choose which flavour at login.

---

