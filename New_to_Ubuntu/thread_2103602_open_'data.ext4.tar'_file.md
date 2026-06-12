---
title: "open 'data.ext4.tar' file"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by dlw on 2013-01-10
How is 'data.ext4.tar' file opened in 12.10?
Archive Manager will not open it.

dlw

---

### Post by Impavidus on 2013-01-11
Archive manager (which is, at least on my machine, actually called **file-roller**, but can be opened from the file manager by rightclicking on a file and selecting "open with archive manager") should be able to open .tar files.

First make sure it really is a .tar archive. The file manager (or at least thunar, I'm not sure about nautilus) assumes it's a tar archive whenever a file is called .tar, but this is no guarantee. Type in a terminal ```
file /path/to/data.ext4.tar
``` (substitude the correct path)
It should give us the exact file type. If it's not something like "tar archive" this file isn't what it pretends to be.

If it is a tar archive you can unpack it in a terminal with```
tar -xvf data.ext4.tar
```It's best to first put it in a directory of its own. If not well-behaved, tar archives can produce a lot of files in the current directory.

---

