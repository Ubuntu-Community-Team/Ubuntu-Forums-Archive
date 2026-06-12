---
title: "What are all the different GUI toolkits that can be used with python?"
date: 2007-03-18
forum: Programming Talk
---

### Post by user1397 on 2007-03-18
I am wondering what are all the different GUI toolkits that can be used with python to make GUI programs.  I know that gtk+ and qt can be used, but apart from that, if there are any more on linux or on any other OS, I do not know.

Does any one here know?

---

### Post by Mirrorball on 2007-03-18
[SIZE=-1]There are also Tkinter and wxPython.
[/SIZE]

---

### Post by pmasiar on 2007-03-18
[EasyGUI](http://www.ferg.org/easygui/) - archetypical Python solution: simple and quick GUI with no frills. No events, no problems :-)

With showmedo videos made by kids.

---

### Post by user1397 on 2007-03-19
all of the above are only for linux, right? 

are there any for windows?

---

### Post by dave091 on 2007-03-19
Here is a list of cross platform and platform specific gui toolkits available for python

[http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)

Tkinter and wxPython are definitely cross platform. I recommend wxPython only because it comes with SPE. :smile:

---

### Post by Mirrorball on 2007-03-19
> **ubuntuman001 said:**
> all of the above are only for linux, right?
No, they are all cross platform.

---

### Post by user1397 on 2007-03-19
ok, thank you guys for all the help.

---

### Post by user1397 on 2007-03-25
Just wondering, does anyone know what toolkit is used for the official bittorrent client?  Are different toolkits used for different platforms? i.e. windows, linux, etc.?

---

### Post by lnostdal on 2007-03-25
It seems wxPython is used on all platforms.

(wx uses GTK+ to render under Linux (edit: it seems to have support for plain X and Motif also; but I bet GTK+ is used in most cases), and the standard Win32 API under Windows)

---

### Post by user1397 on 2007-03-25
> **lnostdal said:**
> It seems wxPython is used on all platforms.

(wx uses GTK+ to render under Linux (edit: it seems to have support for plain X and Motif also; but I bet GTK+ is used in most cases), and the standard Win32 API under Windows)
ah, alright, thanks for the info

---

### Post by Mirrorball on 2007-03-25
> **Mirrorball said:**
> No, they are all cross platform.
.

---

