---
title: "gforth include file problem"
date: 2011-04-08
forum: Packaging and Compiling Programs
---

### Post by robotz421 on 2011-04-08
I am using gforth and am trying to use postgreSQL.  I have the following code:  

```

\c #include  <libpq-fe.h>
c-function PQconnectdb PQconnectdb a -- a  

```When I try to use PQconnectdb I get: "error: libpq-fe.h: No such file or directory".  I have libpq-dev installed and I can find libpq-fe.h in /usr/include/postgresql.  Why is the include file not being found?

---

### Post by robotz421 on 2011-04-08
hmm my post seems to be messed up a bit.  How do I use one of those code boxes? Okay, I have the post fixed now.

---

### Post by SevenMachines on 2011-04-09
I know nothing about forth but since libpq-fe.h is in /usr/include/postgresql/ i would guess that it should work if you make the include relative to the system include path /usr/include, ie
```
#include  <postgresql/libpq-fe.h>
```or add /usr/include/postgresql/ to the search path at  the command line, sorry, no idea how thats done in forth

---

### Post by robotz421 on 2011-04-10
Thank you.  That has solved the problem.

---

