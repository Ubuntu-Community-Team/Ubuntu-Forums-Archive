---
title: "i need good web/text editor"
date: 2007-05-10
forum: Programming Talk
---

### Post by emsee on 2007-05-10
Hi all, I'm NOOB in linux
and i need an asp/text editor (kinda like gedit or SciTe or HTMLPad under windows )
what can you reccomend me?
I it to have ftp access (so i could access and work on the files directly from ftp withput coping them to my comp)

p.s. tried NVU and quanta and scite 
NVU have good ftp but it doesnt recognize ASP and messes the code
all others are great but without ftp

---

### Post by NilsE on 2007-05-10
Have you tried Screem HTML/XML editor.  It is in the menu applications/programming section but you may have to check it on in the menu editor.  I don't remember installing it so it could already be there.

---

### Post by johnnymac on 2007-05-10
I'm a fan of Bluefish but it's not a WYSIWYG editor...

---

### Post by qix on 2007-05-10
Vim

It's the one you wanna learn to edit in. It has ftp support.

---

### Post by emsee on 2007-05-10
tryed to install VIM from installation manager (the build in soft that installs progs automaticly)
it installs alright but then nothing happends, the launch icon wont appear in "programing"
directory does exist dough.
wasup?

---

### Post by emsee on 2007-05-10
bluefish is nice, but no integrted ftp support

---

### Post by RedSquirrel on 2007-05-11
> **emsee said:**
> tryed to install VIM from installation manager (the build in soft that installs progs automaticly)
it installs alright but then nothing happends, the launch icon wont appear in "programing"
directory does exist dough.
wasup?

I don't think vim appears in the menus. What you have likely installed is the command line editor. If you want a GUI interface to vim, try installing gvim (package: vim-gtk).

---

### Post by _Agrajag_ on 2007-05-11
I'm quite fond of Quanta Plus

---

### Post by Inc&#940;nus on 2007-05-12
> **emsee said:**
> Hi all, I'm NOOB in linux
and i need an asp/text editor (kinda like gedit or SciTe or HTMLPad under windows )
what can you reccomend me?
I it to have ftp access (so i could access and work on the files directly from ftp withput coping them to my comp)

p.s. tried NVU and quanta and scite 
NVU have good ftp but it doesnt recognize ASP and messes the code
all others are great but without ftp

I use Kate for editing web files in-situ. Both Kate and Quanta will transparently open and edit files over ssh, ftp, samba, USB mass storage and bluetooth obex to my sure and certain knowledge - I do this all the time with kate  - I also use my phone as carryable storage, and have been able to edit in situ over bluetooth and the USB cable using both (not that I enjoy using Quanta for anything except editing CSS, for which it's good).

Also, there's an ASP plugin for kate which offers syntax highlighting etc.

If you're really having issues getting either to work with network transparency, a swift use of knetattach should fix it.

Also, I don't use FTP for remote access generally, as fish is usually a better fit for me* - and I didn't look into what jiggery-pokery was making it happen, but last time I edited something in-place using Bluefish, it worked but didn't offer to write to the server until I closed the program.

That wasn't an ubuntu machine and I don't have bluefish available right now, but it's evidently possible.


type fish://user@sshhost:port/path/ into konqueror  - BEST THING SINCE SLICED BREAD ALERT :)

---

### Post by FuturePast on 2007-05-12
JEdit will do pretty much everything you might need.

---

### Post by JTorres176 on 2007-05-12
If you're used to SciTE in windows, there is a SciTE package in the add/remove programs list.  I'm personally a big fan of vim and bluefish, but that's just personal preference.

---

### Post by emsee on 2007-05-12
Jedit: tried, it wont start, downloaded and installed it, when i try to start it, it thinks alot and closes itself
Scite: wont open ftp, it asks me for an ftp password and then dies (like win95 :) :) )
quanta: couldnt find ftp support, looked all over, including help

but theirs a bright side to all this: 
1. i learned a lil more bout linux
2. I found another prog, that has everything needed, and is very nice
its called EDITPAD, have tried it on windos and found it very attractive, they have a linux version, and lots of plugins

---

