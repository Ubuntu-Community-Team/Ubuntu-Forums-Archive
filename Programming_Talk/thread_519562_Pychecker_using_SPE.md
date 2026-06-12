---
title: "Pychecker using SPE"
date: 2007-08-07
forum: Programming Talk
---

### Post by in_flu_ence on 2007-08-07
Hi,

    I was using Pychecker in SPE and I have the following error.

basically, i made the following statment.

def dfhw(Uw,Uo,g,ST,denso,densw):
...

Pychecker prompts me the following error
identifier (g) not used
identifier (ST) not used.

What is this error about and how to resolve them?

Thanks

---

### Post by pmasiar on 2007-08-07
I bet it is not error but warning. You pass g and ST patameters to a function but don't use them in function body.

Suggestion: use longer, more descriptive names for both functions and variables.
You need to write them only once, but read them many times. Maybe you remember now what g is,  but 6 months from now, will you remember it anymore?

---

