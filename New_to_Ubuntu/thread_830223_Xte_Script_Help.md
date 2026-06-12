---
title: "Xte Script Help"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by The_Cavester on 2008-06-15
I need some help with Xte command in a script I wrote.
I'm using Hardy 32bit on a Portege M400
This script works fine::)
#!/bin/bash

/usr/bin/xte "key Return" &&
/usr/bin/gnome-osd-client "Pressed Enter"

But this script does not work, Why?:confused:
#!/bin/bash

/usr/bin/xte "key Up" &&
/usr/bin/gnome-osd-client "Pressed Up arrow"

The gnome-osd-client is working but the Up arrow key part is not.
I can run this script in a terminal and xte returns the key string
for the up arrow but this command is not making it's way to the window manager.
The first script is working just fine though, So what am I missing?

Can anybody help

---

### Post by The_Cavester on 2008-06-22
LOOK,  I've asked for help here for the second time and no one of you have anything to say!!!!

If it sounds like I am pissed......your right.

---

### Post by kerry_s on 2008-06-22
:lolflag:
if someone knew they would have helped you.
have you tried using the key number.

ps: you can get pissed all you want, no one here gets paid to do this, we're free to choose who to help, people with attitudes get less/no help.

---

