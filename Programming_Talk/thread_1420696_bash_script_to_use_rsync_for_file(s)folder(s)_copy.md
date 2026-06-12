---
title: "bash script to use rsync for file(s)/folder(s) copy?"
date: 2010-03-03
forum: Programming Talk
---

### Post by halfvulcan on 2010-03-03
I've been looking around and I can script a little, but I really could use a pointer if anyone knows where I can find a bash script that would do something similar to:
I select a file or folder or group of files or folders, some may contain spaces in the names, right-click from PCmanfm (though I imagine almost any linux file manager would work), choose "open with", choose "Copy with Rsync" from the applications list (because I've put a .desktop file in /usr/share/applications pointing to the bash script), it would popup a zenity folder selection window with "Destination" in the title, I'd select the folder to rsync to. It would then maybe flash a pulsating progress bar or the rsync verbose output until the rsync is finished copying/syncing the files and folders to UNDER the folder I selected (just like copy would).  There should also be in the script a provision for if I've launched the script directly with no file selection string, in which case it would first put up a "Choose source files or folders" file selection window.  

This may or may not be a tall order depending on someone's skill level.  I can almost figure out how to do this myself already, stealing pieces of some scripts I've found that use zenity for various purposes, but it would take me many hours unless I could look at an already existing script that has most of these functions working already.  But think about it, sometimes we find ourselves about to copy a massive folder over an older one.  Our first thought is to just copy it over the old one, but then we think "ughh, last time I tried to copy that much data, the file transfer was stopped by one file that failed to copy over the old one because of a permissions or some other issue".  Rsync is a great potential solution because it deals with such things well and it can just skip what it isn't able to copy over, and most of the time, that's good enough for me.

---

### Post by geirha on 2010-03-03
I suggest you try [grsync](apt:grsync) and see if that suits your needs before trying to implement your own.

---

### Post by halfvulcan on 2010-03-03
> **geirha said:**
> I suggest you try [grsync](apt:grsync) and see if that suits your needs before trying to implement your own.

Thank you!  That looks like exactly what I was hoping for.  Sweet. And in the repositories, right in plain sight.  I can't believe I never noticed that.

---

### Post by halfvulcan on 2010-03-04
Update:  okay, not exactly, but a good temporary solution until I get the full functionality I want (any selection of files selected with the file manager transfered to any folder using rsync, overwriting only files that have changed, skipping files it can't replace).  It occured to me that what I want can probably be reverse engineered from a good "copy-to" script using zenity, such as discussed in this thread: [http://ubuntuforums.org/archive/index.php/t-101859.html](http://ubuntuforums.org/archive/index.php/t-101859.html) .  Then most of what's left is probably converting the copy lines to rsync lines.  It will probably require a bit of tweaking to get the syncing of individual files correct.  I've only glanced at those scripts so far, but hopefully someone will find this thread and get good footing on the narrow shoulders of my research.

---

