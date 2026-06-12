---
title: "Changelog-making application?"
date: 2006-10-21
forum: Programming Talk
---

### Post by luca.b on 2006-10-21
Hello.
I'm trying to make a changelog of something, but I'm looking if there are nicer ways to do it (formatting-wise) save to type everything manually (something like dch -i for packaging). In alternative, is there anything to parse SVN log entries into a changelog? Thanks in advance.

---

### Post by toojays on 2006-10-21
Emacs has special facilities for editing changelogs. While you are editing your source code, press C-x 4 a, and Emacs will begin an appropriate changelog entry for you. It also has a function for extracting changelog data from a VCS, but I'm not sure how well it works with SVN (IIRC Emacs 21 did not support SVN, you need an snapshot of Emacs 22).

---

