---
title: "How to update archive"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by The__Doctor on 2011-09-17
If I've made a backup of my home folder, and stored it on a flash drive, how do I update the archive so that files deleted in my home folder are deleted in the archive and files added in my home folder are added to the archive and files modified are also modified/re-added to the archive.

---

### Post by Frogs Hair on 2011-09-17
I have used Back in Time for home folder backup. With the software it is possible to take snap-shots of the home folder anytime changes are made and keep or discard backup snap-shots.

I don't know how you could change just certain portions of The USB if it is read only .

---

### Post by The__Doctor on 2011-09-19
Taking snap-shots would use too much diskspace. Also, I want to put the backups on a USB flash drive so I can move the documents to  new computer or something.

Why are USBs read-only?

---

### Post by Lisiano on 2011-09-19
To name a few backup utilities, rsync, Deja Dup, Git. Read the man (Manual) pages for all of them by googling "man <Name of Program>" or typing this in a terminal```
man bash
```
In short, Rsync is a backup utility that works from the command line (Terminal)
Deja Dup - Not sure myself as I don't use it, but I guess something along the lines of "Rsync in a GUI". Someone please correct me on that.
Git - A version control system developed by Linus Torvalds AKA Our Linux God. Usually used for controlling file versions, usually source code but technically nothing stops you from using it as a backup utility. Technically. Practically I think no one does that on their files but someone might do it on documents and projects.
To find more just google "Backup in Linux OR Ubuntu" the capital OR is important. Google will treat it as "Backup in Linux" and "Backup in Ubuntu" and combine the search results.

---

