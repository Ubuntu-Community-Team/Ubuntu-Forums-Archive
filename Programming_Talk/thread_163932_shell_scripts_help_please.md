---
title: "shell scripts help please"
date: 2006-04-21
forum: Programming Talk
---

### Post by deathbyswiftwind on 2006-04-21
Hi I just bought the book wicked cool shell scripts and I need some help. What all do I need to download to write these shell scripts?

---

### Post by unbuntu on 2006-04-21
It depends on what shell your book is dedicated to.  Normally bash.  If so, you don't have to download anything because bash is the default shell for ubuntu.

---

### Post by mostwanted on 2006-04-22
[QUOTE=deathbyswiftwind]Hi I just bought the book wicked cool shell scripts and I need some help. What all do I need to download to write these shell scripts?[/QUOTE]

Scripta are made up of text. You just open Gedit or Kate and start typing, save it and make it an executable.

---

### Post by IYY on 2006-04-22
Ubuntu has the most common shells installed by default (bash, sh). Look at the scripts in the book: the first line of each would be #!/bin/*shellname*

Where *shellname* is the name of the shell used. If it's not installed by default, you can get it by 

sudo apt-get install *shellname*

---

