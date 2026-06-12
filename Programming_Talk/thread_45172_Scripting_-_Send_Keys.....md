---
title: "Scripting - Send Keys...."
date: 2005-06-29
forum: Programming Talk
---

### Post by grakker on 2005-06-29
Is there a way to have a script bash, python, whatever, interact with the X server, or do the different window managers make this not work?  What I would like to do is set up a keylaunch so that I can push cntrl-alt-p (or some other combination) and have do something like the following (very crappy psuedo code...)

if winactive "*Firefox" then
   $data = copy URL (or screen capture or close the program....)
   $hfile = fopen ("/something/file", append)
   write ($data, $hfile)
   $fclose($hfile)
fi


Or something along the lines of

If program is running
    copy something
    close running gui app
    open a different gui app
    wait for gui to open
    do something with new gui
    .... and so on
fi

or even simpler, someway to send a string to whatever is open.  In other words, send "This is lame" when I hit F8.  The string will enter in vim (if I'm in edit mode), or enter into oowriter, or ....

Is there anything like this.  I'm thinking of something like AutoIt3 for windows, but for linux.  I like using combinations of zenity + bash for doing stuff, but this doesn't really let me interact with other apps, it just gives the command line some candy.

Anyone?

---

### Post by ltmon on 2005-06-29
I think the thing you want to interact with will be the window manager rather than X itself.  I only know KDE, but kwin (the default KDE window manager) exposes a whole lot of functionality through DCOP, which can be called from many scripting languages and even remotely.

Maybe Gnomes WM (metacity?) can do something similar....

L.

---

### Post by cwaldbieser on 2005-06-29
Here are two simple scripts I wrote that interact with the KDE klipper application.  Since I switch between the the command line and the GUI a lot, it is sometimes convenient for me to pipe data to and from the klipboard.  I got the inspiration for this from a Windows utility called "winclip".

File "klipin"
```
#!/bin/bash
##################################################
# A simple shell script that works in conjunction with
# the KDE DCOP server to let you pipe text to the
# klipboard.
#
# example:
# 
# $cat file | klipin
#
##################################################

a=$(cat)
dcop klipper klipper setClipboardContents "$a"
```

file "klipout"
```
#!/usr/bin/python
#########################################################
# A simple python script that allows you to redirect the 
# klipboard contents as though it were standard output.
# 
# examples:
#
# klipout | grep xyzzy
# klipout > out.txt
#
#########################################################
# NOTE: Originally, I wrote this as a one-line shell
# script:
#
# dcop klipper klipper getClipboardContents
#
# , but the QString return value was coming back without
# embedded newlines, so piping the result to grep and 
# such was pretty much useless.  This python version of
# the script is almost as simple, but it does require 
# that the python-dcop package is installed.
#
#########################################################
import pydcop

if __name__ == "__main__":
   klipper = pydcop.DCOPObject("klipper", "klipper")
   print klipper.getClipboardContents()
```

This is really simple, but there a lot more impressive things you can do.  The kdcop utility lets you explore various KDE apps.  It is limited when working with non-KDE apps (e.g. Firefox), though.

---

