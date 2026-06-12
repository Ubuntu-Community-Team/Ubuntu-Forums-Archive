---
title: "Help making a launcher script"
date: 2008-10-27
forum: Programming Talk
---

### Post by b3n0 on 2008-10-27
Hey all, usual story... Noob. With in 2 weeks of using ubuntu I've managed to install wow. I'm kinda happy about that, I think its an achievement for me. Well It would be great to have a desktop shortcut. I tried making a launcher... no joy, it gives me an error along the lines of... 'blizzard requires this file to be in the wow folder'. So I did some research, and found out about scripts. Now correct me if I'm wrong as I only learnt about scripts 1 hour ago. I right click on the desktop > create document > empty file. I type...
```
#!/bin/sh
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine "c:\program files\world of warcraft\launcher.exe"
Icon=/home/concorde/Pictures/Icons/wow.png
Terminal=false
Type=Application
StartupNotify=false
```
I save that as a .sh file
Then in the terminal I type
```
chmod +x /home/concorde/Desktop/wow.sh
```
and that's as far as I get. I get and error in the terminal 'no such file or directory'. Any ideas?

I'm running Ubuntu 8.04 so gnome environment. I have a funny feeling I got this from a Kubuntu page. If so is anyone able to convert it?

---

### Post by JupiterV2 on 2008-10-27
This thread should probably be moved to the wine forum.

---

### Post by geirha on 2008-10-27
You are mixing scripts with launchers. Try saving this as ~/Desktop/wow.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine "c:\\program files\\world of warcraft\\launcher.exe"
Icon=/home/concorde/Pictures/Icons/wow.png
Terminal=false
Type=Application
StartupWMClass=Wine
StartupNotify=false
```
It does not need to be executable. Note that the backslashes need to be escaped (\\).

---

### Post by b3n0 on 2008-10-27
> **geirha said:**
> You are mixing scripts with launchers. Try saving this as ~/Desktop/wow.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine "c:\\program files\\world of warcraft\\launcher.exe"
Icon=/home/concorde/Pictures/Icons/wow.png
Terminal=false
Type=Application
StartupWMClass=Wine
StartupNotify=false
```
It does not need to be executable. Note that the backslashes need to be escaped (\\).

Hey just gave that a go and got 'Couldn't display "/home/concorde/Desktop/WOW.desktop". The location is not a folder.' 
The directory is copy pasted out of the address bar.

---

### Post by geirha on 2008-10-27
> **b3n0 said:**
> Hey just gave that a go and got 'Couldn't display "/home/concorde/Desktop/WOW.desktop". The location is not a folder.' 
The directory is copy pasted out of the address bar.

When do you get that error message exactly?

---

### Post by ad_267 on 2008-10-27
That's what you should be trying to save the file as. The
"/home/concorde/Desktop/" is the directory and "WOW.desktop" is the file name.

---

### Post by b3n0 on 2008-10-27
> **geirha said:**
> When do you get that error message exactly?

As soon as I double click it? To launch it right?

---

### Post by ad_267 on 2008-10-27
Ok try this:

Press Alt-F2 and run "gedit /home/concorde/Desktop/WOW.desktop"

Then in the text editor that opens paste in:
```
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine "c:\\program files\\world of warcraft\\launcher.exe"
Icon=/home/concorde/Pictures/Icons/wow.png
Terminal=false
Type=Application
StartupWMClass=Wine
StartupNotify=false
```

And save the file.

---

### Post by b3n0 on 2008-10-28
Hey thanks for you help. I just got home from work and found that the script that I made works, icon and all. So maybe it just needed a reset.
thanks again.

---

