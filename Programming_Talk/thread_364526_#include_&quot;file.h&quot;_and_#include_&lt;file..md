---
title: "#include &quot;file.h&quot; and #include &lt;file.h&gt;"
date: 2007-02-18
forum: Programming Talk
---

### Post by the_nomad on 2007-02-18
which is the main difference between #include "file.h" and #include <file.h> ? aren't they the same?
thanx in advance

---

### Post by maulattu on 2007-02-18
no, they aren't. with
#include "xxx.h"
you're including the file xxx.h that is in the current directory of the file in it will be included, e.g.: if you have xxx.c and xxx.h in the same directory, you must include xxx.h in your .c file as #include "xxx.h" (or, if it's in another directory -> #include "path/to/xxx.h"

#include <xxx.h> impliedly means #include "/usr/src/include/xxx.h" and it's usually used for system header files like stdio.h, stdlib.h, string.h

---

### Post by LordHunter317 on 2007-02-18
maulattu is correct.  "" includes search the local path, which generally means from the directory you are compiling from or the directory the .c file is located in.  Check your compiler manual for the exact rules.

<> searches the system include path.  Genearlly, most compiles support some sort of switch to modify it.  In GCC, the -I switch adds directories to teh system path.

---

### Post by Wybiral on 2007-02-18
Indeed... They alter the way the compiler searches for included files. Quotes tell it to look in the current directory and "<>" tell it to look in the include directory (which by default is "/usr/include")

Installed headers will generally use "<>" and user-made headers (which are in the folder of the main source or relative to that folder) will generally use quotations.

---

### Post by the_nomad on 2007-02-18
thanx a lot guys :) i appreciate.):P

---

### Post by public_void on 2007-02-18
Also if *#include "filename"* fails then the search continues in the place that *#include <filename>* is defined to search.

---

