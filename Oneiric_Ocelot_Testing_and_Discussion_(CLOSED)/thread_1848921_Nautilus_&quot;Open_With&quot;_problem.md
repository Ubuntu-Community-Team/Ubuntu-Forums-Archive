---
title: "Nautilus &quot;Open With&quot; problem"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by peyu on 2011-09-23
Hi,
I have truecrypt images putting them the tc extension, but nautilus can not detect the mime type. In nautilus 2.x, I used to double clic on it and at the first time, chose the option "use a personalized command" (translation from french interface, I don't know if it's the right phrase) and put 'truecrypt'. 
But now with nautilus 3.x, you can no longer put a personalized command, you can chose between already installed program or search online for others applications. 
Is there any way to set a personalized command to open certain file types ?

Any help would be greatly appreciated :-)

---

### Post by mc4man on 2011-09-23
When you used a 'custom command' previously it created a userapp  .desktop in ~/.local/share/applications
If you have access to that .desktop you could simply copy the contents into a new one you create in same location, named whatever you want - the .desktop name is not important - just keep it simple


Otherwise try (assumes that dir. exists
```
gedit ~/.local/share/applications/tcimage.desktop
```
A basic .desktop below
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=
Name=
Icon=
MimeType=
```
if you don't know the mimetype, (or what nautilus will 'see') then r. click on any of your .tc's > open with something from the list, doesn't matter if it fails.
Then look in ~/.local/share/applications/mimeapps.list - there will be an entry, use that type

As an ex. on lines filled in - this is named  mplayer2.desktop for use on playlists

> [Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=mplayer -playlist %U
Name=Mplayer List
Icon=apple-red
MimeType=audio/x-mpegurl;audio/x-scpls;


you could lose the Icon= line if desired or leave blank
The Name= line is the 'display' name - can be whatever you wish, doesn't need to be the name of the .desktop

---

### Post by jbicha on 2011-09-23
And ask whoever's packaging truecrypt to do the same so that it works in GNOME 3.

---

### Post by peyu on 2011-09-23
Thanks, I will try this. Unfortunately, there is no package for truecrypt because it's not considered open source..

It's a pitty that the old way to do it doesn't exist anymore...

---

