---
title: "[SOLVED] Which package provides a file"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by dupa on 2008-08-21
I have a very simple question.
How can I know (from command line) which packages provides a file i have not on my system?

thanks

---

### Post by Troll_the_Great on 2008-08-21
Open a terminal and type
```
sudo apt-cache search name_of_file
```
I think this is what you want.
Cheers!

---

### Post by dupa on 2008-08-21
> **Troll_the_Great said:**
> Open a terminal and type
```
sudo apt-cache search name_of_file
```
I think this is what you want.
Cheers!

it works. great. thank you

---

### Post by Troll_the_Great on 2008-08-21
Was this it?If yes please mark your thread as "Solved" using the "Thread tools" from the top of the page.
Cheers!

EDIT:too slow, you already did :)

---

### Post by kpkeerthi on 2008-08-21
> **dupa said:**
> I have a very simple question.
How can I know (from command line) which packages provides a file i have not on my system?

thanks

**dpkg -S <file>** Searches for <file> in package database, telling you which packages have that file in them.

---

### Post by forger on 2008-08-21
He asked
> How can I know (from command line) which packages provides **a file i have not on my system**?

I think you cannot do that unfortunately, only through a package database, i.e. [http://packages.ubuntu.com](http://packages.ubuntu.com) - use **Search the contents of packages**

edit: Hm.. apt-cache search seems to do the trick, spoken too soon

---

