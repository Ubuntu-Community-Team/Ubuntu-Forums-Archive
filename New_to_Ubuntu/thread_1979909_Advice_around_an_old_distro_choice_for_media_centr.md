---
title: "Advice around an old distro choice for media centre"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by jermza on 2012-05-14
I'm running Ubuntu 12.04 on my main PC, but it requires a decent machine in order to run Unity 3D. I have an old P4 machine (with on-board graphics), from around 2005, with Windows XP on it. I'm going to be formatting it and setting it up with XBMC for my TV's dedicated media centre.

Obviously being used to Ubuntu's way of doing things, I'll probably stick to an Ubuntu derivative. I've heard that Unity 2D is on its way out, so I'll skip that option.

What do you suggest I install? Lubuntu? Xubuntu? Mint?

---

### Post by Lisiano on 2012-05-14
If you plan to use the machine solely for XBMC, then the ideal way would be to install XBMCbuntu [http://mirrors.xbmc.org/releases/XBMCbuntu/xbmcbuntu-11.0.iso](http://mirrors.xbmc.org/releases/XBMCbuntu/xbmcbuntu-11.0.iso)
It's XBMC preinstalled and configured on Ubuntu. When you use XBMC (As in pick to boot straight into XBMC) then it won't even load anything related to Unity 3D/2D or Gnome Shell or KDE or any other DE.

---

### Post by jermza on 2012-05-14
> **Lisiano said:**
> If you plan to use the machine solely for XBMC, then the ideal way would be to install XBMCbuntu [http://mirrors.xbmc.org/releases/XBMCbuntu/xbmcbuntu-11.0.iso](http://mirrors.xbmc.org/releases/XBMCbuntu/xbmcbuntu-11.0.iso)
It's XBMC preinstalled and configured on Ubuntu. When you use XBMC (As in pick to boot straight into XBMC) then it won't even load anything related to Unity 3D/2D or Gnome Shell or KDE or any other DE.

And will this help performance on such an old PC?

---

### Post by Lisiano on 2012-05-14
It will run the latest software Ubuntu can provide without Unity, so XBMC will get the most performance it can. Only way to have even more performance is to install Ubuntu core and install a bare X install, add MPlayer and use it. But then it's not a media center now is it.

EDIT: You are going to dedicate the box as a Media Center, so you can just try XBMCbuntu and if you don't like it, then try other buntus.

---

### Post by jermza on 2012-05-14
And how is Lubuntu's performance with XBMC? My guess is that should be quicker, but I don't know.  Thoughts?

---

### Post by Lisiano on 2012-05-14
Okay. The difference between Ubuntu, Lubuntu, Kubuntu and Xubuntu is the Desktop Environments they all use (Gnome/Unity, LXCE, KDE, XFCE respectively). That is the core difference between them. When you run XBMC as a media center, you will not use a DE, you will just boot directly into XBMC avoiding Unity, LXCE, KDE and XFCE. So Lubuntu will have less resource requirments when you use the desktop compared to XBMCbuntu but you will use the _same_ amount of resources when you only start XBMC without a DE.

---

### Post by roelforg on 2012-05-14
It's possible to make linux run under very low stuff.
Lubuntu should work on low-power systems.
Never tried it though, i have built my own ubuntu desktop setups beginning from ubuntu server and adding everything i need. And only that (used lxde). It runs in under 256MB ram on a PII with intergrated GFX just fine. So if you've got time and know your linux, you could do it that way and have a streamlined system.

---

