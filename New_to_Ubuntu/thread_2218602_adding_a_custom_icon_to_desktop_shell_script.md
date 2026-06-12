---
title: "adding a custom icon to desktop shell script"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-04-21
i have a shell script on my desktop kill shutdown timer it is on the left hand corner. i want to add a custom icon. note i have also opened the the file properties and the gedit script.

here is screenshot

---

### Post by rburkartjo on 2014-04-21
note on file properties if i click on the icon i still cant change the icon. tks

---

### Post by Dennis N on 2014-04-21
Instead of saving the script to ~/Desktop, put it in ~/bin and then make a .desktop file for the script. Save the .desktop file to your ~/Desktop folder. In the .desktop file, you can specify a path to an icon you want.

Example: Here is a .desktop file to start a script (machinarium) located in ~/bin that in turn sets up and runs the game Machinarium:

```
[Desktop Entry]
Name=Machinarium
Comment=Start machinarium script
Exec=machinarium
Icon=/home/dmn/games/Machinarium/menu-icon-3a.png
Type=Application
```

I saved this file to my **~/Desktop** as **machinarium.desktop**

---

### Post by rburkartjo on 2014-04-21
dennis tks but this is how i did it. i put the script in my home folder than opened the main menu application and added a new launcher to the main menu-selecting whatever icon i wanted. then open the main menu right clicked and selected the add to desktop options. worked great.

---

