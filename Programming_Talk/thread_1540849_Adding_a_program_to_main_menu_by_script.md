---
title: "Adding a program to main menu by script?"
date: 2010-07-28
forum: Programming Talk
---

### Post by hakermania on 2010-07-28
Wat do you ave to do If you want your own application appear in main menu e.g. in the Applications-->Internet ?
I have a make file for my app that can do this but I don't know how..

---

### Post by sisco311 on 2010-07-28
You have to create a .desktop file in ~/.local/share/applications/ or /usr/share/applications/

i.e. in bash:
```
cat << EOF >> ~/.local/share/applications/**name**.desktop
[Desktop Entry]
Version=1.0
Type=Application
Exec=**command**
Name=**name**
Comment=**whatever**
Icon=**path/to/icon**
Categories=*Application;Internet;Network;WebBrowser;*
EOF
```

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---

### Post by hakermania on 2010-07-28
very nice, thank you!

---

