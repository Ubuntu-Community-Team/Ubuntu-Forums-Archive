---
title: "batch delete all files of certain type in folder and subfolders"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by toomanymatts on 2013-04-22
hi guys

Wondering if there's a better way than manual...I downloaded some training materials, and it is all in a folder, with about 200 subfolders (4 levels deep), in the end holding about 900 files (about half-half for the various m4v video lessons and mp3 audio lessons).  

I only want the audio files.

Is there a way (pref with GUI but terminal if I have to) where I could point it at the highest level directory and say 'banish all ye m4v files' and have it delete all the video files from all the subfolders therein?

Thanks for any assistance

Matt

---

### Post by schragge on 2013-04-22
In terminal, try this:
```
find /path/to/directory -type f -name \*.m4v -delete
```

---

### Post by toomanymatts on 2013-04-22
ignore me...

for the sake of posterity, I installed Nautilus Actions Extra, searched the top directory and trashed.  Easy (and kinda feel dumb asking now :) )

---

