---
title: "localhost password"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by gregalynch on 2008-09-16
I'm very much a beginner, so I'm not sure what everything means, but when I open the printer manager (system->administration->printing) it immediately asks for the password of greg (the name of my computer)@localhost.  I don't remember ever establishing a password for this, and the password that I use for everything else doesn't work.  Is there some sort of default password that I need?  Or is there some way to find out what the password might be?  It won't let me make any changes to the printer settings without it.

Thanks

---

### Post by dwhitney67 on 2008-09-16
How many user accounts do you have on your system?

If you only have one ('greg'), then the passport you used to login is the password being requested by the Print Manager.

---

### Post by gregalynch on 2008-09-16
I am the only user on the computer, but the password that I use to login (and to perform administrative tasks) for some reason doesn't work in this situation.

---

### Post by Martje_001 on 2008-09-16
I have had that problem too once. If I'm not mistaking you can; or run it as root (with sudo) or create a root account and use the password (not recommended).

Edit: Yes, here it is:
> I'm using Xubuntu 6.10. I'm logged in as normal user. From "Applications" menu, I choose "Settings" and then from the submenu, I choose "Printing" (which, incidentally, has no icon).

Then a prompt says "Password required. Password for root on localhost?" Of course by default there is no root password, so nothing I type here works (including my own password) and all I can do is cancel.

If I set a root password, this works fine. If I open a terminal and type "sudo system-config-printer" this works fine. But when I choose it from the menu, it doesn't.

I believe the menu entry needs "gksudo" in front of it, but for the life of me I can't find where I edit the menu. It just seems to be included from some mysterious place. I don't see in my ~/.config/xfce4/desktop/menu.xml where this included menu comes from.

Can someone suggest a fix for this?

Thanks

---

### Post by gregalynch on 2008-09-17
running it as root does appear to work.  not a perfect fix, but good enough.  Thanks!

---

### Post by nowshining on 2008-09-17
did you try inserting your own password?? sudo by a one persons' account means that you are also an admin by default and ur pw should work to unclock anything needing sudo, so that means that you input the same pw as you do for your login password, alas when doing sudo by terminal ur pw won't show as you type...

---

### Post by el_baby on 2009-01-04
Solved this: Go to system => preferences => main menu

Here you are editing your menu options, in here, go to:
system -> administration -> printing
and press the PROPERTIES button.

In the "Command" box, replace:
system-config-printer
with:
gksu /usr/bin/system-config-printer

press "CLOSE" and that's it. Next time you go to system => administration => printing it will ask for your password (at that point) and then it WON'T ask for root password.

HTH

---

