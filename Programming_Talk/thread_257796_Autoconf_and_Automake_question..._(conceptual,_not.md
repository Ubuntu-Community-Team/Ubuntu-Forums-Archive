---
title: "Autoconf and Automake question... (conceptual, not technical)"
date: 2006-09-15
forum: Programming Talk
---

### Post by mike41 on 2006-09-15
So Im trying to understand how these tools work and Im a bit confused. Are they always used together, or do they stand as independent programs? Let me know if Im correct. Autoconfig takes configure.in and makes a configure script. Automake takes makefile.am and creates makefile.in. Now does the configure script edit makefile.in? But makefile.in wasn't created until after the configure script was run, so does it actually edit makefile.am? 

I dont know why im getting so confused, but I am.

---

### Post by toojays on 2006-09-15
The configure script takes Makefile.in, and substitutes various variables in it to create the Makefile. It does not change Makefile.in (which is created by automake) or Makefile.am (which is created by a person).

---

