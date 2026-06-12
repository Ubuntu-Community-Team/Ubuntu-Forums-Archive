---
title: "Network Connections"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Alienspecimen on 2013-04-21
Hello,

I accidentally deleted my network connections icon that was placed on the upper bar, where the power button, "date" and "applications" icons reside. It allowed me to view available networks in the area upon clicking on it.

I cannot find anything like it under all menus that I can pull up. How do I retrieve the icon and how do I view what connections are available in the area?

Thanks in advance.


P.S. The tools under preferences and administration menus do not have the ability to do so. Add to the panel tool does not have the icon I need

---

### Post by debodas on 2013-04-21
Are you using Unity? If not, which desktop environment are you using? Don't believe you can delete the applet in unity, at least now without a hack.

---

### Post by steeldriver on 2013-04-21
I'm not sure it's a 'hack' exactly but you could have done it in Unity by adding 'Unity' to the NotShowIn list in the nm-applet.desktop file (either globally in /etc/xdg/autostart, or per-user by overriding it with local nm-applet.desktop file in $HOME/.config/autostart - so check both) - this prevents nm-applet from starting

```
$ cat ~/.config/autostart/nm-applet.desktop
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
[COLOR=#0000ff]**NotShowIn=KDE;Unity;**[/COLOR]
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet


```

Not the kind of thing you can do accidentally though...

---

