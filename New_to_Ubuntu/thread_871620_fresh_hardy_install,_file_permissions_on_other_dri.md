---
title: "fresh hardy install, file permissions on other drives all wrong"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by snuffy on 2008-07-27
have done a fresh install of hardy, now the file permissions on my other drives are all wrong, i opened nautilus as root and changed most of the permissions back to me as owner, but one of them won't stay as owner:myusername and keeps reverting back to owner: root

how do i change the file permission?

cheers
tim.

---

### Post by Sisophon2001 on 2008-07-27
What I do when I have this problem is use chomd like this:

sudo chmod 777 fileorfolder 

and then use nautilus to set permissions back to something sane.

Note that 777 is over kill, and possibly dangerous unless you change it back immediately, but it solves most problems, and then allows you to fix things using graphical tools.

Garvan

---

