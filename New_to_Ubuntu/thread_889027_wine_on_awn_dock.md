---
title: "wine on awn dock"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-08-13
How would i get a wine app on my awn dock.:confused::confused:

---

### Post by pikabuntu on 2008-08-13
> **SpenceMakesSense said:**
> How would i get a wine app on my awn dock.:confused::confused:
Ok, go to system > preferences > awn manager

then, click on launchers > add

now, put the name of the program in the box labled "name" and type in 
wine program_name in the box labeled "command"

---

### Post by SpenceMakesSense on 2008-08-13
Well I did

"wine utorrent"

And it doesnt launch. Am i getting the command wrong?

---

### Post by pikabuntu on 2008-08-13
did you restart the dock?

killall awn

then type awn to get it started again


Edit:
maybe this link will help?
[http://ge.ubuntuforums.com/showthread.php?t=769337](http://ge.ubuntuforums.com/showthread.php?t=769337)

---

### Post by lian1238 on 2008-08-14
Try typing the command in the terminal first. It's easier to see if it's working or not. For wine programs, usually you have to type the full path, not just "utorrent".

Is there a Wine menu in your main menu? If so, try dragging utorrent from there onto your dock. If not, Wine programs are install under "~/.wine/drive_c/". Type that into your file browser and find the .exe for utorrent. Now, the command to run would be "wine <fullpath_to_exe_file>".

---

### Post by SpenceMakesSense on 2008-08-14
> **lian1238 said:**
> Try typing the command in the terminal first. It's easier to see if it's working or not. For wine programs, usually you have to type the full path, not just "utorrent".

Is there a Wine menu in your main menu? If so, try dragging utorrent from there onto your dock. If not, Wine programs are install under "~/.wine/drive_c/". Type that into your file browser and find the .exe for utorrent. Now, the command to run would be "wine <fullpath_to_exe_file>".

Ya that worked. I had done that before but i must had done something wrong. I did notice thought when drag it to the terminal it says 

```
'/home/spence/.wine/drive_c/Program Files/uTorrent/uTorrent.exe' 
```

And when draggin into a program launcher command it says
```
file:///home/spence/.wine/drive_c/Program%20Files/uTorrent/uTorrent.exe

```

---

### Post by luckyuser on 2008-09-05
1)Go To: Applications>System>Preference>Main Menu
2)In the “Main Menu” window, hightlight a section  in the sidebar (ie Accessories, Games, Graphics, etc.)and click on the “New Item” button at the right of the window. 
3)In the “Create Launcher” window, type your application's name in the respective text box.
In the “Command:” text box, insert:

env WINEPREFIX="/home/YOUR_USERNAME_/.wine" wine "C:\PROG~FBU\APPLICATION_DIR\APPLICATION.E"

	Instead of  YOUR_USERNAME, type in your actual user name (I.e., mine is lucky.) 
Instead of APPLICATION_DIR\APPLICATION.E, fill out the rest of the folders up to your exe file.
(Mine looks like: env WINEPREFIX="/home/YOUR_USERNAME_/.wine" wine "C:\PROG~FBU\Concord\concord.e"

4)Click OK, and close the “Main Menu” window. 
5)Try out starting the launcher from where you created it in the Applications Menu
6)If it starts, drag and drop the icon from the menu to the AWN dock. If it does not start, let me know - 

This method is working very well for me, but I'd like to know if it is working for others. (And if there is a better method, sweet)

---

