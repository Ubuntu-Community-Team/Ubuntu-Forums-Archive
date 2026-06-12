---
title: "[SOLVED] Add/Remove without Synaptic"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-19
I am building a minimalist system from scratch using the server install and adding a window manager and file manager etc. on it.

Can I have the add/remove without having synaptic package manager?

What is the package name for the Add/Remove program?

I am a happy camper in using commands to install stuff than Synaptic. But having at least Add/Remove helps in discerning the usefulness of the app before having to install it and also lets you know the package name if its not known.

---

### Post by HotShotDJ on 2008-05-19
> **Inxsible said:**
> Can I have the add/remove without having synaptic package manager?```
sudo apt-get install <package>
sudo apt-get remove <package>
sudo apt-get autoremove <package>
```the autoremove will get rid of un-needed packages that were pulled in by a now-deleted package.

---

### Post by SunnyRabbiera on 2008-05-19
well if you need a minimalistic package manager, but want something with a more GUI interface there is always aptitude.

---

### Post by Inxsible on 2008-05-19
No  I mean the application Add/Remove which is under Applications>>Add/Remove.

What is the package name for that app?

---

### Post by HotShotDJ on 2008-05-19
> **Inxsible said:**
> No  I mean the application Add/Remove which is under Applications>>Add/Remove.

What is the package name for that app?OH!  Its gnome-app-install

---

### Post by SunnyRabbiera on 2008-05-19
gnome-app-install

---

### Post by JC Cheloven on 2008-05-19
Just in case: if you have a command-line system installed, and want to build a desktop system from that, this should be one way:

sudo aptitude install xorg
sudo aptitude install metacity
sudo aptitude install gdm
sudo aptitude install gnome-terminal
sudo reboot

If you want all the software which comes with ubuntu by default, from a terminal:
sudo aptitude install ubuntu-desktop

This would be (in principle) equivalent to an standard ubuntu installation.
Greetings

---

### Post by Inxsible on 2008-05-19
No gdm for me. A CLI login is sufficient. My laptop can support Xubuntu fine. I just hate the fact that any and all distros give you a set of apps and I am almost always unhappy with that set ;).

I might even use Thunar as File Manager and xfce4 as Window Manager if I don't find Flux, Ice, Enlightenment or FVWM-Crystal to my liking

I want to build a minimalist system and install what I want. The only drawback I see to this is during the next upgrade, I might have to re-install the new OS and then install all the apps again. But I don't have a problem with that.

---

### Post by Inxsible on 2008-05-19
> **HotShotDJ said:**
> OH!  Its gnome-app-install

> **SunnyRabbiera said:**
> gnome-app-installand can you have that without having the need to install synaptic?

---

