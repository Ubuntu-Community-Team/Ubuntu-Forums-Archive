---
title: "Setting up GIT"
date: 2012-01-16
forum: Programming Talk
---

### Post by Gannin on 2012-01-16
I'm rather new to using GIT.  I have a directory full of other directories and files.  I only want to push two of those directories, and their sub-files, into a repository.  As in, I want to create a repository that contains only these two directories and their contents, not everything in the top-level directory.  Is that possible?

---

### Post by Bachstelze on 2012-01-16
Just do [font=monospace]git add[/font] only on the directories you want to add.

---

### Post by Gannin on 2012-01-16
Right on, thanks for the help.

---

### Post by tanderson on 2012-01-16
You might also want to check out ./.git/info/exclude

---

