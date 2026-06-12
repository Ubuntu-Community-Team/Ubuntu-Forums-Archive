---
title: "Creating Desktop entry to run script file"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-10-01
Lubuntu 14.04. I've created a shell script to run in a terminal which basically asks for keyboard input and does certain things depending on the response. It runs fine if I open a terminal and invoke the program name. I'm trying to create a desktop entry, which will open a terminal and run the program, without success.
This is the desktop entry:
```
[Desktop Entry]
Name=SaveRestore
Comment=Save or restore
Exec=$HOME/saveres.sh
Icon=$HOME/icon.jpg
Terminal=true
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Games
```
All this does is open a terminal and stop. I can of course just type in ./saveres.sh at the prompt and it works fine. How can I get it to continue and run saveres.sh?
Any help would be appreciated.

---

### Post by sudodus on 2014-10-01
Maybe the PATH variable is not available. Try with the hardcoded path, for example (if your user ud is wimpy, change it the the real user id)

```
Exec=/home/wimpy/saveres.sh
```

*Edit*: Maybe you should also have the following lines

```
Version=1.0
Path=/home/wimpy
```

---

### Post by wimpy2 on 2014-10-01
Thanks for the reply.
> **sudodus said:**
> Maybe the PATH variable is not available. Try with the hardcoded path, for example (if your user ud is wimpy, change it the the real user id)

```
Exec=/home/wimpy/saveres.sh
```
I tried that for both the exec and icon, but it made no difference.
> 
*Edit*: Maybe you should also have the following lines

```
Version=1.0
Path=/home/wimpy
```
Tried that too. Still no change.

---

### Post by mc4man on 2014-10-01
post your script. 
(- whether  alt+F2 works in lubuntu don't know but any script that works from the run dialog should also work from Exec= in a .desktop. If the script works from a terminal isn't a test in this case.
Better to use full path on an Exec= line (& in a run dialog command

---

### Post by sudodus on 2014-10-02
Did you make your desktop file executable:

```
chmod ugo+x SaveRestore.desktop
```

(Modify the file name in the command to what it really is in your computer)

---

### Post by wimpy2 on 2014-10-02
@sudodus Saveres.desktop is executable.
@mc4man Alt-F2 doesn't seem to do anything in Lubuntu 14.04
I'm only just starting to write scripts so this one is fairly simple
Script for saveres.sh
```

#!/bin/sh
read -p "Save or restore? (s/r)" response
if  [ "$response"  =  "s"  ];  then
    echo "Save"
    cp /home/wimpy/borst.sav /home/wimpy/borst/borst.sav
else
    echo "Restore"
    cp /home/wimpy/borst/borst.sav /home/wimpy/borst.sav
fi
exit 0 
```
PS Although Alt-F2 doesn't work, there is a Run option in the main menu. Entering /home/wimpy/saveres.sh in the resulting dialog box does nothing.

---

### Post by JKyleOKC on 2014-10-02
While I'm using xubuntu rather than lubuntu, I believe the desktop interpretation is the same in both systems. I find that to reliably invoke a script through a desktop file, I need to use "EXEC=xterm -e TheScriptFile" where "TheScriptFile" is replaced by the absolute path to the script itself. This also lets me assign a title for the title bar, or set the location and size of the resulting window, if I want, by using additional options to xterm placed before the "-e" which must always be the last one on the line. When I do this, I set "Terminal=false" because the "xterm" brings up the terminal itself.

It isn't always necessary to go this route, but I've found that it always works, while going the way you are using has tended to be a "sometimes" thing...

---

### Post by wimpy2 on 2014-10-02
> **JKyleOKC said:**
> While I'm using xubuntu rather than lubuntu, I believe the desktop interpretation is the same in both systems. I find that to reliably invoke a script through a desktop file, I need to use "EXEC=xterm -e TheScriptFile" where "TheScriptFile" is replaced by the absolute path to the script itself. This also lets me assign a title for the title bar, or set the location and size of the resulting window, if I want, by using additional options to xterm placed before the "-e" which must always be the last one on the line. When I do this, I set "Terminal=false" because the "xterm" brings up the terminal itself.

It isn't always necessary to go this route, but I've found that it always works, while going the way you are using has tended to be a "sometimes" thing...
Thanks for the reply.  I had  actually just solved my problem using what is essentially your solution, I wrote a little script, which I called **test**.
```

#!/bin/sh
xterm -e /home/wimpy/saveres.sh
```
I altered the desktop file to run **test** with the Terminal set to false. In order to allow xterm to stay open I added another line to saveres.sh (I didn't want to use -hold)
```

read -p "Exit? Press Enter" response2

```
Pressing Enter will move to the last line - exit 0.
The desktop entry now runs **test** just fine. I'll mark this as "Solved".

---

