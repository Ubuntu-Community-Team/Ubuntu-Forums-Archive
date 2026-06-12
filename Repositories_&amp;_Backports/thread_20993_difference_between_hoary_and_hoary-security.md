---
title: "difference between hoary and hoary-security"
date: 2005-03-19
forum: Repositories &amp; Backports
---

### Post by abovett on 2005-03-19
This may be a dumb question, but what's the difference between using "hoary" (or "warty") and "hoary-security" (or "warty-security") as the "distribution" entry in sources.list?

Obviously the "hoary-security" one is something to do with security! But is one a superset of the other, or what? Will versions of the same package be found in both? And if so, are they the same or different?

I realise I may be misunderstanding how apt works here (I'm pretty new to debian/apt based distros) - in which case can someone point me to something that will help me understand better? I had a look at the manpage but it didn't answer my question.

Thanks

Andy B

---

### Post by az on 2005-03-19
The packages are like a house of cards.  One can depend on another, and that one can depend on another.  Before advanced packaging, to change one package and not correct the dependancies (and break your system) was known as dependancy-heck.

There is a security repository for security updates.  Once the distubution is released, you cannot change the versions of the packages.  Everything must stay the same, with the exception of bug fixes and security patches.  These go into the security updates repository.

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=abovett]I realise I may be misunderstanding how apt works here (I'm pretty new to debian/apt based distros) - in which case can someone point me to something that will help me understand better? I had a look at the manpage but it didn't answer my question.

Thanks

Andy B[/QUOTE]
[Introduction to Apt-get](http://www.newsforge.com/article.pl?sid=04/12/02/1710208). One from many list of informative website that I have compiled at [HowTo: For People New to Ubuntu](http://ubuntuforums.org/showthread.php?t=13042)

---

