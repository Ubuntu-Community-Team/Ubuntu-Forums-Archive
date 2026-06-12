---
title: "Desktop files just disappeared, still listed in browser."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by crackatoe on 2008-04-28
An odd thing happened today on bootup, all my desktop files disappeared. In the 'desktop' file browser, they are still there, but have completely gone invisible as far as being on the desktop. What gives?

---

### Post by amohanty on 2008-04-29
Maybe nautilus died?? In a terminal see if this outputs anything:

pgrep -o nautilus

If not simply type:

nautilus &

If there is a number maybe it crashed try:
killall nautilus && nautilus &

You may not need to the last part because I think gnome-session auto-restarts it.

hth
AM

---

### Post by Sjovan on 2008-04-29
Maby you should take a look in gconf-editor. Maby a box has been checked or something :)

---

### Post by billgoldberg on 2008-04-29
If you use a badly written conkyrc file the icons can go missing. 
*(you  have to be using conky)*

You never know.

---

### Post by crackatoe on 2008-04-29
> **amohanty said:**
> Maybe nautilus died?? In a terminal see if this outputs anything:

pgrep -o nautilus

If not simply type:

nautilus &

If there is a number maybe it crashed try:
killall nautilus && nautilus &

You may not need to the last part because I think gnome-session auto-restarts it.

hth
AM


Here's what happened:

administrator@PD:~$ pgrep -o nautilus
6105 
administrator@PD:~$ nautilus &
[1] 7060
administrator@PD:~$ killall nautilus && nautilus &
[2] 7066
[1]   Done                    nautilus
administrator@PD:~$ 

Rebooting....

---

### Post by crackatoe on 2008-04-29
That worked. Everything that went invisible is back. I'm not one to go poking around in a terminal window unless the instructions say I need to.  Thank you for your help!

---

### Post by community nerd on 2009-09-29
I have the same thing but i am running dolphin because i couldn't locate the icon for nautlius. Anyone help please.

---

