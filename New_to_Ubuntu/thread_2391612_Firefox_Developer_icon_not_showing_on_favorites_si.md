---
title: "Firefox Developer icon not showing on favorites sidebar, but IS showing on Desktop."
date: 2018-05-11
forum: New to Ubuntu
---

### Post by aregowe on 2018-05-11
Firefox Developer icon not showing on favorites, but IS showing on Desktop.

Any ideas what's going on? I have my firefox-developer.desktop file in my /home/user/desktop directory, and the same file in my /usr/share/applications directory. Below is the exact same file for both. It shows the desktop icon for the desktop shortcut, but if I put it on the favorites sidebar, it doesn't show the icon, it's just blank.

Ubuntu 18.04

```
[Desktop Entry]
Name=Firefox Developer
GenericName=Firefox Developer Edition
Exec=/opt/firefox-developer/firefox/firefox
Terminal=false
Icon=/opt/firefox-developer/firefox/browser/chrome/icons/default/default128.png
Type=Application
Categories=Application;Network;X-Developer;
Comment=Firefox Developer Edition Web Browser.

```

---

### Post by leunam12 on 2018-05-11
Does it persist after reboot?

---

### Post by Keith Myers on 2018-06-05
I too am having issues with many .desktop files not being able to show any icon from the Dock.  It will not launch the app either.  The same .desktop file from a 16.04/Unity desktop file works there.  But half my applications in 18.04 either won't offer an Add to Favorites right-click option.   Or if they do and will actually dock, they won't show any icon and will not launch.

---

