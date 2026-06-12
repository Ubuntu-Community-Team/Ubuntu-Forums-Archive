---
title: "Switch back to ubuntu Login from Kubuntu"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Djanvk on 2008-09-07
First off I am having the after login screen black screen back to the login screen problem.

I was able to login using the xfdc and icewm desktops but cannot with gnome.  So I though I would install KDE and used the 

sudo apt-get install kubuntu-desktop command

That installed just fine and now when I restart the system it's the blue Kubuntu login screen and not the gnome screen which is fine, BUT I cannot login with anything now, not xfce or icewm.

I'm have ubuntu 8.04 on a Dual boot system of Win XP.

Any help much appreciated.

Thansks

---

### Post by Xiong Chiamiov on 2008-09-07
```

sudo dpkg-reconfigure gdm

```
and choose gdm as default.

---

### Post by Djanvk on 2008-09-07
Ok that worked but still have the kubuntu screen with a ubuntu login type of screen.

Is there a way to uninstall ubuntu then reinstall ubuntu?

---

### Post by gjoellee on 2008-09-07
on the login screen click on Sessions and find GNOME.

If you started using "KDM" instead of "GDM" this might be the problem. You can most likely configure the widnow display manager back to GDM if you install ubuntu-deksotp again....


```
sudo apt-get install ubuntu-desktop
```

---

### Post by Xiong Chiamiov on 2008-09-07
Oh, you want to change the loading screen.

You could reinstall, but [this]("http://ph.ubuntuforums.com/showthread.php?t=862124") should be easier.

---

### Post by Djanvk on 2008-09-07
Yep got it, thanks.  Still wish I could used Gnome without have to do that failsafe gnome.

---

### Post by Xiong Chiamiov on 2008-09-07
> **Djanvk said:**
> Yep got it, thanks.  Still wish I could used Gnome without have to do that failsafe gnome.
Wait, what failsafe gnome problem?  Rather than giving workarounds, we might be able to fix the actual problem.

---

