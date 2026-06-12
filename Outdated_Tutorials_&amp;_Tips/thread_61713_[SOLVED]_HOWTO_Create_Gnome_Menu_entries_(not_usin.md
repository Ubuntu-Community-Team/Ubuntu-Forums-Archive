---
title: "[SOLVED] HOWTO: Create Gnome Menu entries (not using smeg)"
date: 2005-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-09-01
**CAVEAT:** After u install a new app, u might think that the menu entry to that app is missing. Before u read any more, just log out and log back in. If the menu entry still isnt there, then follow this HowTo. Otherwise, u might overwrite the existing newly created menu entry or have duplicate entries.

**Part 1**
Well, I thought about writing this HowTo many months back but I somehow let it go. However, looking at the number of posts which say "wherez my menu entry? why is smeg crashing?", I have decided to write this one. This will be particularly useful to newbs and intermediate users.
Alright I dont use **smeg**. I will illustrate how I add a Gnome menu entry by giving an example. let us say I have downloaded the game called Nexuiz in my home folder and I want to make a menu entry. herez how I do it: 
```
sudo gedit /usr/share/applications/nexuiz.desktop
```
and then make the file which opens up look like this:
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/usr/bin/nexuiz
Icon=/home/arnie/Nexuiz/sources/darkplaces/darkplaces32x32.png
Terminal=false
Name=Nexuiz
Comment= First Person Shooter
Categories=Application;Game;
```

save this and close it. Now I have a neat menu entry under games in Gnome menu called "Nexuiz"
Now I will explain what I have done though most of it is self-explanatory.
1) u need to choose a filename (lets say "xyz.desktop") insteadof nexuiz.desktop depending on how u want to name the file. however, it will be at the same location (/usr/share/applications/)
2) Now about the entries in the file:
The first 3 lines will be the same for all applications ie.,
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
```
**Exec** will contain the path of the executable
**Icon** will contain the path of the icon u want to choose for the menu entry (try to make sure its a .png or .xpm file)
**Terminal** will have a value of ***true*** if u want to run the  application in a terminal window. Most GUI apps u would NOT want to run in terminal, so u can keep it as ***false***
**Name** and **Comment** are self explanatory
**Categories** is the crucial one.
here u CANT put in anything u want (u are restricted by certain keywords)
Make the first word **Application;** (**the semicolon is important**)
The second word can be one of the following depending on where u want your app to appear in the menu:
> GNOME MENU
Menu Entry  ---> second word that u have to put in category (**followed by semicolon**)
----------------------------------------------------------------------------------
Accessories --> Utility; 
Edutainment --> Education;
Games --> Game;
Graphics --> Graphics;
Internet --> Network;
Office --> Office;
Programming --> Development;
Sound & Video -->AudioVideo;
System Tools --> System;
Others --> Other;
Now u are all set.  save and exit. u will immediately have a new entry in your Gnome menu.

**Part 2**
there are certain apps that will not run till u execute them from the folder in which they reside (in other words u have to *cd* to that folder or open that folder in nautilus and execute it. These are generally binary files which u have downloaded and u run them directly without installing. Example: The game CUBE.
How do u add a menu entry in this case? If u add a menu entry just like u did in part 1, the app wont run because u are not running it from its folder. even creating a shortcut doesnt work.
In this case this is what u do:
u make a small script by doing: 
```
sudo gedit /usr/bin/cube.sh
```
which looks like this:
```
cd /home/arnie/cube/
./cube_unix

```
save and close. then, to make it executable, do a 
```
sudo chmod 755 /usr/bin/cube.sh
```
thats it! u are all set. Now point to this shell script in ur desktop menu entry. Thus for this case **Exec** in *xyz.desktop* will look like:
> Exec=/usr/bin/cube.sh

---

### Post by Maier on 2005-09-01
Nice howto, and good explaining :)

good work..

---

### Post by RaymondQE on 2005-09-01
Nice work.  Maybe you can add this to guide to the wiki.

---

### Post by Quirky on 2005-09-04
I couldn't get this to work for me in Hoary. I wanted to add a Nethack icon to the Games menu:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Icon=nethack.xpm
Name=Nethack
Comment=Adventure game
Exec=/usr/games/nethack-gnome
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=true
```

then```
killall gnome-panel
``` but it still didn't appear. I tried all sorts of order of the params, adding GNOME; to categories... but nothing seems to work.

Is there another file that perhaps reads in the .desktop files and that needs editting? Or perhaps the name is important? The file I used was ```
/usr/share/applications/nethack-gnome.desktop
```

---

### Post by arnieboy on 2005-09-04
[QUOTE=Quirky]I couldn't get this to work for me in Hoary. I wanted to add a Nethack icon to the Games menu:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Icon=nethack.xpm
Name=Nethack
Comment=Adventure game
Exec=/usr/games/nethack-gnome
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=true
```

then```
killall gnome-panel
``` but it still didn't appear. I tried all sorts of order of the params, adding GNOME; to categories... but nothing seems to work.

Is there another file that perhaps reads in the .desktop files and that needs editting? Or perhaps the name is important? The file I used was ```
/usr/share/applications/nethack-gnome.desktop
```[/QUOTE]

for **Icon** use the complete path. Are u sure the executable path is correct? Delete **Startupnotify=true**. Name and path of file is perfect. u dont have to kill gnome panel to make this work.

---

### Post by Buffalo Soldier on 2005-09-04
Thanks a lot arnieboy. I manage to get my TagTool entry working.

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/usr/bin/tagtool
Icon=/usr/share/pixmaps/TagTool.png
Terminal=false
Name=TagTool
Comment= MP3 and Ogg Vorbis tag editor
Categories=Application;AudioVideo;
```

---

### Post by Maier on 2005-09-04
quirky

are you even sure, you can use .xpm files for icons ?!

*****************
Icon=nethack.xpm
******************

try changing it to :nethack.xpm, to something else, another .png file perhaps ? :)

GL

---

### Post by arnieboy on 2005-09-04
[QUOTE=Maier]quirky

are you even sure, you can use .xpm files for icons ?!

*****************
Icon=nethack.xpm
******************

try changing it to :nethack.xpm, to something else, another .png file perhaps ? :)

GL[/QUOTE]
yes xpm file can be used for icons.

---

### Post by arnieboy on 2005-09-04
[QUOTE=Buffalo Soldier]Thanks a lot arnieboy. I manage to get my TagTool entry working.

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/usr/bin/tagtool
Icon=/usr/share/pixmaps/TagTool.png
Terminal=false
Name=TagTool
Comment= MP3 and Ogg Vorbis tag editor
Categories=Application;AudioVideo;
```[/QUOTE]
nice to know that; enjoy :)

---

### Post by Quirky on 2005-09-04
[QUOTE=arnieboy]for **Icon** use the complete path.[/QUOTE]

This fixed it. Oh man! What a gaff! I really can't believe I didn't try that, Thanks a bunch for the tip, I can clean up my Desktop 'shortcuts' now :)

EDIT: It actually WASN'T that. But editting and opening the menu without killing the panel allowed me to see the icon, clicking it gave me a permission error. No need to specify icon paths if its in /usr/share/pixmaps . So the problem was file permissions. chmod 644 fixed it.

---

### Post by arnieboy on 2005-09-04
[QUOTE=Quirky]This fixed it. Oh man! What a gaff! I really can't believe I didn't try that, Thanks a bunch for the tip, I can clean up my Desktop 'shortcuts' now :)[/QUOTE]
hey u are welcome :) enjoy :)

---

### Post by FLeiXiuS on 2005-09-04
There's actually been a little bug I've been trying to work out, perhaps you could take a look at it.  

My gedit icon has completely dissapeared one day out of the random.  Not sure why, I've been fiddling with smeg and manually editing the desktop files...

```

[Desktop Entry]
Encoding=UTF-8
Name=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=text-editor
Categories=Application;Utility;

```

---

### Post by arnieboy on 2005-09-04
[QUOTE=FLeiXiuS]There's actually been a little bug I've been trying to work out, perhaps you could take a look at it.  

My gedit icon has completely dissapeared one day out of the random.  Not sure why, I've been fiddling with smeg and manually editing the desktop files...

```

[Desktop Entry]
Encoding=UTF-8
Name=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=text-editor
Categories=Application;Utility;

```[/QUOTE]

Include the whole path for **Icon** and it will work just fine.

---

### Post by FLeiXiuS on 2005-09-04
I've tried that also and I've tried the full path for another icon.

---

### Post by arnieboy on 2005-09-04
[QUOTE=FLeiXiuS]I've tried that also and I've tried the full path for another icon.[/QUOTE]
change gedit %U to just gedit and check again
u mean to say, u can see the entry but cant see the icon in accessories? also check for duplicate .desktop entries for gedit in /usr/share/applications . also remove **startupnotify=true** and the mimetype entry

---

### Post by FLeiXiuS on 2005-09-04
Yeah thats another I've tried, I cannot view the entry at all...Searched through the load logs.  Nothing out of the ordinary.  Permissions are all correct.  Just something is happening..

---

### Post by arnieboy on 2005-09-04
[QUOTE=FLeiXiuS]Yeah thats another I've tried, I cannot view the entry at all...Searched through the load logs.  Nothing out of the ordinary.  Permissions are all correct.  Just something is happening..[/QUOTE]
ok try this:
```
rm -rf $HOME/.gnome/apps
```
and log out of gnome and log back in.
also make sure u have the whole **Icon** path.

---

### Post by FLeiXiuS on 2005-09-04
Tried it yesterday, but I will do so again.  MIME types were a bit screwy...

Yeah, still the same problem.

---

### Post by arnieboy on 2005-09-04
[QUOTE=FLeiXiuS]Tried it yesterday, but I will do so again.  MIME types were a bit screwy...

Yeah, still the same problem.[/QUOTE]
my final suggestion:
do a:
```
sudo updatedb
```
followed by:
```
slocate gedit.desktop
```
and remove all these files except the one in */usr/share/applications*
I think the one screwing it is in 
> $HOME/.local/share/applications

---

### Post by FLeiXiuS on 2005-09-04
OK, You've officially been given the GNOME sticker for today :-).

The problem was the duplicate ICON in [.local/share/applications/gedit.desktop] which was fault and did cause the problem.

---

### Post by arnieboy on 2005-09-04
[QUOTE=FLeiXiuS]OK, You've officially been given the GNOME sticker for today :-).

The problem was the duplicate ICON in [.local/share/applications/gedit.desktop] which was fault and did cause the problem.[/QUOTE]
heh enjoy :)

---

### Post by darehanl on 2005-09-09
Thanks for the awesome tip!

Just a note to other people: vim (maybe gedit does it too, I haven't checked) automatically filled in the .desktop entry. Quite nice.

---

