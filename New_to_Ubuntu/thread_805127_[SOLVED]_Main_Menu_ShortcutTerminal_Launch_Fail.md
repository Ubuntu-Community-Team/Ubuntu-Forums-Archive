---
title: "[SOLVED] Main Menu Shortcut/Terminal Launch Fail"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by cheesypoof on 2008-05-23
Hi, I have been experiencing this problem for the past couple of days. My "Main Menu" shortcut which launches the command "alacarte" does not start the window. When I open a terminal and type "alacarte" or "sudo alacarte" I receive text such as this...

> ***@***:~$ sudo alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

FYI:
Release 8.04 (hardy)
Kernel Linux 2.6.24-17-generic
GNOME 2.22.1

Additionally, I have tried changing the ownership of the file alacarte to my user, but that did not fix it. Hopefully somebody can help me solve the problem. If you don't have a solution, hopefully someone can provide me with the "Keyboard Shortcuts" terminal command.

Thanks,
cheesypoof

---

### Post by spiderbatdad on 2008-05-23
Have you installed the program Timidity?

---

### Post by cheesypoof on 2008-05-23
I checked Synaptic and Timidity was not installed. I think I remember doing something with that libasound file when I was trying to get my flash sound to work.

---

### Post by spiderbatdad on 2008-05-23
I was just fishing for an answer based on the error: undefined symbol: midiparser_input_buf

Timidity is a midi parser. Seems like the result of some sound program you have. Sorry I don't know more. Googling that error turns up several links: for example:[http://www.linuxquestions.org/questions/fedora-35/system-config-network-command-gives-an-exception-635557/](http://www.linuxquestions.org/questions/fedora-35/system-config-network-command-gives-an-exception-635557/)

---

### Post by jakob.g on 2008-06-06
hey,

i had the same problem and just managed to fix it by installing 

python 2.4 minimal
python 2.4 dev
python 2.4

hope this helps!

jakob

Edit:

If you're having trouble with permissions and alacarte will only run with sudo, try renaming/deleting ~/.config/menus/applications.menu

---

