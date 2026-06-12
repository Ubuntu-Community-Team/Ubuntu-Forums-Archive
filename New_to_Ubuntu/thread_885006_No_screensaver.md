---
title: "No screensaver"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Animeniac on 2008-08-09
I have installed the graphics card driver for my NVIDIA GeForce 4 MX by using EnvyNG. I've also installed Compiz-settings-manager, emerald and xserver-xgl. And now the screensaver never pops up whenever it is idle for 10 minutes. Yes, I've have selected a screensaver from "Screensaver" under "Preferences".

How can I make the screensaver work again? Thanks?

---

### Post by Mazza558 on 2008-08-09
So does compiz/emerald work?

---

### Post by Animeniac on 2008-08-09
> **Mazza558 said:**
> So does compiz/emerald work?

Yes.

---

### Post by SZ07 on 2008-08-09
When you lock your screen, does the screensaver start?

In the General Options for Compiz, uncheck "unredirect fullscreen windows" and see if it makes any difference. If not change it back to the default setting.

As a last resort, you could uninstall the gnome-screensaver package (using the completely remove option in Synaptic) and then reinstall it.

---

### Post by Animeniac on 2008-08-11
The screensaver does work if I uncheck "unredirect fullscreen windows", but I have to move the mouse a little, in order to see the screensaver when the computer has been idle for the time the screensaver is set to start.

---

### Post by alienexplorers on 2008-08-11
Do you have power management set to turn off your monitor after 10 minutes.  If so, you will never see your screensaver since the monitor will be off.

---

### Post by Animeniac on 2008-08-11
I have the power management set to turn off my monitor after 40 minutes. I have the screensaver set to turn on after 10 minutes.

---

