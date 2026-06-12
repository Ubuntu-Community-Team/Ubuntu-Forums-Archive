---
title: "[SOLVED] Keeping it up to date"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by CCCody on 2008-07-23
So I installed Ubuntu again and really seem to be liking it this time, I still can't do everything I need to do but it's getting better. 

Anyways how or what do I use to clean up files that are no longer needed, drive defreg etc, all the stuff that keeps your system fresh and up to date?

Thanks for the help. Peace yo!

---

### Post by halitech on 2008-07-23
because of the way the file system works, no need to do a defrag like you had to in windows. Far as cleaning up files, the only thing you really need to clean up is the temp files in firefox.

---

### Post by CCCody on 2008-07-23
So I don't have to do a registry like cleanup or anything? Once I delete a file from my computer it's gone? No extra crap to delete with it?

Also where would I go to see currently installed programs? Sort of an Add/Remove type thing.

Thanks!

---

### Post by scragar on 2008-07-23
Applications>Add and Remove
or
System>Administration>Synaptic Package Manager

first is for the most common packages, second is a list of all packages available to download easily, use **status** on the bottom left, then installed above it to only see installed packages.

---

### Post by halitech on 2008-07-23
there is no registry in linux like windows so no, you don't have to clean the registry at any time :) As far as deleting files, once you remove it from the trash, its gone forever (so make sure you don't delete anything you want to keep)

2 was to see installed apps, Applications -> Add/Remove Programs or System - Administration - Synaptic Package manager

---

### Post by CCCody on 2008-07-23
Thanks, appreciate the help from both of you! You have my thanks.

---

### Post by halitech on 2008-07-23
very welcome :) if we have answered your questions, mark the thread solved so others will know it is closed.

---

### Post by tiachopvutru on 2008-07-23
Also, all configurations and system settings are stored in files. If you want to keep your personal settings and files, preserve your /home directory. 

Google for "Linux's directory structure" to get some familiarities, [here]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")'s the first result.

No need to worry about defragmenter unless you use more than 80% or 90% of your hard drive. In Windows, it's at this point that you can't defrag any longer. So in either situation, it's best to leave some spaces in your hard drive. :)

---

