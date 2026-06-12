---
title: "Creating launcher shortcut"
date: 2013-01-16
forum: Repositories &amp; Backports
---

### Post by iain150 on 2013-01-16
I am trying to use [this ]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") to create a launcher icon for a script I have written that opens a group of files I commonly use for work, but when I tried the shortcut I got the following message "Details: Failed to execute child process "/usr/home/Documents/2D/2dscript.sh" (No such file or directory)".
You can see the files and permissions in the screenshot.
The script works when prompted in terminal.
I cannot think of what is wrong pls help thanks.

---

### Post by mc4man on 2013-01-19
Try (assuming blue is your user name
```
[Desktop Entry]
Version=1.0
Name=2D
Comment=Opens all my 2D pdf files.
Exec=/home/[COLOR="Blue"]iain[/COLOR]/Documents/2D/2dscript.sh
Icon=screensaver
Terminal=false
Type=Application
Categories=Utility;Application;
```

(- for scripts here I just create a bin folder in my home folder to place them in. Then the Exec= is just Exec=scriptname
(after a restart or sourcing .bashrc

You could also probably lose the .sh, both in scriptname & Exec=

---

