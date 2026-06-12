---
title: "Permissions within GNOME and gksudo"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Dev3383 on 2008-07-29
I, am as posting in this forum would indicate, a fairly new user to Ubuntu. 

i am in the process of transferring over from IIS to Apache2, thus from windows to Ubuntu. 

now i am normally the guy answering stupid questions so i looked around before i finally decided to ask for help (stupid geeky pride).

I need permissions for the file manager (nautilus, as i understand it), to copy some files from a remote share, into a directory i have created at /var/media. Everything i have found indicates i should be able to give nautilus permissions by going to the CLI (CTRL+ALT+F1-F6) and entering ```
gksudo nautilus
```. when i do this it responds with 
```
(gksudo:7623): Gtk-WARNING **: cannot open display:
```

Any help would be awesome.

---

### Post by InfinityCircuit on 2008-07-29
You want to use gksu nautilus from the X environment, not from the command line.  Go to X (Ctrl+Alt+F7) and then type Alt+F2 to get a Run box open.  Then gksudo nautilus should work.

---

### Post by ConMan318 on 2008-07-29
Gksdo is a graphical superuser mode, so in a command line mode you can't open it.  Since there is no graphical display, you are getting that error.  Hit Alt+F2 and type 'gksudo nautilus', or type it from the command line **in the gui** (meaning from a terminal).

---

### Post by Dev3383 on 2008-07-29
Thank you, i was unaware of the ALT+F2 Run app window. That should take care of me nicely. 

Thank you for the helpful replies

---

