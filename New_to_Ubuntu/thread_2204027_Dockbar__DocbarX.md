---
title: "Dockbar / DocbarX"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-02-06
I'm running Ubuntu 12.04 with Unity.
I was wondering if anyone else is running Dockbar.
It is a really nice little dock that supports Unity Quick Lists.

That brings me to my question.  Chromium's Quick List works fine from the dock, but I cannot get any other Quick Lists to work.
I've tried opening a program and pinning that program to the dock and I've tried dragging a .desktop file onto the dock.
Both methods allow me to add a program to the dock, but any corresponding Quick List is ignored.
The Quick Lists work fine from Unity's left-hand dock like thing (I can't remember what it is called).

In the DockbarX preferences I have checked the boxes that should enable support for Unity Quick Lists.

I would really appreciate any help.  This seems like a great program, it is lightweight and if the Quick List problem could be figured out, it would do exactly what I want.

[IMG]http://screencloud.net/img/screenshots/5ce81d1097e0b03054a1d22cbfd6a37f.png[/IMG]

---

### Post by stinkeye on 2014-02-06
Hi GrouchyGaijin,
I had a look at dockbarx a while ago and still had it installed so had another look.
It appears to me dockbarx only recognizes the old form of quicklists using **X-Ayatana-Desktop-Shortcuts=**
and not **Actions=**

eg my shutter.desktop shows a quicklist in dockbarx....
```
[Desktop Entry]
Version=1.0
Name=Shutter
Name[de_DE]=Shutter
Name[pt_BR]=Shutter
GenericName=Screenshot Tool
GenericName[de_DE]=Anwendung für Bildschirmfotos
GenericName[pt_BR]=Captura de tela
Comment=Capture, edit and share screenshots
Comment[de_DE]=Bildschirmfotos aufnehmen, bearbeiten und mit Anderen teilen
Comment[pt_BR]=Aplicativo avançado para capturar imagens da tela
Exec=shutter %F
Icon=shutter
Terminal=false
Type=Application
Categories=Utility;Application;
StartupNotify=true
MimeType=image/bmp;image/jpeg;image/gif;image/png;image/tiff;image/x-bmp;image/x-ico;image/x-png;image/x-pcx;image/x-tga;image/xpm;image/svg+xml;
[COLOR="#FF0000"]**X-Ayatana-Desktop-Shortcuts=**[/COLOR]Select;Screen;Window;Active;Delete-session

[[COLOR="#EE82EE"]**Select Shortcut Group**[/COLOR]]
Name=Capture an area of the screen
Exec=shutter --select
OnlyShowIn=Unity

[Screen Shortcut Group]
Name=Capture the entire screen
Exec=shutter --full
OnlyShowIn=Unity

[Window Shortcut Group]
Name=Select a window to capture
Exec=shutter --window
OnlyShowIn=Unity

[Active Shortcut Group]
Name=Capture the current active window
Exec=shutter --active
OnlyShowIn=Unity

[Delete-session Shortcut Group]
Name=Delete Session
Exec=rm /home/glen/.shutter/session.xml
OnlyShowIn=Unity


```

...but my custom gnote.desktop doesn't show a quicklist....
```

[Desktop Entry]
Name=Gnote
Comment=Take notes, link ideas, and stay organized
GenericName=Note-taker
Exec=gnote %u
Icon=gnote
MimeType=x-scheme-handler/note;
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;GTK;Utility;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnote
X-GNOME-Bugzilla-Component=main
X-GNOME-Bugzilla-Version=3.6.1
Name[en_AU]=gnote

[COLOR="#FF0000"]**Actions=**[/COLOR]new;scribbles;search

[[COLOR="#EE82EE"]**Desktop Action new**[/COLOR]]
Name=New Note
Exec=gnote --new-note
OnlyShowIn=Unity;

[Desktop Action scribbles]
Name=Scribbles
Exec=gnote --open-note Scribbles
OnlyShowIn=Unity;

[Desktop Action search]
Name=Search Selection
Exec=sh -c "gnote --search $(xsel)"
OnlyShowIn=Unity;

[Desktop Action addtoNotes]
Name=Add Selection to Notes
Exec=sh -c "echo $(xsel) >> /media/Data/Notes"
OnlyShowIn=Unity;
```
If I change my gnote.desktop to use the old [COLOR="#FF0000"]X-Ayatana-Desktop-Shortcuts[/COLOR] style the quicklist shows in dockbarx.
The unity launcher will show quicklists for both the old and new form.

---

### Post by Frogs Hair on 2014-02-06
I have used Dockbarx with XFCE, but not with Unity and there was a Zietgeist dock manager plug-in needed as well.

> dockbarx only recognizes the old form of quicklists using **X-Ayatana-Desktop-Shortcuts=**
and not **Actions=**

^ This

---

### Post by GrouchyGaijin on 2014-02-07
Good eye Stinkeye!  That did the trick.  Thank you!

---

