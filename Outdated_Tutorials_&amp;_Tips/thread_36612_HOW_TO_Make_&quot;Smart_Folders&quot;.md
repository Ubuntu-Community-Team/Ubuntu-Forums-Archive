---
title: "HOW TO: Make &quot;Smart Folders&quot;"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by JimmyJazz on 2005-05-24
Smart Folders automatically search for a term and display its results, great for your music collection.
I always liked the smart folder feature on iTunes and I noticed OS X Tiger added this feature to the entire OS so I decided to try to add this feature to GNOME and this is what I have come up with so far.
Open GEDIT and enter...
> 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
         Exec=gnome-search-tool --named=<**search term**> --start
TryExec=
Icon=
X-GNOME-DocPath=
Terminal=false
Name[en]=faithless
GenericName[en]=
Comment[en]=
 then save it as *.desktop (replace * with whatever you want) and place it on your desk top.  Their you have it just double click on it and it will automatically search for the term and display it.  Your serach term can be part of a file name or a filetype can be entered using *.filetype (i.e. --named=*.mp3)

There may be a better way to do this but I'm not aware of it yet, it would be cool to see something like this fully developed into GNOME.

---

### Post by Sionide on 2005-05-24
Interesting, little bit easier than firing up a terminal and using the *find* command.

---

### Post by N'Jal on 2005-05-24
Can you explain to me what these SMART folders do? Since trying this script i figure i might as well just use gnome search. I will be interested to see how this works but as it stands it has no use for me.

---

### Post by jonbuys on 2009-03-19
I wish it were that simple.  If we could somehow integrate the folders with a tracker search that actually looks inside the files, this would be so much more useful.

---

### Post by kidux on 2009-03-19
Doesn't Gnome-Do do this? It has a plugin to search through your files and folders, just by typing the name of it.... or am I missing something?

EDIT: Crap! This thing is 4 years old! *sigh* Resurrecting the dead is a full time job, lol.

---

