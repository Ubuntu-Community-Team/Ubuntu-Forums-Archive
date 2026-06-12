---
title: "Can't add some programs to favourites in Ubuntu 22.04"
date: 2022-06-07
forum: New to Ubuntu
---

### Post by hakelm on 2022-06-07
I can't add some Desktop Entries  to favourites in Ubuntu 22.04, The desktop files do, however, work if I click on them in /usr/share/applications.
Please find some examples of two desktop files that can't be attached to favourites and one that does work.
What haven't I understood?
H

**Commercial Microchip application, can't be attached:**

[Desktop Entry]
Name=MPLAB IDE
Comment=IDE for Microchip PIC and dsPIC development
Exec=/usr/bin/mplab_ide
Icon=mplab_ide.png
Terminal=false
Type=Application
Categories=Application;Development;Programming;
StartupNotify=true

**Homebrewed application, can't be attached:**

[Desktop Entry]
Version=1.0
Type=Application
Name=mysql2graf
Icon=/usr/share/icons/mysql2graf.ico
Path=/dok/ny/p/hep/test/mysql2graf
Exec=/dok/ny/p/hep/test/mysql2graf/mysql2graf
StartupNotify=false
StartupWMClass=mysql2graf
OnlyShowIn=Unity;
X-UnityGenerated=true
X-Desktop-File-Install-Version=0.24


**Homebrewed application, can be attached:**

[Desktop Entry]
Version=1.0
Name=Sus
Comment=pm-suspend
Exec=/home/he/hep/scripts/susa
Icon=/usr/share/icons/Humanity/apps/32/access.svg
Terminal=false
Type=Application
Categories=Utility;Development;

---

### Post by #&amp;thj^% on 2022-06-07
see this, may help you: [https://askubuntu.com/questions/1378642/application-in-the-dock-cant-be-added-to-favourites](https://askubuntu.com/questions/1378642/application-in-the-dock-cant-be-added-to-favourites)

---

### Post by GhX6GZMB on 2022-06-07
Your Categories are wrong/missing. These are extremely important, as they are the basis for the desktop when building the Favorites menu during login.
Only certain standardized ones are permitted, you can't just define your own. Here's a list:
[https://specifications.freedesktop.org/menu-spec/latest/apa.html](https://specifications.freedesktop.org/menu-spec/latest/apa.html)

---

### Post by hakelm on 2022-06-08
Thanks, 
but it doesn't seem to help, neither adding a StartupWMClass, Categories or both.
Many of the working desktop files I have miss either one or both of  StartupWMClass and Categories.
What can I do?
H

---

### Post by hakelm on 2022-06-08
I found  desktop-file-utils, and run:

desktop-file-validate mysql2graf.desktop
desktop-file-install mysql2graf.desktop
update-desktop-database

none of which produced any output, nor improved it the desktop file behaviour.
H

---

### Post by GhX6GZMB on 2022-06-08
I've changed/added your "Categories=" lines as marked in red. Note that a "Main" catagory must _always_ be included as in the link I posted.
```
[COLOR=#000000][Desktop Entry][/COLOR]
[COLOR=#000000]Name=MPLAB IDE[/COLOR]
[COLOR=#000000]Comment=IDE for Microchip PIC and dsPIC development[/COLOR]
[COLOR=#000000]Exec=/usr/bin/mplab_ide[/COLOR]
[COLOR=#000000]Icon=mplab_ide.png[/COLOR]
[COLOR=#000000]Terminal=false[/COLOR]
[COLOR=#000000]Type=Application[/COLOR]
[COLOR=#ff0000]Categories=Development;Science;Electronics[/COLOR]
[COLOR=#000000]StartupNotify=true[/COLOR]
```
[B]Homebrewed application, can't be attached:
[/B]```
[Desktop Entry]
Version=1.0
Type=Application
Name=mysql2graf
Icon=/usr/share/icons/mysql2graf.ico
Path=/dok/ny/p/hep/test/mysql2graf
Exec=/dok/ny/p/hep/test/mysql2graf/mysql2graf
StartupNotify=false
StartupWMClass=mysql2graf
OnlyShowIn=Unity;
X-UnityGenerated=true
X-Desktop-File-Install-Version=0.24
[COLOR=#ff0000]Catagories=Utility[/COLOR]
```[B]
[B]Homebrewed application, can be attached:
[/B][/B]```
[Desktop Entry]
Version=1.0
Name=Sus
Comment=pm-suspend
Exec=/home/he/hep/scripts/susa
Icon=/usr/share/icons/Humanity/apps/32/access.svg
Terminal=false
Type=Application
Categories=Utility;Development
```

That ought to work.
If you still have issues, check the permissions of the .desktop files.
The ones in /usr/share/applications should have: root:root -rw- r-- r--
in $ROOT/.local/share/applications should have: *user*:*user* -rw- r-- ---

---

