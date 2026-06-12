---
title: "Back up an SVN repository securely."
date: 2011-03-13
forum: Programming Talk
---

### Post by lone_wolfII on 2011-03-13
I'd like to keep a backup of my personal SVN repository. 

The only issue is that I'd like the backup to be encrypted and possibly compressed as well. 

What's a good tool to use to do this? gzip with a password and then an rsync? 

Any opinions are most welcome. :D

---

### Post by lykeion on 2011-03-13
Regarding compression I'd suggest p7zip/7zr. It supports password, encryption, volumes, and lots of compression methods.
Just wonder why you need to be so secretive about your repository?

EDIT
p7zip is actually not a good choice for backups since it doesn't store file group/owner.
Better to use zip which supports encryption with a password, something like this:
```
svnadmin dump repositorypath | zip --encrypt > svnbackup.dump.zip
```

---

### Post by MadCow108 on 2011-03-13
duplicity does this:
[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)

((I never used it so I can't tell if its any good)

---

### Post by lone_wolfII on 2011-03-21
Thanks guys, I'll give them a shot.

---

