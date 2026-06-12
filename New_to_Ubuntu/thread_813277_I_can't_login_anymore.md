---
title: "I can't login anymore"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by NotLikingIt on 2008-05-30
Well, at the joy of finally getting my stuff working
I played around some settings to make things look nicer

but yeah...something went wrong

i'm guessing it has to do the login window and some service at startup

right now, when I reboot my computer into ubuntu, and it loads Gnome. 

What appears is a window, not the login window, it would be an application trying to search local network...I'm guessing it's the remote login....

not surprisingly, it can't find anything, therefore I cannot login, how would I fix this?

Any help is greatly appreciated

Edit: Solved by editing /etc/gdm/gdm.conf-custom
under servers changed chooser to false

---

### Post by NotLikingIt on 2008-05-30
okay, I tried to go to the recovery mode
and type in gdm after log in as root under command line

the window popped up again

according to the help button, it's trying to find hosts on the local network with somethign called "XDMCP" enabled for me to log in

how do I disable this

---

### Post by timberspine on 2009-05-26
> Solved by editing /etc/gdm/gdm.conf-custom
under servers changed chooser to false

Thank you ... this helped! I did the same thing and I couldn't log on normally because of that pesky XDMCP login dialog box.

---

