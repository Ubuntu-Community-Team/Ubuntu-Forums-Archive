---
title: "Matlab's icon instead of Android studio's icon is shown for android studio's project"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by alprobyte on 2013-07-09
Hello.
I'm have installed Matlab and Android Studio on Ubuntu 12.04.2. When I open Android project in Studio, Matlab's icon is shown for opened project instead of Android studio's icon in Unity side panel (note that android studio's icon is shown for several seconds at the beginning). But if I open main Android studio's window, icon is correct. Why?

The contents of matlab.desktop and android-studio.desktop files respectively:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=matlab -desktop
Name=MATLAB
Icon=matlab
Categories=Development;Math;Science
Comment=Scientific computing environment
```
and
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Android Studio
Icon=/usr/bin/android-studio/bin/idea.png
Exec="/usr/bin/android-studio/bin/studio.sh" %f
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=false
StartupNotify=true
StartupWMClass=jetbrains-android-studio
```

---

