---
title: "Execute part of a script only when ..."
date: 2015-08-16
forum: Programming Talk
---

### Post by vasa1 on 2015-08-16
I made a [small script]("http://ubuntuforums.org/showthread.php?t=2290887") that I want to use via a keyboard shortcut (Super+s) but I want *mousemove* to work only when the window in focus is LibreOffice Calc. How should I modify the script to that end?

```
#!/usr/bin/env bash

xdotool mousemove --sync 218 144 click 1
```

Edit: this is what I did:```
#!/usr/bin/env bash

# hint: use "xdotool getmouselocation" to get values

if 
    xdotool getwindowfocus getwindowname | grep -Eq "LibreOffice Calc$"
  then 
    xdotool mousemove --sync 218 144 click 1
#  else 
#    zenity --info --text="Oops"
fi 

```Is there a better way than "*xdotool getwindowfocus getwindowname | grep -Eq "LibreOffice Calc$"*"?

---

### Post by vasa1 on 2015-08-17
> **vasa1 said:**
> ... Is there a better way than "*xdotool getwindowfocus getwindowname | grep -Eq "LibreOffice Calc$"*"?
I'm using this now:```
#!/usr/bin/env bash

# hint: use "xdotool getmouselocation" to get values

xgg="$(xdotool getwindowfocus getwindowname)"

if [[ "$xgg" == *" - LibreOffice Calc" ]]
  then
    xdotool mousemove --sync 218 144 click 1
fi


```

---

### Post by Vaphell on 2015-08-17
you could use *getwindowpid *and use extracted pid to get process info with* ps*

```
$ pid=$(xdotool getwindowfocus getwindowpid)
$ proc=$(ps -p "$pid" -o args=)
$ echo "$proc"
gnome-terminal

```

---

