---
title: "KIOEXEC: Malformed URL trash:/"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by PetePete on 2008-11-29
something has gone (been wrong with for quite a while) my dolphin.

Clicking on trash icon shows Malformed URL trash:/ error. Inserting a memory stick shows error

KIOEXEC
/media/disk IS A FOLDER, BUT A FILE WAS EXPECTED

I've done some research and reinstalled konqueror, dolphin, and apt-get install kubuntu-desktop

Think this all started happening when I installed kde 4.0 then removed it.



any ideas?

cheers

---

### Post by mrowth on 2008-12-27
> **PetePete said:**
> something has gone (been wrong with for quite a while) my dolphin.

Clicking on trash icon shows Malformed URL trash:/ error. Inserting a memory stick shows error

KIOEXEC
/media/disk IS A FOLDER, BUT A FILE WAS EXPECTED

I've done some research and reinstalled konqueror, dolphin, and apt-get install kubuntu-desktop

Think this all started happening when I installed kde 4.0 then removed it.



any ideas?

cheers

I have the same problem now. Although I'm not using Dolphin (just Konqueror).

Clicking **mounted** media icons (on the desktop, in the panel...) to open them in a Konqueror window works. 
Manually typing "trash:/" into Konq's address bar works.
Executing "konqueror trash:/" from a terminal works.
I can also get at "special" folders through Konqueror's navigation sidebar.

But trying to open freshly inserted DVDs or memory cards (or the trash) the most *convenient* way, through desktop/panel icons, gets me above-mentioned KIOExec error.

What I did do yesterday was install ubuntu-desktop to check out GNOME again, then removed pulseaudio (but kept the rest of ubuntu-desktop). 

Kubuntu Hardy, fully updated. KDE 4 removed a long time ago.

Edit: Installed Dolphin. It works with Dolphin. But Dolphin has other issues (which I suspect may be features); I like Konqueror so much better.

---

### Post by mrowth on 2008-12-27
Here's a solution, inspired by [http://kubuntuforums.net/forums/index.php?topic=3091248.0](http://kubuntuforums.net/forums/index.php?topic=3091248.0) and some poking around.

Simple method (what now I imagine might work):

1. Edit the file "~/.local/share/applications/kde-kfmclient_dir.desktop".

2. Append "%u" to the "Exec[$e]=konqueror..." line. 

3. Done.

Putzy, clicky GUI method (what I actually did):

1. Bring up the application associations dialogue for an affected media type; either through a medium's properties dialogue, or by running, say, "keditfiletype media/dvdvideo". (It doesn't matter if you have a DVD inserted.)

2. In the list of applications associated with that filetype, select "Konqueror", then click the "Edit" button.

3. Switch to the 2nd-to-last tab ("Programm", in German) and add "%u" to the command line (this was missing from mine, it was just "konqueror --profile filemanagement").

4. Done. 

This fixed both the problem with trash:/ and the "KIOExec" errors.

I don't know about Dolphin, but the solution might look similar. 

Hope this helps.

---

### Post by PetePete on 2008-12-29
cheers. the GUI method worked fine for me (couldn't find the file for the command line)

---

