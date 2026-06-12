---
title: "Making a bleachbit like script with shred -vzfu"
date: 2016-01-14
forum: Programming Talk
---

### Post by adept-james on 2016-01-14
Hi I have recently realized that bleachbit doesn't seem to erase my files it errors always with firefox sqlite file. This got me interested in secure shredding files and I would like to make a script where I could say make an alias for sudo reboot --clean or sudo poweroff -c and have it wipe all of the files that i want it to. For example:  All firefox and chromium files all pidgin accounts and history  all putty files if any  all terminal history all virtual box history  All suggestions welcome I am researching this also i thought it would be prudent to put this to the community because it is filled with greatly experienced programmers and i am a relative beginner for instance i have never written a shell script. Thank you for your patience, James

---

### Post by Dreamer Fithp Apprentice on 2016-01-14
Some random points:
- you probably know, but just in case: This will STILL be insecure. All the shred/wipe type programs are essentially obsolete.  It is no longer possible to securely wipe files on modern hard drives consistently and with reasonable confidence, because of remapping.  See "man wipe".  Still worth doing, but you should keep the limits in mind and those limits are greater than they used to be, back in the day when the OS managed marking bad clusters like God intended it to. If you really want a secure system now, you have to encrypt the the drive BEFORE any data goes on it, with something like truecrypt or Veracrypt. That isn't to say overwriting will fail consistently either of course. Probably, most of the time, it WILL destroy the data, especially if the file is of recent origin and hasn't been edited, altered, or moved about, and the drive is in good shape.  And of course, if it turns out to have been the wrong file and you accidentally wiped out something irreplaceable that you really NEED, then wipe becomes a totally reliable destroyer of information that consumes date and excretes entropy. Seriously, most of the time it probably works, It is just that you can't count on it.
- bleachbit does have the -o option which overwrites files once. Once is sufficient unless your opponent is willing to take the HD apart and spend non-trivial amounts of money. Of course you still have the remapping and similar issues.
-Using one of the really heavy duty wipers will take longer than you might expect. Think about maybe niceing it to run in the background.
-depends on what you might want to wipe, but you may want to look at the "find" command. It can help you wipe files without wiping the directories they are in. Sometimes that's a real good idea.

---

