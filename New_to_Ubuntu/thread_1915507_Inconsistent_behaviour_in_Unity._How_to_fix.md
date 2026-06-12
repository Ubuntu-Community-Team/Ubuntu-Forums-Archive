---
title: "Inconsistent behaviour in Unity. How to fix?"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by kramer65 on 2012-01-26
Hello,


I've been using Unity for a couple weeks now, and there's something which has been bothering me quite a lot. When I click a program icon on the left icon panel (or how do you call that thing?) it opens as expected. I often want to open another instance of the same program however. To achieve this I right-click on the icon and click "Open a new window" (or similar wordings). This option is however, not available with all programs. SQLiteman for example doesn't show this option.

Since I often need to use several windows of SQLiteman, this behaviour is very annoying. Is there a way to fix this so that the "Open-another-window-of-this-program" option is available with all programs?

---

### Post by Krytarik on 2012-01-26
> **kramer65 said:**
> Is there a way to fix this so that the "Open-another-window-of-this-program" option is available with all programs?
Nope, although you can add those Quicklist item to specific apps, of course, by modifying their respective .desktop files*, there is no universal fix for *all* apps, as this would mean all their respective .desktop files would have to be modified.

Regards.

* better copy the default one into your "~/.local/share/applications" and  modify that instead, this would override the default one; restart of Unity needed

---

### Post by kramer65 on 2012-01-26
Hmmm, that is unfortunate to hear. Unfortunately that is a bit too much hassle for me. I'll see how much it will annoy me in the future and see what I'll do then..  :(

Thanks a lot for the answer anyhow. I really appreciate:P it!

---

### Post by Krytarik on 2012-01-26
> **kramer65 said:**
> Unfortunately that is a bit too much hassle for me. I'll see how much it will annoy me in the future and see what I'll do then..  :(
To ease your pain at least in regard to SQLiteman, copy & paste this into the text editor and save it under the name "sqliteman.desktop" into "~/.local/share/applications" in your home directory (you may need to press Ctrl+H to see the hidden files/dirs), then relogin to make it take effect:

~/.local/share/applications/sqliteman.desktop:
```
[Desktop Entry]
Type=Application
Name=Sqliteman
GenericName=Sqlite admin tool
Comment=Administer and develop your Sqlite3 databases
Icon=sqliteman
Exec=sqliteman %f
Terminal=false
StartupNotify=true
MimeType=application/x-sqlite3;
Categories=Development;
**X-Ayatana-Desktop-Shortcuts=New**

# Translations
GenericName[cs]=Sqlite administrace

[B][New Shortcut Group]
Name=New Window
Exec=sqliteman
TargetEnvironment=Unity[/B]
```I've bold-marked the parts I've added, in case you want to try to apply it to other apps also. The default, system-wide .desktop files are stored in "/usr/share/applications".

Btw., you can always middle-click any app launcher in the Unity Launcher to open another instance of it (if you have a middle-click at your mouse, otherwise press the right and left mouse buttons simultaneously, or [emulate the middle-click]("http://www.tuxgarage.com/2011/06/emulate-middle-click-in-ubuntu.html")).

---

