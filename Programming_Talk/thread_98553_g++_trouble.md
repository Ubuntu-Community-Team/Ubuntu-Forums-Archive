---
title: "g++ trouble"
date: 2005-12-03
forum: Programming Talk
---

### Post by grim918 on 2005-12-03
i have 2 computers that are running ubuntu one of them is running in server mode and the other has the normal breezy badger. i installed the the g++ compiler on both of them and the compiler works great on regular one but it doesnt work on the server version. i installed the package using 
sudo apt-get install build-essential.
does anyone know what could be causing the problem.

---

### Post by invalid on 2005-12-03
You will have to be more specific. What is the exact error you get when you try to use it?

Cb

---

### Post by KingOfNowhere on 2005-12-06
You need to be more specific with your problem, but depending on what you are trying to complie, you may need a different version of g++ (if this is 3rd party software). Explain your problem and post your error.

---

### Post by JohnnyMast on 2005-12-06
Both gcc and g++ are notinstalled by default, my suggestions ofpackages to apt-get

 gcc3.6 
 g++
 make
 manpages-dev

These will turn your machine into a uber super development machine for when your building packages the old old fashion wat (./configure ; make; make install )

---

### Post by LordHunter317 on 2005-12-06
That's not enough.  You should always install build-essential at a minimum.

---

### Post by blanky on 2005-12-06
> 
i installed the package using
sudo apt-get install build-essential.


Guess he already did.

---

