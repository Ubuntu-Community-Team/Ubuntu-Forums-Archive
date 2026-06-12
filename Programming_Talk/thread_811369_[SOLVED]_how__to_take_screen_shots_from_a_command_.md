---
title: "[SOLVED] how  to take screen shots from a command promt"
date: 2008-05-29
forum: Programming Talk
---

### Post by brijith on 2008-05-29
Hai 

what is the command to take the screen shot. What I mean is, I could take the screen shot by entering a command in terminal..

***[COLOR="Red"]Thanks[/COLOR]***

---

### Post by dtmilano on 2008-05-29
Try 'import' from ImageMagick.

---

### Post by vishzilla on 2008-05-29
you would need to install package scrot. Search in Synaptic
[https://help.ubuntu.com/community/scrot](https://help.ubuntu.com/community/scrot)

---

### Post by Kevbert on 2008-05-29
If you're running Ubuntu (at least 7.10 and above, anyway) you already have the means to take a screenshot.  Just go to Applications - Accessories - Take Screenshot.

---

### Post by Perfect Storm on 2008-05-29
On gnome you can do this;

```
gnome-screenshot -b -e --delay=3
```


```
[size=1]orion@orion:~$ gnome-screenshot --help
Usage:
  gnome-screenshot [OPTION...] Take a picture of the screen

Help Options:
  -?, --help                     Show help options
  --help-all                     Show all help options
  --help-gtk                     Show GTK+ Options
  --help-bonobo-activation       Show Bonobo Activation options
  --help-gnome                   Show GNOME options
  --help-gnome-session           Show session management options

Application Options:
  -w, --window                   Grab a window instead of the entire screen
  -b, --include-border           Include the window border with the screenshot
  -d, --delay=seconds            Take screenshot after specified delay [in seconds]
  -e, --border-effect=effect     Effect to add to the border (shadow, border or none)
  -i, --interactive              Interactively set options
  --display=DISPLAY              X display to use
[/size]
```

---

### Post by brijith on 2008-05-29
[COLOR="Red"]Thanks friends[/COLOR]

---

