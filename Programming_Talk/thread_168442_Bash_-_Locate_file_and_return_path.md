---
title: "Bash - Locate file and return path"
date: 2006-04-30
forum: Programming Talk
---

### Post by ninocass on 2006-04-30
Ive had a look through the net and the man pages, is there a command that lets me search a directory for a file and return its path?

I recently got a virus that deleted a lot of my .exe's i want to write a script that will take in a txt file of filenames, search the XP CDRom and copy the files to folder to save me manually doing it

Cheers

Nino

---

### Post by LordHunter317 on 2006-04-30
If you got a virus that deleted system files on Windows, you can run 'sfc.exe' to restore files from the CDs, no work required.

---

### Post by T*&amp;1p87)v# on 2006-04-30
man find can give you a lot of info on the find command which is quite powerfull,

cd ~

find . -name "filename.extension"

 will search recursively starting from you home folder for the file filename.extension and return back the path

if you want the full path of the files the start searching from the root folder /

---

### Post by LordHunter317 on 2006-04-30
The files on the XP cd aren't named like the ones on the disk (because they're compressed) nor are they all on the disc directly (drivers and several other core files are in archives).  More importantly, if patched versions of files were installed, reinstalling directly from CD could ruin things.

The OP needs to use sfc.

---

### Post by ninocass on 2006-04-30
cheers for the info guys, ill give the SFC a whirll

i got the W32.polip visus [dont ask me how!] it managed to spread throughout my network [laptop + 2 Desktops] bar 1 terminal as it wasnt turned on.  It trashed a load of .exe like cmd.exe, calc.exe etc etc so i was manually searching the name on the  cd and copying/renaming it into the proper folders :S

---

