---
title: "Simple Script"
date: 2006-09-14
forum: Programming Talk
---

### Post by tobaccoman on 2006-09-14
Hi!
I'm very new in LINUX and must say that I like it!

Could someone help me in creating a simple script.

I have an application that I start via the terminal by typing:

... cd/newbox
.... ./newbox

And a I need the the terminal to reamin open.

How can I launch the same via a shortcut on the desktop.

It's probably very simple, but as mentioned, I'm new in this...

Cheers!

Daniel

---

### Post by Tomosaur on 2006-09-14
All you need to do is right click on the desktop and click 'create launcher'. You then type the path to your program as the command.

---

### Post by X.Cyclop on 2006-09-14
Save this as "newbox.desktop" on your desktop:
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Newbox
GenericName=Game
Comment=This is a game...
Exec=sh ~/Desktop/newbox
Icon=icon.xpm
Terminal=false

```

Of course, change **Name**, **GenericName[/Be, [B]Comment** and **Exec**. ;)

Add your icon to **/usr/share/pixmaps** or type your icon's full path.

---

