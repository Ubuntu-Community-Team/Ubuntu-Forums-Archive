---
title: "organizing my desktop in ubuntu 17.04"
date: 2017-10-16
forum: New to Ubuntu
---

### Post by ftbaker2 on 2017-10-16
I have just installed ubuntu on two minis which ran poorly on windows because of insufficient memory and/or processor. I am astounded by how well those machines now work. I am also impressed by how much better ubuntu has gotten since I first tried it several years ago. My problem is that I have trouble finding apps which I have not pinned to the Launcher without scrolling through the lengthy list of installed apps. In Windows, which was my sole OS for as many years as it has been in existence, I just put shortcuts to my most frequently used apps on the desktop and organized them in folders. In ubuntu I am unable to drag an app icon to the desktop; maybe the concept of "shortcut" is not used in ubuntu?

---

### Post by ajgreeny on 2017-10-16
Once you have found an application and opened it the launcher (or shortcut) will appear in the launchbar on the left.  Before you close the app right click in its launcher and choose "Lock to launchbar" and it will remain there. You can order the icons by dragging up or down.

You can also use the dash by clicking on the top icon in the launcher then start typing the name or description of the app you want and one or more launchers for apps will show on the screen.

---

### Post by ftbaker2 on 2017-10-16
Thanks for your reply. I had already figured out how to lock apps to the launcher. However, I want only a few very frequently used apps there, not everything I might occasionally use. I don't suppose you could have files in the launcher? 
Your comment about using search to quickly locate a particular app was helpful and a step in the right direction; I would still rather have a folder(s) from which I could quickly start some apps.

---

### Post by ajgreeny on 2017-10-16
There are several ways  you could do that.
If you really want launchers on the desktop I think you can copy the appropriate .desktop file from /usr/share/applications to the Desktop folder in your /home, but it is not something I have ever done, so that may not be correct, and I don't use unity/Ubuntu so can not test this right now.

Try it yourself; you can easily remove the .desktop file from Desktop if either it does not work or does not act as you want.

Alternatively you could create a new .desktop file for nautilus to open a folder in nautlus (files) which contains the launchers you want.
First create a folder in your home called launchers. then create a text file containing
```
[Desktop Entry]
Keywords=file-manager
Name=Launchers
Comment=File manager for launchers
Exec=nautilus /home/username/launchers/ %f
Icon=nautilus
Terminal=false
Type=Application
Categories=GTK;Utility;TextEditor;

```and save it in your home as launchers.desktop, then make it executable with ```
chmod +x launchers.desktop
```
Now when you double click that desktop file in your home it shouid open the launchers folder which you can populate with the launchers you want. You can now lock that new launcher icon to the launchbar to keep it there.

PS:
I have not tried any of this but can't see any reason for it not to work.

---

