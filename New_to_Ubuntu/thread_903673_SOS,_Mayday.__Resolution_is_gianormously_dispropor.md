---
title: "SOS, Mayday.  Resolution is gianormously disproportionate!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-28
all I can say is what happened to my knowledge preceding the FAIL.
I made a new user account, the ctrl alt backspace to restart gnome and sign in as new user.  while there, I realized how badly I needed to set everything up like wirreless kppp aircard thing, and other personalizations, so I went back to my usual user account and compiz is GONE,  resolution is GONE, and hell even my kppp configuration is GONE, so I'm in windows partition asking for direction out of this mess.  I remember the last time i had to reinstall cause I couldn't get the right advice (or was too stupid to follow direction.  whatever the case, let's get my ubuntu back to normal.

addditionally, it's only offering two options for adjustment "some# x bad", or "some# x worse" at 61hz (sorry I can't remember the two poor resolutions).

---

### Post by alienexplorers on 2008-09-06
When your computer burped did you by chance loose the graphic driver for your card.  You could noot up and go to terminal and enter:
> sudo aptitude install envy-core
Once loaded run Applications -> System Tools -> EnvyNG.
Delete your older driver using envy if one is installed.
Do Not Reboot.
Load the new driver using automatic install.
reboot when done.
when back up and running and you still have the 640x480
or 800 x 600 resolution run:
> gksu displayconfig-gtk
select your monitor and graphic card.

---

