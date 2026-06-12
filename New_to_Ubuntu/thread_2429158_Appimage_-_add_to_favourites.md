---
title: "Appimage - add to favourites"
date: 2019-10-14
forum: New to Ubuntu
---

### Post by nibz-au on 2019-10-14
Hi all

Ive downloaded the programs krita, godot and lmms
these are all .zip files with an appimage i just click to run
how can i get these to stay on the dock?

i saw a thread that said i should get asked to add to file system but that doesnt happen
there is no option to right click and add to favourites for these

---

### Post by Dennis N on 2019-10-14
The AppImage needs to have a .desktop file in ~/.local/share/applications in order to show in the applications menu and activities overview search. Once you have started it from either of these locations, you should be able to pin it to the launcher. You may have to create the .desktop file yourself, and you may have to supply an icon. 

Some AppImages will create a .desktop file, in ~/.local/share/applications, but most don't. For example, Etcher made a .desktop file on first run by double-click. It also automatically provided the icon, so it was easy. Krita didn't do either, as I recall, so I made the .desktop file, and had to find an icon for it on google. You should use an .svg file for the icon.

For example, here is a .desktop file for Krita, (note: my location for all my appimages is ~/appimages):
```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=krita
Type=Application
Categories=Graphics;
Exec=/home/dmn/appimages/krita-4.2.5-x86_64.appimage %U
Name=Krita AppImage
GenericName=Graphics Design
StartupNotify=true

```
Save it as krita.desktop in ~/.local/share/applications

The Krita icon (krita.svg) was put in /usr/share/icons, which is a standard searched location.

---

### Post by nibz-au on 2019-10-15
Thank you very much, 

any idea why i cant get lmms on the favourites?.. this stilld oes not give me the options..

> 
[Desktop Entry]
Version=1.0
Type=Application
Name=Lmms
Comment=Music
Exec=/home/nibz/GameDev/lmms.AppImage
Icon=/home/nibz/Pictures/lmms.png
Categories=Music
Path=
Terminal=false
StartupNotify=false


---

### Post by Dennis N on 2019-10-15
> **nibz-au said:**
> Thank you very much, any idea why i cant get lmms on the favourites?.. this stilld oes not give me the options..
When choosing categories you are supposed to include one of the following main categories: AudioVideo, Audio, Video, Development, Education, Game, Graphics, Network, Office, Settings, Science, System, Utility. 

So use one of these words in your Categories at a minimum. You can have more than one Category. Categories are separated by semicolons (;) and also the list of categories ends in a semicolon.

'Music' is an 'Additional Category' so you should include one of the main categories with it, chosen from its 'Related Categories' column in the table linked below. That might help.

```
Categories=AudioVideo;Music;
``` 

See the Additional Categories and their Related Categories here:
[https://specifications.freedesktop.org/menu-spec/latest/apas02.html](https://specifications.freedesktop.org/menu-spec/latest/apas02.html)

---

