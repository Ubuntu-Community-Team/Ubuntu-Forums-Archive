---
title: "Makefile space question"
date: 2006-07-01
forum: Programming Talk
---

### Post by cwaldbieser on 2006-07-01
I am trying to write a makefile where some of the prerequisites have embedded spaces.  E.g.
```

mytarget: prereq with spaces
     @echo 'prereq is ?<'

```

make sees this as a rule that says "mytarget" has 3 prerequisites, "prereq", "with", and "spaces".  Is there any way I can get it to treat "prereq with spaces" as a single prerequisite?

Thanks.

---

### Post by toojays on 2006-07-01
Use backslashes to escape the spaces:```
mytarget: prereq\ with\ spaces
     @echo 'prereq is ?<'
```

---

