---
title: "Help with LFS"
date: 2009-07-23
forum: Packaging and Compiling Programs
---

### Post by nikhilbhardwaj on 2009-07-23
Hi i've been using ubuntu for some time
i decided to build a lfs system reading the book lfs 6.4

i've been able to successfully start my computer
but there's an error message that i get
while the initial scripts are started

/etc/rc.d/rcsysinit.d/S80localnet
line 27 hostname command not found

and my login prompt is
(none) login:

it appears that hostname isn't installed
which package source can i find hostname in
or is it that perhaps it is installed some place else and i need a symlink

i'd appreciate if you could help me with this

---

### Post by nikhilbhardwaj on 2009-07-26
got it
it was in nettools-1.30

i had made a mistake with coreutils which also has this program
now alls well

---

