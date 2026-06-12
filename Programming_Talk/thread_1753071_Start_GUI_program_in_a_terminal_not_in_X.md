---
title: "Start GUI program in a terminal not in X"
date: 2011-05-08
forum: Programming Talk
---

### Post by hakermania on 2011-05-08
Hello :)

For example, if I go to Ctrl+Alt+F1 and give there
```
gedit
```
I get error message:
```
cannot open display
```
This means that it isn't connected to the X server, I assume...
So, how can I through a command line like this to execute a command that will open to the GUI environment at Ctrl+Alt+F7?

Thx in advance for any answers!

---

### Post by johnl on 2011-05-08
```

DISPLAY=:0 gedit

```

---

### Post by hakermania on 2011-05-09
Thank you!
Hmmm....I've actually made a server on my PC, and through a Web Page(using dyndns connected to my server) I can run commands on it from another PC connected to the internet from all around the world. The only drawback is that my PC has to be turned on. But when I run GUI commands I usually get:
cannot open display etc. errors....
Your solution works perfectly, but not in the php exec() function :/
There, I also get:
```
gedit  (gedit:17038): Gtk-WARNING **: cannot open display: :0
```

---

### Post by cgroza on 2011-05-09
> **hakermania said:**
> Thank you!
Hmmm....I've actually made a server on my PC, and through a Web Page(using dyndns connected to my server) I can run commands on it from another PC connected to the internet from all around the world. The only drawback is that my PC has to be turned on. But when I run GUI commands I usually get:
cannot open display etc. errors....
Your solution works perfectly, but not in the php exec() function :/
There, I also get:
```
gedit  (gedit:17038): Gtk-WARNING **: cannot open display: :0
```
SSH would be much more suited for this kind of task. And wih X forwarding you can have the application running on the server displayed on your computer.

---

### Post by hakermania on 2011-05-10
Thx for the suggestion, but I want to run commands from the other PC regardless its operating system and without having to install anything!

---

### Post by dwhitney67 on 2011-05-10
> **hakermania said:**
> Thx for the suggestion, but I want to run commands from the other PC regardless its operating system and without having to install anything!

Try turning off the computer to see if that works.

---

