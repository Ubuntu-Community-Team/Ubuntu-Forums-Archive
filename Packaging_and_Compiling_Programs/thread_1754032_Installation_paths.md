---
title: "Installation paths"
date: 2011-05-09
forum: Packaging and Compiling Programs
---

### Post by jackantares on 2011-05-09
Hello!

I'm developing a game for Ubuntu, but i don't know where are the better places to put some files of the game in the installation.

- The executable file (would be in /usr/bin?)
- The application data (images, music, sound, ...)
- How do I create an entry in the application menu, linking to the binary file?

Thanks in advance!

---

### Post by AlphaLexman on 2011-05-09
Take a look at some standards:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by jackantares on 2011-05-09
Very useful! Thanks a lot!!
This solves my problem of place the binaries and data, but how do I add an entry manually in the Application menu?

---

### Post by cipherboy_loc on 2011-05-09
This is a fairly simple [example]("http://drbrainiac.wordpress.com/2007/11/04/how-to-create-custom-desktop-launchers-in-ubuntu-gnome/"), but on installation, you can copy that file to /usr/share/applications, where all the .desktop files are stored. Also look at those files for more information on customizing them.

Edit: This might help a bit more.
[http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en](http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en)

Cipherboy

---

### Post by jackantares on 2011-05-09
Thanks! This helps a lot! Is almost all I need.
I took a look at a .desktop file, of the aqualung app:

[Desktop Entry]
Name=Aqualung
Comment=Gapless audio player
Exec=aqualung
Icon=aqualung.xpm
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application
Encoding=UTF-8

There is a reference to an icon aqualung.xpm, but where are this icon? There is a default icon directory?

---

### Post by AlphaLexman on 2011-05-09
> **jackantares said:**
> There is a reference to an icon aqualung.xpm, but where are this icon? There is a default icon directory?
Usually program icons are 'theme-able' so that a user could change his / her firefox icon to match a theme. I am not a theme designer, but do enjoy a nice continuity to my desktop.

For a nice start, look in:
```
/usr/share/icons
```

---

### Post by jackantares on 2011-05-09
Thanks!

I have used the search tool and found that the icons are in this directory. Problem solved!

Grateful for the help!

---

### Post by jackantares on 2011-05-09
Now I've created a .desktop file to my game, with:

[Desktop Entry]
Type=Application
Version=1.0.0
Encoding=UTF-8
Name=mygame
GenericName=...
Comment=Control a thief with your mouse and collect jewels
Icon=mygame.png
Exec=/usr/games/mygame/mygame
Terminal=false
StartupNotify=false
Categories=Application;Game;ArcadeGame

In the /usr/games directory I have created a directory called "mygame", where is the executable called "mygame" and a directory called "content", with game resources.
But, when I open the executable by the app menu, it doesn't works. The game window open, but I think the game break cause it can't find the resource directory. If I  open directly by clicking on the executable itself, it works. The same  problem occurs when I create a launcher with the command  /usr/games/mygame/mygame. There is something wrong with this path?

---

