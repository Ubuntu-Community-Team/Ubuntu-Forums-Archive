---
title: "newbie wants to run python"
date: 2006-05-07
forum: Programming Talk
---

### Post by minnew on 2006-05-07
I'm coming from the Windows world where I was playing around with Python...I installed Ubuntu and got it running OK, but I can't seem to launch Python??? Apparently the program exists on my hard drive, but double clicking on the "executable" does nothing??? What am I missing?

thanks

---

### Post by jrib on 2006-05-07
Hi, to get to the python interpreter, you can open a terminal ```
applications menu > accessories > terminal
``` and then type ```
python
```.

That should get you into the interpreter, did you want something else?

---

### Post by Wallakoala on 2006-05-07
In windows, you can just click on the python program to launch it. But with ubuntu, you have to go into the terminal (Applications -> Accesories -> Terminal) and do ```
python /path/to/yourpythonfile.py
```
and substitute /path/to/yourpythonfile.py for the path to your file.

---

### Post by minnew on 2006-05-07
thanks, but how does one know which programs run within the GUI (GNOME) and which ones don't?  And how would I run python within one of the IDEs available for it?   And, can I write a script that starts the Termnial then runs Python (or any other program)?

thanks, and excuse my ignorance

---

### Post by unbuntu on 2006-05-07
[QUOTE=minnew]thanks, but how does one know which programs run within the GUI (GNOME) and which ones don't?  
[/quote]
basically you can't tell, but most of the unix tools are console executables while GNOME apps **usually** have "gnome" or "g" before it, like "gnome-app-install" and "gedit".

> 
And how would I run python within one of the IDEs available for it?   

It depends on what IDE you use, and running it from IDE is pretty straight-forward.  I'm sure you'll find out how once you are in an IDE.

> 
And, can I write a script that starts the Termnial then runs Python (or any other program)?

thanks, and excuse my ignorance
Well, it's not much of a script but basically you can
```

#! /bin/bash
env python

```
make it executable ```
 chmod 0755 script.sh 
``` and make a link to wherever you find convenient.

Side note:  In KDE's Konsole, it allows you to create a python session right in the terminal program, which I think is pretty handy, but I don't think it will be implemented in GNOME's terminal anytime soon.

---

