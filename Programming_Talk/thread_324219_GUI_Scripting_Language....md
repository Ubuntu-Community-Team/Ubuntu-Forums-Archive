---
title: "GUI Scripting Language..."
date: 2006-12-23
forum: Programming Talk
---

### Post by electronpusher on 2006-12-23
I'm an amateur programmer new to Ubuntu Linux. I think I'm using the correct terminology. I use AutoIT to write GUI wrappers for my windows programs. As far as I know there is no Linux version of AutoIT. Is there anything similar for Linux. I'm not especially interested in all the GUI details and want something dead simple so I can concentrate on the actuall program. I do a lot of stuff in GNU C, G77 and FreeBASIC. I've been looking at TCL/TK and it looks pretty complicated. I need something DEAD simple for a GUI Moron! Thanks in advance for any help anyone can give me!

---

### Post by Hairy_Palms on 2006-12-23
you could have a look at zenity, it makes guis using bash (the language of the ubuntu terminal)
if you want gui basic programs you could always check out realbasic its free as long as you only want to compile for linux and has imo the best ide in linux

---

### Post by maddog39 on 2006-12-23
You can use Glade to script the actual GUI's and then in C/C++ import/parse the glade file with the gtk glade library of course then make a class to match the signal handlers defined in the glade.

---

