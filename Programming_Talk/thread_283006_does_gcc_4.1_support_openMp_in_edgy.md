---
title: "does gcc 4.1 support openMp in edgy"
date: 2006-10-23
forum: Programming Talk
---

### Post by Relain on 2006-10-23
well the title says it all. I tried looking around and didn't find much. WIkipedia says it does in some distros, but in ubuntu? Don't want to move my core box to edgy until it's 'stable'.

thanks

---

### Post by maubp on 2006-10-24
I was under the impression that only RedHat had backported OpenMP to gcc 4.1

If you search the forum there are some old thread on this topic - you might want to try Intel's compiler (free as in beer, read the small print) which also supports OpenMP.

I installed icc 9.1 on Ubuntu Dapper Drake and it seems to work.  I haven't managed to get my code to run any faster using this, but it does use both cores on my Athlon.

I do want to try the gcc openmp support at some point, just to see if it does any better.

---

