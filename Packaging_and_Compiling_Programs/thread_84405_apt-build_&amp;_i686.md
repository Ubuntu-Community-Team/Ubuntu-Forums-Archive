---
title: "apt-build &amp; i686"
date: 2005-10-31
forum: Packaging and Compiling Programs
---

### Post by GoldBuggie on 2005-10-31
When I use apt-build and a i686 kernel it does not seem to work. The compilation gives me an error when reaching the c compiler: could not make executable or something like that. Anyway...the problem I think is that when you look for which system is detected it says i386. When I do a normal./configure it says i686. But apt-build uses the dpkg --print-artchiteture(bad spelling) and that says i386. 

dpkg has a hard-coded print of which system it is(at least this is what i have concluded). So my question is....how do I get apt-build to work for my i686 kernel???

I would like to recompile something for my computer but in the same time not break some of the ubuntu specifics files or directories. Apt-build is a great idea but now how to get it to work?

---

