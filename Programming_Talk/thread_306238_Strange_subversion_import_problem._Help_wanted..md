---
title: "Strange subversion import problem. Help wanted."
date: 2006-11-24
forum: Programming Talk
---

### Post by CJNyfalt on 2006-11-24
Hi, most normal subversion commands like checkout, status and diff works for me, but import fails.

Each time I try to import something, I get the following:
sh: /usr/bin/bin: not found
svn: system('/usr/bin/bin svn-commit.tmp') returned 32512

Seems like a broken shellscript, but where? ](*,)

EDIT:
And typically I managed to figure out the problem some minutes after I posted.
It was a typo in $SVN_EDITOR.

---

