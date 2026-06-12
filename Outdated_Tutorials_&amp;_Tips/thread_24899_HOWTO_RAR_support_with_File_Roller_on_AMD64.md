---
title: "HOWTO: RAR support with File Roller on AMD64"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam on 2005-04-08
I've searched a little and didn't found anything about using File Roller with RAR archives on AMD64. The rar package required by File Roller in order to work is not available on AMD64 (correct me if I'm wrong; this howto would be useless). But it can be done with a little trick.


Install unrar-nonfree package:
$ sudo apt-get install unrar-nonfree

Make a symlink for unrar named rar:
$ cd /usr/bin/
$ sudo ln -s unrar rar


Hope this helps ! :wink:

---

### Post by dermotti on 2005-04-08
Will it unrar rar3.0 files?

---

### Post by Dracontopes on 2005-04-08
With the normal "rar" package it could not open a certain .rar file, but with this package it actually works! :) I don't know if that was a 3.0 package, but good chance it was.

---

### Post by bored2k on 2005-04-08
[http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/)

Search for rargui, its a GUI frontend.

---

### Post by Sam on 2005-04-08
[quote=dermotti]Will it unrar rar3.0 files?[/quote]
Yes the unrar-nonfree package handles rar 3.0 files.

[quote=bored2k]http://www.rarewares.org/debian/packages/unstable/

Search for rargui, its a GUI frontend.[/quote]
It was for avoiding installing an another application. But thank you for the suggestion !

---

### Post by bored2k on 2005-04-08
[QUOTE=Sam]Yes the unrar-nonfree package handles rar 3.0 files.


It was for avoiding installing an another application. But thank you for the suggestion ![/QUOTE]
 It is optional, you can't do anything with it unless you have those two files. 

I still prefer the old, rar e file.rar way:-D.

---

### Post by Chareos on 2005-05-20
Following these instructions file-roller no longer complains for unsupported file.

BUT... it opens and shows no files in archive. Even If I call ti to extract data from nautilus, if creates the foldername_FILES directory, but leaves it empty.

Note: of course archive is NOT empty and fully working ;-)


Any ideas ?

---

### Post by Sam on 2005-05-20
[QUOTE=Chareos]Following these instructions file-roller no longer complains for unsupported file.

BUT... it opens and shows no files in archive. Even If I call ti to extract data from nautilus, if creates the foldername_FILES directory, but leaves it empty.

Note: of course archive is NOT empty and fully working ;-)


Any ideas ?[/QUOTE]
Strange... I haven't used this often (I use the terminal to unrar my files), but everytime I did it worked. Anyway it's only a hack I found for a friend which prefers the gui.

---

### Post by Chareos on 2005-05-21
unrar works for me, that's just the file roller gui.
I'd really prefer to stick with a single gui, instead starting playing (and having problems) with rargui too...

---

