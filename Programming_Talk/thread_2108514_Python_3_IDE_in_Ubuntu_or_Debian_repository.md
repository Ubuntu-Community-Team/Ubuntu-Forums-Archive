---
title: "Python 3 IDE in Ubuntu or Debian repository"
date: 2013-01-24
forum: Programming Talk
---

### Post by davidvgregory on 2013-01-24
I have been looking for a Python 3.x IDE in the Ubuntu and Debian repositories and can't seem to find one (other than IDLE, which I consider to be more of a 'decorated editor' than a true IDE). Does anyone know of anything that is appropriate for larger projects and is in the repository?

So far the best solution I can come up with is the Eric 5 tarball (I love Eric 4 for Python 2.7), but I was hoping to just let apt do all the work.

I apologize if I'm asking a question that has already been answered here, but I couldn't seem to find anything.

---

### Post by NilPointer on 2013-01-25
I use Geany. In my opinion, it's great and lightweight IDE. It's in Ubuntu repositories and it supports "projects", has autocompletion, syntax highlighting, etc.

---

### Post by Warren Hill on 2013-01-25
There are lots 

Geany, Pydev in eclipse, idle

Look in the software centre select "Development" then "IDE" you will find lots though not all support Python.

I would go for Pydev personally but the choice is yours.

---

### Post by davidvgregory on 2013-01-25
Thanks for the tips.

I'm checking Geany out as I write this and  planning on looking at Pydev next. I'm trying to migrate from 2.7 to 3.2  right now and I'm forever slipping into the older syntax once I get  "going" and forget that it's not compatible. I'm hoping for something  with an editor that will flag these errors so I can fix it before I  try to run it and get nothing but a stack trace for my effort. Idle will  show me when I am wrong, but has no support for project management or  version control. PIDA, SPE, Eric 4, and Spyder have the latter but they  see 2.7 as syntactically correct.

Hopefully one of these will be what I'm looking for. Otherwise I might have to actually pay attention to what I'm doing...ugh xP

---

### Post by r-senior on 2013-01-25
I've only used it with Python 2 but I believe later versions of pylint can check Python 3 for problems. I set up pylint as a custom build command in Geany so that I can fire it off easily when editing a file.

---

### Post by davidvgregory on 2013-01-25
Looks like I've found what I'm looking for. Thanks everyone for the replies!

---

