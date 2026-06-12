---
title: "[SOLVED] gnome teerminal"
date: 2009-01-11
forum: Programming Talk
---

### Post by Jackp90 on 2009-01-11
In some of the small programs that I have wrote I have the terminal open a new window to complete the remainder of the command in a new window with the following command:

gnome-terminal -x $1

The problem with this is that it closes the terminal when it is done completing the action.  This might not seem like a bad thing but its kinda annoying when you have an with the task at hand and cannot read the terminal output (ie installing a program with the apt-get function)

This is not that important of a thread but it would be nice if I could get this fixed.  

Thanks for any help

---

### Post by Jackp90 on 2009-01-11
Sorry about title I guess that it must have been that coffee :)

---

### Post by $USER on 2009-01-11
try this

gnome-terminal -x bash -c "$1; read -n1"

that will wait till you hit enter before closing the window

---

### Post by Jackp90 on 2009-01-11
That worked like a charm thank you

---

