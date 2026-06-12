---
title: "Problem with .desktop file and icons"
date: 2007-09-21
forum: Programming Talk
---

### Post by mssever on 2007-09-21
I'm having trouble making a .desktop file display the correct icon, and I can't figure out why. I just get a generic blank icon.

My .desktop file includes the following line: ```
Icon=prog-name.png
```My installer contains the following:
```
for i in 16 22 24 32 36 48 64 72 96 128 192; do
  ln -s "${sharedir}images/logo_${i}.png" "/usr/share/icons/hicolor/${i}x${i}/apps/prog-name.png"
done
```What am I doing wrong?

---

### Post by deadlydeathcone on 2007-09-21
In the .desktop file, just use "prog-name" instead of "prog-name.png".

---

### Post by mssever on 2007-09-21
Didn't make any difference.

---

### Post by deadlydeathcone on 2007-09-21
Did you remember to update the icon cache afterwards?

```
sudo gtk-update-icon-cache /usr/share/icons/hicolor/
```

---

### Post by mssever on 2007-09-21
I didn't know to update the icon cache. However, it still doesn't work. I can't imagine what the problem is. Maybe I didn't show enough code? Here's my full .desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=Net Responsibility
GenericName=Internet accountability software
Comment=Configure Net Responsibility
Exec=sudo net-responsibility-config-cli
StartupNotify=false
Terminal=true
Type=Application
Icon=net-responsibility
Categories=System;Network
```And here's the full relevant installer code (which runs as root):
```
mv "${sharedir}net-responsibility.desktop" /usr/share/applications
for i in 16 22 24 32 36 48 64 72 96 128 192; do
  ln -s "${sharedir}images/logo_${i}.png" "/usr/share/icons/hicolor/${i}x${i}/apps/net-responsibility.png"
done
gtk-update-icon-cache /usr/share/icons/hicolor/
```



EDIT:I just changed the Icon line to /usr/share/icons/hicolor/36x36/apps/net-responsibility.png, which worked. But that's not workable since I have a simplified icon for the smaller sizes. Besides, it's supposed to look it up without a full path.

---

### Post by deadlydeathcone on 2007-09-21
Have you tried using the cp command instead of symlinks? The standard convention for icon themes is to never link an icon to something out of it's own directory, as then they can't be moved to another directory later on without breaking. You should probably follow suite, unless you're trying to keep the size of your install to a bare minimum - for all I know, gtk-cache-update might be set ignore icons linked in such a way.

Otherwise, your code looks fine - unless ${sharedir} isn't a full path or the destination doesn't exist it really should work. As for destinations - you might want to add this to the beginning of your for loop as a basic sanity check:

```
  if [ ! -e "/usr/share/icons/hicolor/${i}x${i}/apps/" ]
  then
 	 mkdir -p "/usr/share/icons/hicolor/${i}x${i}/apps/"
  fi
```

---

### Post by mssever on 2007-09-21
For testing purposes, I installed the icons in the Tango theme, which is the theme that I'm currently using. It worked, and gtk-update-icon-cache took some time to return--instead of returning immediately like with the hicolor theme.

According to the spec, isn't the system required to fall back to the hicolor theme? Is it just my system, or is there a bug here? And how can I work around this problem? Obviously, I have no guarantee that the user will be using the Tango icon theme.

---

### Post by deadlydeathcone on 2007-09-21
If the update exited instantly, the cache file is probably corrupt. This will generate a new one
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```
You should see "Cache file created successfully."

I'm hoping that's it, as hicolor is working for me on Gutsy, and worked on Feisty as well - otherwise it's likely a bug.

As for your question, it looks like hicolor does get inherited automatically. The chain of inheritance has always been Hicolor < Gnome < Tango & Tangerine < Human, yet on Gutsy nothing points to it at all and it works fine.

---

### Post by mssever on 2007-09-22
Apparently I have to use the -f switch in my install and uninstall scripts. Using it makes the icons show up, but I have to use it every time. Furthermore, I tried installing the program on my server (also running Feisty) and had identical issues.

The man page for gtk-update-icon-cache says that the -f switch forces an update even if the cache file is up to date. So for some reason g-u-i-c always thinks that the hicolor theme is up to date. Sounds like a bug for me. However, it's easy to work around. After all, I know it isn't up to date since I added files to it. So the -f switch doesn't hurt anything.

---

