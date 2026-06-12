---
title: "Brasero says:"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kramer65 on 2008-05-06
Once I added all the songs which I want to burn to brasero I click "Burn".

It then gives a pop-up box which says "Please wait: some tasks are not completed yet."

It says that for the pas 2 hours now and nothing seems to happen.

Does anybody know what's wrong?

---

### Post by kramer65 on 2008-05-06
Well well well.

This is the most useless post I've ever done. It suddenly started burning.. after two hours though, but still.

Anybody tips on speeding it up though?

---

### Post by mjitkop on 2008-05-06
Hi, kramer65.

What type of CD did you make? Data/audio? 2 hours is really a long time and even if it was uncompressing audio files to make an audio CD I doubt it would take this long. 

Maybe it had trouble the disc? 

I'm just thinking out loud. ;-)

---

### Post by kramer65 on 2008-05-06
Hmmmm, I tried it twice again now and it seems to be working fine now.. 
Maybe it was a strange freeze or something?

---

### Post by tpischke on 2008-10-02
I see this consistently when copying a folder of music into brasero using the 'Search Directory' feature.

Workaround is to restart Brasero, or copy files individually rather than use the search directory feature.

---

### Post by v1nsai on 2009-02-24
I'm also having this problem when I try to burn an audio disk.  I've added 15 tracks, let them all load and clicked burn, and like the OP i've been staring at the "Please wait: some tasks are not completed yet" box with the "progress" bar (kind of ironic when it's not making any progress).

Anyway, tried completely uninstalling in synaptic and reinstalled because nothing at all would happen when I clicked the burn button, after reinstallation I now have the tasks not completed yet error.  Anyone find a fix for this yet?

---

### Post by jvin248 on 2009-07-27
Same problem here.. select songs, press burn audio disk and throws the error 'some tasks not completed yet'.  I can close that box, but brasero itself will not close unless I start up terminal and use htop to sigterm it.
 
running Xubuntu 8.04.03 

I did an apt-get remove --purge and then installed again and the problem persists.

I may try again as the purge option didn't remove the /home preferences files - maybe something lurking there? ...


I extended google search and saw more suggestions for K3b .. I checked my system and I had most of KDE already there for a couple of other programs so installing K3b (and libk3b2-extracodecs) was only about 12MB of additional space.  You may not want to do this if you have a clean Gnome or GTK system and don't want to add the extra KDE overhead.  I also had a project I needed to get done so this works for now.

Brasero did make some cds but not consistently (never knew if it would work or not).
I'm still curious why Brasero hangs.

---

### Post by Arup on 2009-07-27
Go to edit>plugin and disable normalize.

---

