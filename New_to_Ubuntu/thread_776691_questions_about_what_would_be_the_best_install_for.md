---
title: "questions about what would be the best install for me"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by vphreeze on 2008-04-30
ok, so i am obviously new here (and to Linux). i tried out an Ubuntu 7.10 Live disc and liked it enough to wanna play with it more...and then Hardy came out. i was due to reformat my laptop anyway, so i partioned off my 100gb hard drive into a approximately 10gb for Windows XP, 80gb as a stoarage space for my files (that both OS's can access) and left 10gb as unformated free space for a future Ubuntu install.

as of now, i have used Wubi to install Ubuntu 8.04 under XP, just using 4gb of space while i tried some stuff out. i really like how easy Wubi was, and i like the option of the dual boot. i am gonna want to move/reinstall Ubuntu to the free space i left for it and i was curious if it would be better to format the free space and tell Wubi to install there, or use the regular Live CD and install it that way?

if i go with the Live CD, will it automatically detect and set up **just** the free space accordingly? or do i need to create a formatted partion out of it first? if i format, should i go FAT32 or NTFS, or will Ubuntu reformat the space to the appropriate format? how hard will it be to keep the dual boot as it is with XP first (and auto) and Ubuntu as the alternate choice?

if i go with a reinstallation using Wubi, would there be any sort of performance difference since it would now be on its own partion instead of Window's? would it matter if i formatted the partion as FAT32 or NTFS?

---

### Post by vphreeze on 2008-05-08
in case anyone cares, i ended up finding some instructions for dual booting on a Mac that answered my question. basically, it said that i need to take approximately double the RAM i have and reserve that for a "swap" partition and the rest could be for the OS installation. so that makes 8gb for Ubuntu with a 2gb swap partition (i have 1gb of RAM). i did this a day or so after the original post, and everything has been working great so far.


by the way, i am not trying to bump my own thread or anything, i just wanted to post that the problem was solved and what i did...in case anyone comes across my post while searching for answeres to a similar question.

---

### Post by Sef on 2008-05-08
> so that makes 8gb for Ubuntu with a 2gb swap partition (i have 1gb of RAM). i did this a day or so after the original post, and everything has been working great so far.

Actually with 1 gbs, you don't really need that much swap.  1 gb swap is enough.  1 1/2 times applies to when less ram was installed.

> by the way, i am not trying to bump my own thread or anything, i just wanted to post that the problem was solved and what i did...in case anyone comes across my post while searching for answeres to a similar question.

It's ok to bump your thread as long as 24 hours have gone by since your last post.

---

