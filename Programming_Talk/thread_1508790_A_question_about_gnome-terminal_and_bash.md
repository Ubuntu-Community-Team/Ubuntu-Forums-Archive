---
title: "A question about gnome-terminal and bash"
date: 2010-06-13
forum: Programming Talk
---

### Post by adit on 2010-06-13
Suppose I type the following command
```
~$ gedit somefile.txt
```Which of the following things happen?
1) The gnome-terminal reads the command and calls gedit
2) The gnome-terminal reads the command and passes it to bash, then bash reads it and the bash calls gedit.

---

### Post by geirha on 2010-06-13
gnome-terminal passes the characters you type to bash's stdin. When bash recieves the newline, it parses the command line and runs gedit with somefile.txt as the first arg.

---

### Post by Bachstelze on 2010-06-13
Second one. gnome-terminal only acts as an interface between you and bash, it does not uns-derstand anything about the commands you type (when you press the "t" key, it just displays the "t" character, it does not try to make any sense out of it). If you do a [font=monospace]ps -ef[/font], you will see that the PPID of the gedit process is the PID of the bash process, which means that gedit was called by bash.

---

