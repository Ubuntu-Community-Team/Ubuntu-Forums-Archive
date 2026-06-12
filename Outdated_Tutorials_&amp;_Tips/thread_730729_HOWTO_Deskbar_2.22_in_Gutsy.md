---
title: "HOWTO: Deskbar 2.22 in Gutsy"
date: 2008-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ElTimo on 2008-03-21
Ok, I recently got a PM from someone asking how to make the deskbar not suck. Here's what i told him:


1.) Crack open a terminal and type```
sudo apt-get build-dep deskbar-applet #thats a lot of hyphenation!
```This will pull in lots of packages (about 250 MB worth, IIRC) but go ahead unless you really can't spare the space.
2.) When that whole mess-o-packages finishes installing, get the deskbar 2.22.0 source from ["hnyah"]("http://ftp.acc.umu.se/pub/GNOME/sources/deskbar-applet/2.22/deskbar-applet-2.22.0.1.tar.bz2")  and unzip/unbzip/ungzip it to an easily-accessible directory. For the sake of sanity, let's pretend you unzipped it to ~/deskbar
3.) Type these commands in a terminal:```
cd ~/deskbar
``````
./configure --prefix=/usr
``````
sudo make install
```
4.) Log out and back in again to have deskbar switch to the newest version, then right click the icon and select "Preferences->General" and check the box next to "Stick to panel"
5.) This is the most important step.

ENJOY YOUR NEW DESKBAR!

(seriously, the whole thing won't work if you don't do this ;-))

Hope this helps someone

EDIT: ok i lied, it's only about 75 MB of packages :-P

---

### Post by bhavi on 2008-03-24
Thanks mate.. Tried it out just now.. After getting in 75MB of packages downloaded.. :P

---

### Post by quill3033 on 2008-06-15
Will this work in Ubuntu 8.04. I've finally erased my 6.06 and the only thing I miss is the old deskbar (2.14) which was great at finding files and launching programs alike. 
Now I am making do with an icon in the panel called "Search for files" (the one that has a pair of binoculars as an icon) and the orange deskbar. But I'm really missing the old deskbar.

---

