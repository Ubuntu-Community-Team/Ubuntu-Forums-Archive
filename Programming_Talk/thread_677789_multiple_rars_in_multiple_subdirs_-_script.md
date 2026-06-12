---
title: "multiple rars in multiple subdirs - script?"
date: 2008-01-25
forum: Programming Talk
---

### Post by yrufset on 2008-01-25
Hello all.
let's say iv'e got a dir called ABC, and it contains the next subdirs: ABC1, ABC2... ABC19.
in any of the ABC1..19 i got rar archives (rar, r00...r19).

you can look at it as if it's the whole season of McGyver or something, and every dir' is one episode.

my goal is to unrar all of the subdirs to ONE folder, in the shortest way.

what i'm doing now, is Extract Here... for every subdir (which take decades), and then go dir' by dir', copying the extracted file into the new dir'.

in windows there used to be an app which lets you r-click a dir, then choosing 'search for archives' which would generate a new window with all of the archives found on that dir', and then you could unrar them all to a new location with one click.

any help will be much appriciated :)

---

### Post by vanadium on 2008-01-25
With the find command, you can find all rar files in the directory three and execute a command with what is found:

find . -name '*.rar' -exec <command> {} \;

The "{}" gets substituted with the found item. The "\;" is a mark for "find"that shows where the command passed to -exec ends. You should then add appropriate command line options for the command to unrar in the location you specify.

---

### Post by yrufset on 2008-01-25
thanks for the fast reply.

i tried:
 find . -name '*.rar' -exec unrar {} /home/myuser/down /

and got:
find: missing argument to `-exec'

any ideas why?

---

### Post by yrufset on 2008-01-25
Well, I Got It!!
found an old post about a different question, but the answer did the trick.

anyway, in order to extrect all of the rar files in a given directory (into the main dir) i used:
find -type f -name '*.rar' -exec unrar x {} \;

as i said, it worked flawlessly ;)

---

