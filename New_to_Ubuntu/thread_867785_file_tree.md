---
title: "file tree"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-23
so I'm practicing at the command line, learning my way around.  so when I first start my terminal it is in adamogardner.  the parent directory od this is my home directory, and the only thing in my home directory is adamogardner.  Is this needed?  I didn't exactly intend to set my computer up one  way or another. but I'm findong it inefficient to go through two parent directories to get to wherever comes before home directory (the one that holds bin and etc et al.   So is there a point to having an adamogardner directory?  Other users wouldn't be found in my home folder would they?  that would make the homew folder shared?  or does that have to do with setting permissions?   I'm just trying to get a better grasp of this and why it's this way

---

### Post by arubislander on 2008-07-23
Hi,

The /home directory is where all the home-directories of the users you define on your computer. So the /home directory is not yours but the system's (or more specifically root's). Every user's home directory lives there in the form of /home/<usernam> 

Happy exploring.

---

### Post by nick_h on 2008-07-23
Here is a link describing the Linux Filesystem Hierarchy:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by Potatoj316 on 2008-07-23
you could use cd / to get to root instead of cd ../.. then to get back to your home directory cd ~/ works (maybe its just cd ~ i never use it)

---

