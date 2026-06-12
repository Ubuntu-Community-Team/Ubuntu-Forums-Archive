---
title: "ubuntu 12.10 spamming multiple error messages on system login"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-10
ubuntu has been spamming me multiple error messages about system tools such as bluetooth, it later on reports that it seems you have modified the /etc/xdg/autostart/*.desktop files, i catched the bluetooth error applet in the location /etc/xdg/autostart/bluetooth-applet.desktop

here is what the bluetooth-applet.desktop looks like
 ```
[Desktop Entry]
Name=Bluetooth Manager
Comment=Bluetooth Manager applet
Icon=bluetooth
Exec=bluetooth-applet
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-bluetooth
X-GNOME-Bugzilla-Component=applet
X-GNOME-Bugzilla-Version=3.6.0
AutostartCondition=GNOME3 unless-session gnome
NoDisplay=false
X-Ubuntu-Gettext-Domain=gnome-bluetooth2
```

---

