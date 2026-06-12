---
title: "[SOLVED] Nothing happens after login"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by jsdieorksw on 2008-06-03
I'm new to ubuntu, i purchased a new dell laptop a few weeks ago with 7.10 pre-installed.  It worked great, keyword: worked.  I got around to upgrading a few days ago and ever since I've been having problems.  My bittorrent client was acting up, I completely lost audio, and now after I login nothing happens.  Just a blank orange screen.  I can login (but nothing happens), take screenshots, and get the shut down menu to come up, but that's it.  My computer is about as useful as a rock right now.  Can anyone help? Is there anyway to get back to 7.10?

---

### Post by abn91c on 2008-06-03
make sure you did not download a tar ball, if you can open a terminal try sudo aptitude reinstall gnome-desktop

---

### Post by jsdieorksw on 2008-06-03
I can't access the terminal, I can't access anything.  After I login the screen is the standard orange and doesn't change.

---

### Post by ajgreeny on 2008-06-03
So try pressing Ctrl+Alt+F1 to go to a console and there try ```
sudo apt-get install --reinstall gnome-desktop
```or perhaps ubuntu-desktop instead of gnome-desktop, but I don't think that is the problem.

It may well be that you have lost the graphics driver, having now updated.  Without knowing your hardware in detail it's difficult to know where to go, but I'm sure others may be able to help more.  If you know the hardware, get back with more info and we may be able to help.

---

### Post by ChameleonDave on 2008-06-03
So your Gnome installation is screwed for some reason.

OK, just use another desktop environment whilst you get that fixed.

Hit Ctrl + Alt F1 or F2 to switch to the terminal, and then enter this:

```
sudo apt-get install fluxbox
```

Fluxbox is nice and lightweight.  You could, if you liked, take the opportunity to try out KDE or XFCE.

When on the log-in screen, you get to choose which desktop environment you want to use.

---

### Post by jsdieorksw on 2008-06-03
Sounds good, I'm currently not with my laptop, I'll post back soon when I try these suggestions out. Thanks guys!

---

### Post by jsdieorksw on 2008-06-03
Problem solved! You guys are wonderful! I re-installed gnome and now it works!

---

