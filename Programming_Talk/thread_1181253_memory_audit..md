---
title: "memory audit."
date: 2009-06-07
forum: Programming Talk
---

### Post by leblancmeneses on 2009-06-07
I have several malloc, realloc, free in my code.

what tools do you all recommend and how do i run them to help identify if there are any memory leaks?

preferably command line utilities:

language is c and i have libraries similar to this signature:
void rh_stack_constructor(rh_stack_instance* instance, void (*onFreeing)(rh_stack_node*));

---

### Post by MadCow108 on 2009-06-07
valgrind is usally the tool of choice

---

