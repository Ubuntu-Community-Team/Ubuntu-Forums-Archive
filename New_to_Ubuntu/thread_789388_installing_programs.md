---
title: "installing programs?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by teqsun on 2008-05-10
Ok, so I have been using linux for a little while and I was wondering about how programs work.

Like I an type bitchx in the terminal and it brings the program.  but If I compile a programs, I have to use ./programname

how do I get ./programname to be programname?

---

### Post by Steveway on 2008-05-10
Add the directory it is in to your PATH.
Use Google to find out how.

---

### Post by pbpersson on 2008-05-10
I think that some programs have a shell script or symbolic link in /usr/bin that actually points to the /installdirectory/programname

---

### Post by ubersolid on 2008-05-10
I usually build my programs after compiling as deb packages using checkinstall.

Like so:
1. ./configure
2. make
3. sudo checkinstall

And you get a .deb. Easy install and easy to uninstall. Hope it helps you.
checkinstall is available in the repos.

---

