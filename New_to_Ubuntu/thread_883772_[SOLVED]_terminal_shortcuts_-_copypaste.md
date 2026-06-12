---
title: "[SOLVED] terminal shortcuts - copy/paste"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-08
In xterm, ctrl c, and ctrl v don't work.  I searched terminal shortcuts.  THey don't exist?  Isn't this something we use in a terminal?  any way to set it up?

---

### Post by Lod on 2008-08-08
Try CTRL-Insert for Ctrl-C and SHIFT-Insert for Ctrl-V

---

### Post by quantumstitch on 2008-08-08
Using a 3 button mouse, you can highlight and use the middle mouse button to paste.

---

### Post by pedro_orange on 2008-08-08
You can right click on terminal to paste stuff already on your clipboard.
You can also copy using this method.

---

### Post by drs305 on 2008-08-08
nevemind...

---

### Post by Ryadt on 2008-08-08
CTRL+SHIFT+V to paste.

---

### Post by sisco311 on 2008-08-08
> **drs305 said:**
> Another option, close to what you already do: CTRL-SHFT-V and CTRL-SHFT-C within the terminal.

> **Ryadt said:**
> CTRL+SHIFT+V to paste.

doesn't work in **xterm**

---

### Post by drs305 on 2008-08-08
> **sisco311 said:**
> doesn't work in **xterm**
xterm! You are correct sir! Deleted my previous post re gnome-terminal: CTRL-SHFT+C to copy, CTRL-SHFT-V to paste.

---

### Post by ellgor on 2008-08-08
Hi,

There probably is but I dont know enough programming to do it, anyway I was looking/testing terminals out for the very same reason and after trying quite a few have narrowed it down to 3. I can highly recommend Yakuake (dont be put off by the name) once seen and tried ,well, next is the good old Gnome-terminal and finally Rox-term, hope this is of help.

Regards, Ellgor.

---

### Post by adamogardner on 2008-08-08
> **ellgor said:**
> Hi,

There probably is but I dont know enough programming to do it, anyway I was looking/testing terminals out for the very same reason and after trying quite a few have narrowed it down to 3. I can highly recommend Yakuake (dont be put off by the name) once seen and tried ,well, next is the good old Gnome-terminal and finally Rox-term, hope this is of help.

Regards, Ellgor.

maybe I don't have xterm.  maybe I have gnome.  What comes with ubuntu?  how do I list my terminal?

---

### Post by sisco311 on 2008-08-08
> **adamogardner said:**
> maybe I don't have xterm.  maybe I have gnome.  What comes with ubuntu?  how do I list my terminal?
the default terminal in ubuntu is gnome-terminal
Ctrl+Shift+c (copy)
Ctrl+Shift+v (paste)
also works in fxce4-terminal

sorry drs305 :-\"

---

### Post by Capa Pinbacker on 2009-01-05
To change the default gnome-terminal copy/paste short cut keys (say to Ctrl-C and Ctrl-V, resp.), do the following:

1. press "alt+F2", and run "gconf-editor"
2. navigate to apps/gnome-terminal/keybindings
3. change copy to "<Ctrl>c"
4. change paste to "<Ctrl>v"

---

### Post by theacerguy on 2009-01-05
ctrl shift v or c works for me

---

### Post by tarps87 on 2009-01-05
> **adamogardner said:**
> In xterm, ctrl c, and ctrl v don't work.  I searched terminal shortcuts.  THey don't exist?  Isn't this something we use in a terminal?  any way to set it up?

ctrl + c does work it just doesn't do what you want :)
ctrl + c is used for killing the program currently running in the terminal
Try running gedit from the terminal (without a & after it) and then pressing  ctrl + c

Just thought it might be useful for you to know, the previous post have answered you original question

Edit: Just realised this is an old post

---

