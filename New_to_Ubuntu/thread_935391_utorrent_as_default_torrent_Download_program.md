---
title: "utorrent as default torrent Download program"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by azelez on 2008-10-01
Hi all, 

I come from a windows environment and I got used to the utorrent program.

I am running the utorrent program using the wine application but even as I mark the utorrent as default, it does not change the default torrent.

Does anybody have any idea how to change the utorrent as default torrent download application?

---

### Post by MrWES on 2008-10-01
I'm assuming you're leechin your torrent files from isohunt, etc., and using Firefox. Goto Edit | Preferences | Applications and set the desired application for bitorrnet see file to utorrent.

---

### Post by azelez on 2008-10-03
Thanks, 

I tried and it worked. I'll keep this in mind for other programs.
Anyway, I changed to deluge, and it did this automatically.

Adrian.

---

### Post by R.Bucky on 2008-10-03
I use KTorrent on Ubuntu. I prefer this app over others (yes, even utorrent) because of the easy to use interface and the IPblock plugin and others.

---

### Post by btmorex on 2009-01-04
It took me a while to figure out how to get file associations right with utorrent so I wrote a short guide:

[http://blog.shadypixel.com/fixing-utorrent-file-associations-in-linux/](http://blog.shadypixel.com/fixing-utorrent-file-associations-in-linux/)

If you follow those steps, utorrent will be the default .torrent app in gnome (i.e. firefox will offer to open a .torrent with utorrent and double-clicking a .torrent will automatically open utorrent).

Also, utorrent will appear in the gnome menus as just another app.

---

### Post by greylander on 2009-08-22
I followed btmorex' instructions several months ago and it worked for FireFox 3.0.13.

Unfortunately FireFox 3.5 does not list uTorrent as an option, even though FireFox 3.0.13 still recognizes it and has it as default.

Either FireFox 3.5 has failed to import something from 3.0.13, or it is failing to read the Gnome mimetypes in the same way.

I cannot remember if I had to do anything extra to make Firefox find the app or recognize it as a default.

One small thing I did have to do differently from btmorex' instructions was to edit (or create?) the file:  ~/.local/share/applications/mimeapps.list  instead of ~/.local/share/applications/defaults.list.  (maybe this has something to do with the version of ubuntu -- I'm currently using 9.04 and I believe I was running 8.1 when I first did this -- in both cases it was "mimeapps.list" not "defaults.list").

Anyone have any thoughts about what I need to do to make FireFox 3.5 see uTorrent as an app for bittorrent?

Thanks!

---

### Post by btmorex on 2009-08-23
Do you have the firefox-gnome-support package installed for 3.5? That may not be the exact name, but it something like that... I'm using Debian right now so I can't check.

firefox-gnome-support is what links gnome file associations with firefox download associations.

---

