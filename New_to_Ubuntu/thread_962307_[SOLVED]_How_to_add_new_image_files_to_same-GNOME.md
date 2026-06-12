---
title: "[SOLVED] How to add new image files to same-GNOME?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by justchange on 2008-10-29
I've been getting to know Ubuntu for only a few days, with no prior experience with command line Linux.
I want to add my own image files to the included game same-GNOME, but I can't figure out how...
I know the location (/usr/share/gnome-games/same-gnome/themes/2.10), but
#1 I'm denied permission because the folder is owned by "root"
#2 I have NO clue what to do next.

I've tried creating a user "root", but that didn't fool the program at all... it told me that "root" wasn't allowed to use the GUI.

I opened a terminal window, but have absolutely no idea what to do with it... the commands nor syntax. (I have some minor experience with DOS command line... and I can cut & paste.)

Can anyone get me started... or point me in the right direction?

Thanks.

---

### Post by SunnyRabbiera on 2008-10-29
yeh by default the root account is disabled on Ubuntu, and to access the folder you need you need to enter administration mode.
Lucky for you even though you will have to use the command line for this, the command itself is easy enough to jot down"
gksudo nautilus

This will open nautilus your file manager in super user do mode (sudo stands for super user do, it allows root access without actually having a root account)
Also keep in mind its not a good idea to enable a root account.

---

### Post by dracayr on 2008-10-29
open a terminal and type ```
gksudo nautilus
```. you should now be able to exchange the images

dracayr

---

### Post by SunnyRabbiera on 2008-10-29
> **dracayr said:**
> open a terminal and type ```
gksudo nautilus
```. you should now be able to exchange the images

dracayr

Or just copy and paste the command, lucky the gnome terminal allows copy and paste options.

---

### Post by justchange on 2008-10-29
Worked like a charm!

Thanks to you both for the fast, friendly, helpful responses.

I'm lovin' this OS!
:)

BTW, I especially appreciate Sunny's detail... it really helps the learning process along. (Not that there's anything wrong with the immediately-helpful direct approach, dracayr.)

---

