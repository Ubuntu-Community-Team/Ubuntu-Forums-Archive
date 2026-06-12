---
title: "Compile gnumeric problems encountered"
date: 2012-04-05
forum: Packaging and Compiling Programs
---

### Post by anticode on 2012-04-05
when i compile gnumeric :

gnm-solver.c: In function 'gnm_solver_class_init':
gnm-solver.c:1234:10: error: 'gnm__BOOLEAN__OBJECT_POINTER' undeclared (first use in this function)
gnm-solver.c:1234:10: note: each undeclared identifier is reported only once for each function it appears in
gnm-solver.c:1256:10: error: 'gnm__BOOLEAN__POINTER' undeclared (first use in this function)
gnm-solver.c:1266:10: error: 'gnm__VOID__BOOLEAN_INT' undeclared (first use in this function)

In gnm-marshalers.c i find the gnm__BOOLEAN__OBJECT_POINTER, and in gnm-solver.c head #include "gnm-marshalers.h"

I don't know how to Solve this problem

---

### Post by Paddy Landau on 2012-04-06
Why don't you just install gnumeric from the repository?

---

### Post by oldos2er on 2012-04-06
Thread moved to Packaging and Compiling Programs.

---

### Post by anticode on 2012-04-06
> **oldos2er said:**
> Thread moved to Packaging and Compiling Programs.

Please say in detail,thanks

---

