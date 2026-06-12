---
title: "[SOLVED] this may seem stupid"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by vikasmk on 2008-07-08
look ,this may seem a really stupid question , but how do i stop the cursor blinking in the linux console ???? i remember there was an option in gutsy in the preferences but not there in Hardy. any one know how to ???

---

### Post by dodle on 2008-07-08
Give it some eye-drops :).

Sorry, I don't know.

---

### Post by kestrel1 on 2008-07-08
For some reason this has been removed in Hardy. You can stop it blinking if you go to System - Preferences - Keyboard & uncheck the box in there, but this affects all programs.
Aparantly this guy has a patch for this:
[http://www.jcornwall.me.uk/](http://www.jcornwall.me.uk/)
Scroll down the page to find it. Don't know if it works though.

---

### Post by kestrel1 on 2008-07-08
The above does work, but to install it is a different matter. on the blog, it just says to copy the file to /usr/bin/ but you need root access to do this. However, if you try:
```
sudo cp gnome-terminal /usr/bin/
```
You cannot do it, because you have the terminal open. To get around this, try the folowing:
Open a terminal & type:
```
konsole
```
This should open up the konsole, unless it is not installed in which case type:
```
sudo apt-get install konsole
```
Once you have a konsole window open, close the terminal, then type:
```
sudo cp gnome-terminal /usr/bin/
```
You need to be in the directory that the file 'gnome-terminal' is in ie Desktop, so cd to the correct folder or use the correct path where you saved the program.
Anyway, when you run the terminal from now on the cursor will not blink.

---

### Post by kestrel1 on 2008-07-08
There is another way to do this, I think:
```
gksudo nautilus
```
This will open a gui so you can copy the file that way. You will need to shutdown the terminal again, before the copy can take place.

---

### Post by vikasmk on 2008-07-09
i just turned off the blink in prefenrence> keyboard  . i had forgotten about it . thanks all of you ;)

---

