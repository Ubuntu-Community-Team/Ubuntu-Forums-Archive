---
title: "Could not locate terminal"
date: 2009-06-22
forum: Programming Talk
---

### Post by swappo1 on 2009-06-22
Hello,

I am getting an error message when I try and execute a program in Geany.
> 17:49:00: Could not find terminal "xterm" (check path for Terminal tool setting in Preferences)  I am not sure of the path to the terminal or where in preferences to put it.

---

### Post by Bodsda on 2009-06-22
> **swappo1 said:**
> Hello,

I am getting an error message when I try and execute a program in Geany.
  I am not sure of the path to the terminal or where in preferences to put it.

If you type the command```
which xterm
``` it will give you the path.

---

### Post by Mirge on 2009-06-22
Make sure you have xterm installed too, sudo apt-get install xterm should do it I believe.

---

### Post by swappo1 on 2009-06-22
Turns out it wasn't installed.  I take it xterm is not the same as terminal?  It is installed and working fine now.

---

### Post by jinksys on 2009-06-23
> **swappo1 said:**
> Turns out it wasn't installed.  I take it xterm is not the same as terminal?  It is installed and working fine now.

Xterm is *a* terminal, it's just one of many.  If you are using Ubuntu and are using Gnome, you are probably using Gnome Terminal.

---

### Post by damianday on 2011-09-19
For GNOME try this;
Go to Edit -> Preferences -> Tools -> 
Now in the Terminal edit box enter [COLOR="Red"]gnome-terminal[/COLOR]

---

