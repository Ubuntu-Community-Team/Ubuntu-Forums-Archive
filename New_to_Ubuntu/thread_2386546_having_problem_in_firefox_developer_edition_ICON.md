---
title: "having problem in firefox developer edition ICON"
date: 2018-03-07
forum: New to Ubuntu
---

### Post by niveshna2018 on 2018-03-07
hi 
   I am using UBUNTU 16.04 LTS .i recently downloaded firefox developer edition browser and installed with help of this forum members. but after i installed it is working good but there is question mark in the area of icon .when i click to see "NO IMAGE IS AVAILABLE".i already having in-built firefox in my system how do i get blue color firefox icon on my system pls help me guys...:(:(:(

---

### Post by &amp;KyT$0P# on 2018-03-07
Please post the contents of the .desktop file you used to create the launcher.

---

### Post by again? on 2018-03-07
The firefox-dev edition installs a launcher to ~/.local/share/applications/firefox-developer.desktop
Edit this file to use an icon of your choice.
```
gedit ~/.local/share/applications/firefox-developer.desktop
```

Currently the file points to a non existent icon file.
I've attached a png file you can use.
Use the full path to your icon file.
eg my ~/.local/share/applications/firefox-developer.desktop
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Firefox Developer Edition
Icon=**/home/glen/Pictures/icons/Firefox_Developer_Edition_logo.png**
Exec=/home/glen/.local/share/umake/web/firefox-dev/firefox %u
Comment=Firefox Aurora with Developer tools
Categories=Development;IDE;
Terminal=false
```

---

### Post by niveshna2018 on 2018-03-08
it is working good .:P:P 
my problem solved thank you very much

---

