---
title: "[SOLVED] how to edit process that load by default"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by macvr on 2008-08-15
hi, my laptop loads Bluetooth , evolution by default 
 i found them running in the system monitor process[attached pics]

i want to know how to remove evolution from process?

i want to know how to remove bluetooth from the processes?
     AND also turn it back on when i want to?

---

### Post by jualin on 2008-08-15
System, Preferences, Sessions should do the trick, which is similar to running "msconfig" on Windows. Good luck!

---

### Post by Pro-reason on 2008-08-15
Open the session manager.  You can do it from the preferences menu, or you can type "*gnome-session-properties*" at the command line.

---

### Post by jualin on 2008-08-15
> **Pro-reason said:**
> Open the session manager.  You can do it from the preferences menu, or you can type "*gnome-session-properties*" at the command line.

Thank you for the command line alternative. I didn't know that one. :)

---

### Post by macvr on 2008-08-15
ok i think i messed up the settings!!!!!!!!!

while i was editing the startup programs, i accidentally deleted the network manager!!!
where to i find it? to add it again?

---

### Post by jualin on 2008-08-15
> **macvr said:**
> ok i think i messed up the settings!!!!!!!!!

while i was editing the startup programs, i accidentally deleted the network manager!!!
where to i find it? to add it again?

You just need to add it again. Go to System, Preferences, Sessions, Add, and in write 
1> Network Manager for the name.
2> nm-applet --sm-disable for the command.

---

### Post by macvr on 2008-08-15
ok did that: worked fine,
what do i add to description?[i know not required , but wanted to return it to original state]

another silly question- why does it say disable?[i know it is as before but didnt understand y]

---

### Post by jualin on 2008-08-15
> **macvr said:**
> ok did that: worked fine,
what do i add to description?[i know not required , but wanted to return it to original state]

another silly question- why does it say disable?[i know it is as before but didnt understand y]

Originally the description was "Network Manager". I have no idea why the "disable" is there. I just gave you the command that I had on my computer, I tried running "nm-applet" from the terminal and it runs the same way, but I don't know if that will affect your machine in any way. Sorry for not being of more help, :(

---

### Post by macvr on 2008-08-15
thank you..

---

### Post by jualin on 2008-08-15
You are welcome!

---

