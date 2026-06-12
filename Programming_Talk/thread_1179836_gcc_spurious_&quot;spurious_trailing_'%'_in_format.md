---
title: "gcc: spurious &quot;spurious trailing '%' in format&quot;"
date: 2009-06-06
forum: Programming Talk
---

### Post by bcz on 2009-06-06
Have just loaded Ubuntu 9.04 and added stuff from repositaries so I can compile GTK programs

My programs were compiling fine on Fedora 9 (and still do)

I am getting compiler warnings.

Statement...      sprintf(workX,"%d.%02d\%",w1,w2);

gives spurious warning "spurious trailing '%' in format

Seems to be a problem with gcc (or grey hairs are beginning to tell)
But Fedora 9 had no problem

Any help appreciated

Bill C

---

### Post by Linteg on 2009-06-06
gcc on F11 warns about this too (at least when using -Wall) so I don't think there's something wrong with your compiler. Do you want to print a %-sign at the end? If so, the correct notation should be %% not \%.

---

### Post by bcz on 2009-06-06
Thanks Linteg

Problem solved

Pure chance that earlier compiler treated '\' escape character the way I wanted it to.  So a better compiler forces me to correct my old code.

Making mistakes proves I am human.  Hopefully I don't make too many

Mislaid my ANSI C Bible years ago, but doubt if I would have checked the right place...  So thanks again

If you're in Melbourne, I owe you a beer

Rgds Bill C

---

