---
title: "Trying to program where downloads ALL from directory."
date: 2009-07-22
forum: Programming Talk
---

### Post by JK3mp on 2009-07-22
Okay, so suppose there's a site full of txt's and sub folders with txts in a directory. Anyone know a way i can start up on a program that downloads everything in a directory. None of the files are proteected or any of that shizz but theres a ton of them and 1 by 1 would be long. I figure i can work a program with wget or similiar function to get to that/similiar result. Any help appreciated, thank you.

---

### Post by soltanis on 2009-07-22
Okay, slow down? Over HTTP? You can do that with wget.

In a more general case, if you are trying to make a list of files in a directory (for the purposes of say, downloading them), then the difficulty of this task depends on the language you are using (for C, it is long and complicated; for perl, it is one statement; for other languages, it varies).

---

### Post by The Cog on 2009-07-22
Sounds like a job for **rsync**. rsync can log in using SSH and retrieve an entire subtree.

---

