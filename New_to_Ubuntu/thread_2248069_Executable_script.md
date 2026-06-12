---
title: "Executable script"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by marino4 on 2014-10-12
Ok so I whant to make a script that will run a simple shell command so i made a Script.sh file and edited it.

[Desktop Entry]
Type=Application
Name=Amnesia
Exec=cd '/home/(myusername)/test/test.sh' ; ./amnesia
Icon=utilities-terminal
Terminal=true
StartupNotify=false

How do i make it executable now i opened properties and checked Allow execution bu it just doesn't whant to work so how do i do it?

---

### Post by nerdtron on 2014-10-12
Does this line even work on the terminal? cd '/home/(myusername)/test/test.sh'

Is test.sh a folder?

---

### Post by sotiris2 on 2014-10-12
If amnesia also has execute permissions why not make the exec line simply ```
exec=/home/{myusername}/pathto/amnesia
```
I mean why try to change to the directory with cd and then give a relative path rather than simply give the absolute path and run one command? Also nerdtron is right is test.sh a directory?

---

### Post by Impavidus on 2014-10-12
This looks more like a .desktop file than like a shell script and indeed if you wish to start something by clicking on a kind of starter a .desktop file is what you need. The .desktop file doesn't need execute permissions, the program you execute of course does. More examples of .desktop files can be found in /usr/shate/applications.

As for the exec line, see sotiris2's comment.

---

