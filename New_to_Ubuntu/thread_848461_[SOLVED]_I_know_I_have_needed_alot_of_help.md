---
title: "[SOLVED] I know I have needed alot of help"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-03
Well, I had my bro install compiz off some site and caused my desktop to not load. Well I re-installed and now I just need help on where and how to install compiz. Thanks

You can also help me thru AIM- deadlySniperRIO

---

### Post by wolfen69 on 2008-07-03
compiz is already installed. go to system>admin>hardware drivers. install your video card driver. reboot. then open the terminal and
Code:

```
sudo apt-get install compizconfig-settings-manager
```

then go to system>preferences>appearance>visual effects and enable "extra". then go to system>preferences>advanced desktop effects settings to enable what effects you want.

here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more.

---

### Post by ACJarrett on 2008-07-03
If you are running Hardy compiz will already be installed onto the distro.  An easy way to set it up is to use the Advanced Desktop Manager That you can download from Add/Remove programs under your applications menu.  I believe you need to check the option to view all to be able to download it though.

---

### Post by deadlySniper on 2008-07-03
I am running Xubuntu so system>preferences>appearance>visual effects isint there. I am very use to Ubuntu and openSUSE. So I dont know where the special effects would be.

---

### Post by dizee on 2008-07-03
Compiz is not installed by default in Xubuntu.

To install it (assuming you've installed the right graphics drivers and have 3d acceleration) do:
```
sudo apt-get install compiz compizconfig-settings-manager emerald fusion-icon
```

Run the Compiz fusion icon from the menu (should be under Accessories if I remember correctly), and then right-click on the icon in the system tray. From there, you can select the compiz window manager. Add "fusion-icon" to the autostarted applications in the Xfce settings if you want Compiz started every time you log in.

---

### Post by deadlySniper on 2008-07-03
E: Couldn't find package fusion-icon

I am guessing that I need to get compiz in synaptic or off somewhere

---

### Post by dizee on 2008-07-03
just do it without fusion icon then (I must have installed that manually):
```

sudo apt-get install compiz compizconfig-settings-manager emerald
```
then run (press alt+F2 for the run dialog) ```
compiz --replace
```

---

### Post by ChameleonDave on 2008-07-03
Please use a more descriptive title.  "I know I have needed alot of help" is useless for us helping you, and useless for people searching the forum for solutions.

---

