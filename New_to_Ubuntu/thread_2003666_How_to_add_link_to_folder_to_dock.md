---
title: "How to add link to folder to dock"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Natalie P on 2012-06-14
I've just started dual booting Ubuntu 12.04 on my machine alongside Windows 7. I have a separate partition for most of my documents, music, etc. that I can reach from within both operating systems.

In Ubuntu, I can access it by clicking "Home Folder" in the dash then "File System" in the lefthand pane then there's a bunch of folders, one of which is called "shared". I think I named it that with a mount point, but it's its own separate logical partition. In Windows 7 that folder just shows up as the "D:" drive.

I just want to have quick access to this folder from the dash since it is where I'll be storing most of my data from either OS. **How can I put that folder on my dash (instead of the Home Folder)?**

---

### Post by black veils on 2012-06-15
maybe by creating a .desktop file, putting it in```
 /home/username/.local/share/applications
``` this will be another menu/app entry, so you can add it like any other launcher.


the file should be named what you want the launcher/app to be called, example: Music for the music folder. then give it the extension ```
.desktop
```the contents should be something like this (but you need to tweak the path and name, maybe even icon)
```
[Desktop Entry]
Name=directory you want
Exec=nautilus /home/username/the/directory/you/want
Icon=system-file-manager
Terminal=false
Type=Application
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;

```but hey, maybe there is another way to add a specific directory to the launcher.

---

### Post by Natalie P on 2012-06-19
Thanks so much, that was exactly what I needed.

---

### Post by Dngrsone on 2012-06-19
You can also add it as a right-click option to the Home folder launcher: go [here](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available) and look at the first item on the list.

---

