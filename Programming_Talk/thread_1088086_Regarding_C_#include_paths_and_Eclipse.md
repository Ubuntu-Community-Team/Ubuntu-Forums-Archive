---
title: "Regarding C #include paths and Eclipse"
date: 2009-03-05
forum: Programming Talk
---

### Post by adambard on 2009-03-05
DISCLAIMER: I'm new at this.

So I've downloaded a large chunk of code constituting firmware for an AVR wireless development kit, and each file #includes a number of header files.

The directory structure is pretty hierarchical, with lots of subdirectories containing various header files and so forth.  However, all the include directives contain no information regarding path, just the name of the header file with the quote syntax, e.g. #include "compiler.h"

Naturally, hitting the "build" button causes Eclipse to complain bitterly about all these files it can't find.

What recourse exists besides going to each text file and updating the paths to be complete?  I assume there's some blindingly obvious solution that I'm simply not aware of.

Thanks in advance.

---

### Post by Can+~ on 2009-03-05
Are you sure it's not "<compiler.h>"? As in linked with the -I flag or other?

Does it come with a make file?

---

### Post by adambard on 2009-03-05
No makefile is apparent.  And it definitely uses the double-quote syntax, exactly like this:

#include "compiler.h"

---

