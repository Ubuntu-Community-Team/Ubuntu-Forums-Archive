---
title: "apt-cache search only showing installed packages"
date: 2006-01-07
forum: Repositories &amp; Backports
---

### Post by OneWingedAngel on 2006-01-07
Something has gone wrong with apt on my system. apt-cache is only listing installed packages when I search. I checked my sources file (fine), did an apt-get update (no change) and reinstalled apt (ditto).

Anyone know what's wrong and how I can fix it?

---

### Post by Saiboogu on 2006-01-08
Having that very same problem, shame no one has replied to this yet. I'll keep an eye on this thread (and go back to my searching... )

Good luck!

---

### Post by Saiboogu on 2006-01-08
As a temporary workaround, I have found that 

```
sudo aptitude search 
```

searches packages not installed, like apt-cache search used to. Still wish I could figure out what is going on here..

---

### Post by OneWingedAngel on 2006-01-10
[QUOTE=Saiboogu]
```
sudo aptitude search 
```
[/QUOTE]

Thanks. (aptitude show works too). I never knew aptitude did this (I always avoided it in my Debian days)

---

### Post by narcisgarcia on 2008-12-23
I've found this alternative command:

sudo aptitude search '~i'keyword

(without separation between ' and keyword)

---

### Post by dE_logics on 2010-03-17
And the bug persists till date.

However updating solves the problem.

---

