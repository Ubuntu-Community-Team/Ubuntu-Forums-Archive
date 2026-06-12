---
title: "svn: omitting backup files from vim (.bak)"
date: 2007-07-29
forum: Programming Talk
---

### Post by orlox on 2007-07-29
Hi! Well, my question is pretty much what the topic of the post says. Im developing a website and I'm using vim, wich generates backup files (*.bak). I need a way to make svn ignore this files when making a commit. I read something about making svn ignore certain kinds of files on a specific folder, but I need a way to make svn ignore all files of a certain type (in this case, the .bak files) when commiting.

---

### Post by AlexThomson_NZ on 2007-07-29
If you can live without vim creating backups, add this to your .vimrc

set nobackup

(Don't know how to get svn to ignore them, but it's something anyway)

---

### Post by scooper on 2007-07-29
You can also redirect the backup files elsewhere.  For example, these lines in my ~/.vimrc file place backups and swap files in ~/.backup or in a .backup subdirectory of the working directory.  If neither is found I think it follows the default rules, but merely creating ~/.backup will change where the files go.

```
set backupdir^=./.backup,$HOME/.backup
set directory^=./.backup,$HOME/.backup
```

---

### Post by orlox on 2007-07-30
Perfect! Setting the backup files as you said does the trick :)

Thanx!

---

