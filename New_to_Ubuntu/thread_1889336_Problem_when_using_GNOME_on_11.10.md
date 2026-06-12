---
title: "Problem when using GNOME on 11.10"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by gatgat23 on 2011-12-01
When I log in with GNOME, the panels are not appearing. It seems like, it has no interface. I even waited for many minutes. Can someone help me? 

BTW, I'm using nVidia GeForce 5500 FX with the recommended drivers on Additional Drivers app. Help please.

---

### Post by colobix on 2011-12-01
Since you said "panel", I assume you mean Gnome's fallback mode (classic). Gnome3 doesn't have panels. And ubuntu 11,10 doesn't come with gnome 2.
If you want the panels back, you should either go for the XFCE environment (comes pre-installed) or you can install Mate (a gnome 2 fork).

---

### Post by gatgat23 on 2011-12-01
I don't know if I said it right. But when I said panel, I mean it's the top bar. GNOME Classic works. But GNOME, doesn't. I can only see my wallpaper and I can highlight, right-click. But the top bar isn't appearing. Even when I press Super key, nothing happens. Help please.

---

### Post by gatgat23 on 2011-12-01
Help please. :(

---

### Post by cortman on 2011-12-01
I'm far from an expert, but try checking for broken packages and reload gnome?

```
sudo apt-get -f install gnome-shell
```

---

### Post by gatgat23 on 2011-12-01
Here's what it said:
```
sudo apt-get -f install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by gatgat23 on 2011-12-02
Bump. Help please. I want to use GNOME, and tweak that thing. :(

---

### Post by lolpenguin on 2011-12-02
This usually happens when an extension messes things up...no window manager, no shell.

---

### Post by gatgat23 on 2011-12-02
> **lolpenguin said:**
> This usually happens when an extension messes things up...no window manager, no shell.

What can I do then? I reinstalled gnome-shell, but still, no interface. :confused:

---

### Post by lolpenguin on 2011-12-02
Does Unity (3D) work?
Are all the dependencies installed? libmutter, clutter, etc.

---

### Post by -kg- on 2011-12-02
it sounds to me like he's already in Gnome 3D  Log out or reboot, then when you come to the Log In screen, click the little button to the right of the text box.  In the menu, you should see two selections...Ubuntu and Ubuntu 2D.  Select Ubuntu 2D then log in and see what you have.

---

### Post by gatgat23 on 2011-12-03
> **lolpenguin said:**
> Does Unity (3D) work?
Are all the dependencies installed? libmutter, clutter, etc.
Nevermind that. Found out that my video card is blacklisted and can't even run Unity 3D. I can run the Ubuntu environment but can't use Unity 3D. So, I think that's it.
> **-kg- said:**
> it sounds to me like he's already in Gnome 3D  Log out or reboot, then when you come to the Log In screen, click the little button to the right of the text box.  In the menu, you should see two selections...Ubuntu and Ubuntu 2D.  Select Ubuntu 2D then log in and see what you have.
I can log in on Ubuntu 2D. But, I found my answer. Look above.

Will make this thread as solved?

---

### Post by lolpenguin on 2011-12-03
Click thread tools, then mark as solved.

---

