---
title: "HOWTO: Show window info by clicking on it"
date: 2011-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Eestlane on 2011-01-02
Assume you wanted to set root user a different theme than you have. You would have to open the appearance changer from root user (by running it with root privileges). The simple problem you might have, however, is not knowing the name of the application. This is where this snippet of code is useful.

The code for this shell script is following:
```
#!/bin/sh
TEXT_PROMPT="Click on the application you want to see information about."
echo "message:${TEXT_PROMPT}" | zenity --timeout 1 --notification --listen

tmpFile=$(mktemp)
xprop >${tmpFile}
winType=$(grep 'WINDOW_TYPE' ${tmpFile} |sed 's/^.*_\([^_]*\)$/\1/')
winClass=$(grep '^WM_CLASS' ${tmpFile} |cut -d\" -f4)
className=$(grep '^WM_CLASS' ${tmpFile} |cut -d\" -f2)
winTitle=$(grep '^WM_NAME(STRING)' ${tmpFile} |cut -d\" -f2)
owningProg=$(grep '^_NET_WM_PID(CARDINAL)' ${tmpFile} |sed 's/.*= //g' |\
   xargs ps -o comm= -p)
classRole=$(grep '^WM_WINDOW_ROLE(STRING)' ${tmpFile} |cut -d\" -f2)

rm -f ${tmpFile}

zenity --info --text="<b>Name:</b>\t${winClass}\n<b>Class:</b>\t${className}" --title="AppInfo"
```
Or here: [http://pastebin.com/g2zBjzeR](http://pastebin.com/g2zBjzeR)
[SIZE="1"](Most of the code is gathered from here: [http://forum.ubuntuusers.de/topic/transparenz-wird-nach-neuanmeldung-vergessen/#post-851627](http://forum.ubuntuusers.de/topic/transparenz-wird-nach-neuanmeldung-vergessen/#post-851627))[/SIZE]

Steps:
1) Make a new empty textfile in your home (or any subdirectory) with any name you want.
2) Copy and paste the code into that empty file.
3) Save the file.
4) Open your terminal and use command cd to go to the directory where your file is.
5) In the terminal use the command "chmod +x yourfile" (without quotes).
6) Now you can double click that file or open it in terminal (by using dot slash, e.g  "./yourfile" while being in the same directory)
7) You can also add a launcher to your panel. Right click on panel and select "Add to panel...", then select the first option "Custom Application Launcher". For the command select the yourfile.


Hope it's useful to anyone.

---

