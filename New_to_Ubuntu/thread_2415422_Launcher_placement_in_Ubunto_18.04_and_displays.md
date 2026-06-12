---
title: "Launcher placement in Ubunto 18.04 and displays"
date: 2019-03-25
forum: New to Ubuntu
---

### Post by vysero on 2019-03-25
On Ubuntu 16.04 under displays there is an option to setup the Ubuntu launcher placement to both displays. Has this option really been removed in 18.04? I can not seem to find it.

---

### Post by Frogs Hair on 2019-03-25
16.04 uses the Unity desktop and 18.04 uses Gnome desktop. There is a 3rd party shell extension used to move and tweak the dock. 

[https://extensions.gnome.org/extension/307/dash-to-dock/](https://extensions.gnome.org/extension/307/dash-to-dock/)

---

### Post by deadflowr on 2019-03-27
Ubuntu Dock settings options in system settings are fairly tame.
But you should be able to set it to show on multiple monitors in dconf editor.
In dconf editor it should be in org > gnome > shell > extensions > dash-to-dock.
In there should be an option to set multi-monitor to on/true/green, which should set the dock to appear on all monitor screens.

Dconf editor needs to be installed, alternatively though you can run this command to do the same thing
```
gsettings set org.gnome.shell.extensions.dash-to-dock multi-monitor true
```

---

