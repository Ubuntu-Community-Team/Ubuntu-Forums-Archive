---
title: "Confused with software installation locations"
date: 2024-06-16
forum: New to Ubuntu
---

### Post by whocaresalltaken on 2024-06-16
Hi,

I installed josm via the software and updates. It complained about my java version being outdated even though I had installed the latest version via apt. It appeared the josm path was incorrect and I didnt know how to fix this. I then went ahead and installed josm via apt and everything works fine. However, I have to launch josm (installed with apt)  via the command line with java -jar which works fine.

However, when I launch the version from "show apps" its the older version with the java error. I want to to uninstall this older version but I have no idea how to. I want to keep the working one installed via apt and uninstall the one shown in "show apps" how do i do this ?

Its so confusing how apps install,  these two josm versions are obviously in different locations but I have no idea on determining where and why they install in there respective locations.
Where can i get a clear understanding what happens when software is installed with different methods ?

---

### Post by Holger_Gehrke on 2024-06-16
You might want to check whether the one installed through 'Software' is a snap. snaps are a newer package format that Canonical has developed and is pushing heavily. The packages live in '/var/lib/snapd/snaps' and contain a read-only compressed file system that get mounted to subdirectories of '/snap/'. Use the command 'snap list' to see the installed snaps. 'snap remove' with the name of the package will remove an installed snap.

Applications overview or start menus are generated from text files with the extension '.desktop' found in the 'applications' subdirectories of the directories listed in the environment variable 'XDG_DATA_DIRS'. The 'Name' line in the '.desktop'-files is used as a key of kinds to order the data read from these files. If two '.desktop'-files have the same 'Name'-line then one will overwrite the other when the menus are generated. In general the '.desktop'-file for a snap will be read later than the one in from a .deb-package and will overwrite it in the menu. So removing the snap should automatically make the menu item for the .deb-package appear.

Both the snap and the .deb package are somewhat out of date. Openstreetmap operates their own repository for current versions of josm. See [https://josm.openstreetmap.de/wiki/Download#Ubuntu](https://josm.openstreetmap.de/wiki/Download#Ubuntu) for details.

Holger

---

### Post by whocaresalltaken on 2024-06-16
Thank you for the explanation.

---

