---
title: "HOWTO: Quickly extract mp3's from music videos on Youtube and enqueue them in Amarok"
date: 2008-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by motin on 2008-09-23
This script allows you to quickly add Youtube music videos as mp3's to your Amarok playlist. It is a basically a wrapper around ffmpeg and a modified youtube-dl script, but is not required to run in a terminal window. 

It is written as bash scripts, and the packaging is my first attempt with debian packaging. Also no-one else has tried it yet so though it works for me, it may or may not work for you!

Install the attached packages in the following order: flv2mp3-zenity, youtubemusic, then press Alt + F2 and run "youtubemusic". 

A tip is to add it to a keyboard short cut - I have it on Ctrl + Shift + Alt + Y. I'll probably pop in a .desktop file in future versions - but for now I am all keen on hearing if these scripts even work for you! :)

Attached are also screen shots of how it all looks like during usage. All feedback is welcome!

---

### Post by thischarmingman on 2008-12-30
Many thanks for that, yours was the only script that worked for me!

---

### Post by etrejos on 2009-03-13
I could not open the file
 "could not be opened, because the associated helper application does not exist. Change the association in your preferences"
any tips?
thank you

---

### Post by mrowth on 2009-03-13
> **etrejos said:**
> I could not open the file
 "could not be opened, because the associated helper application does not exist. Change the association in your preferences"
any tips?

Yes. This might be a problem with Firefox' setup.

(Unfortunately you can't right-click and "save as" a forum attachment. Are you getting no choice at all as to what to do with the file? It just wants to open it with... GDebi, I presume?)

Open Firefox' "Edit" menu, pick "Preferences", click the "Applications" tab, find the entry "Software Package (application/x-debian-package)", and select it.

The right column should turn into a drop-down list. Open it, and change it to "Always ask". 

The next time you click on the attachment, you'll be given a choice: Open the file, or save it. If you save it, you can install it later from wherever you saved it to. A double-click in your filemanager should bring up the correct application.

Or open it, but before click on the drop-down list first next to the "Open with" and pick "Other...". Then "walk" the fileselector to /usr/bin and pick gdebi-gtk or gdebi-kde (whichever you have and prefer, gtk goes better with GNOME or Xfce). Then you can install .deb packages "from the web".

(You "should" actually be able to "teach" Firefox to use gdebi-gtk/-kde in the Preferences/Applications dialogue (mentioned above), but it doesn't seem to work right for me. Hm, well.)

---

### Post by binbash on 2009-03-14
Does this work with amarok2?

---

