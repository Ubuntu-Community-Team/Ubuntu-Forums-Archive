---
title: "[SOLVED] black screen at install"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by ttiell on 2008-07-08
I tried to install within XP Pro.  It says that it installed completely and restarts.  at restart, I have a choice between Ubuntu and XP.  If I choose Ubuntu, I see a gui of Ubuntu and a status bar.  When the status bar completely fills...I get a black screen.  I'm guessing graphics card drivers need to be set up but I don't know which or how.  I have a Foxconn Nividia 8400GS-256.

---

### Post by LowSky on 2008-07-08
try starting ubuntu in safe mode. When you get to a login screen login and the type at a terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ttiell on 2008-07-08
Do you mean that I can only use Ubuntu in safe mode?  Isn't there a way to fix this problem and not just go around?

---

### Post by bobnutfield on 2008-07-08
No, you will not have to continue to run in safe mode.  This command is simply to reconfigure your x server to get to a gui desktop.  You will have to get the propriatory Nvidia drivers, though if you want to get the most out of your graphics.  Once you have a stable desktop, you can go to System>Amin>Hardware Drivers and it will show you a message that drivers are available.

Bob

---

