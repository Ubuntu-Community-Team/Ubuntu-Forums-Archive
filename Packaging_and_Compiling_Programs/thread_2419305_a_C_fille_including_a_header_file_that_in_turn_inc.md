---
title: "a C fille including a header file that in turn includes another header file"
date: 2019-05-20
forum: Packaging and Compiling Programs
---

### Post by vigalchin on 2019-05-20
Ironically I am not a newbie but slightly fuzzy memory. I am trying to punch my way out of a wet paper bag :-(

Ok ....

- I have two directories .. say dirA and dirB.

-  dirA contains my C bozo.c file along with an include file (also in dirA) donbass.h. "donbass.h" includes an iinclude file  "donesk.h" from dirB.

- for now I am using command line (bash shell) complilation

      gcc -I. - IdirB -c bozo.c

The gcc compiler can't find ditrB/"dobass.h" ... Why?  (Should be easy peesy") :-(


BTW I using Ubuntu 18.04 and gcc 7.3.0.

Vasily

---

### Post by spjackson on 2019-05-21
I am afraid that is all very confusing... which may explain why nobody has tried to help yet.

> 
- I have two directories .. say dirA and dirB.

-  dirA contains my C bozo.c file along with an include file (also in  dirA) donbass.h. "donbass.h" includes an iinclude file  "donesk.h" from  dirB.

- for now I am using command line (bash shell) complilation

      gcc -I. - IdirB -c bozo.c

So far so good... (except for the space between the - and IdirB but I'll assume that's a typo).
> 
The gcc compiler can't find ditrB/"dobass.h" ... Why?

You haven't mentioned ditrB before, is it a typo for dirB?
You haven't mentioned dobass.h before, is it a typo for donbass.h?
But you said that donbass.h is in dirA, so I'm confused.
gcc will not (cannot) show the relative directory name for a header it cannot find unless that relative directory is specified in the #include directive e.g.
```

#include "ditrB/dobass.h"

```
If you are doing that, you need -I for the parent directory of ditrB.

It would help if you could show all relevant #include directives, without typos, and the verbatim compiler output.

Is dirB a sub-directory of dirA or are you correctly using the relative path? e.g.
```

gcc -I. -I../path/to/dirB -c bozo.c

```

---

### Post by TheFu on 2019-05-21
Assuming ... 
```
$ tree -d proj
proj
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; contrib
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; include
&#9474;** &#9500;&#9472;&#9472; dirA
&#9474;** &#9492;&#9472;&#9472; dirB
&#9500;&#9472;&#9472; lib
&#9500;&#9472;&#9472; share
&#9492;&#9472;&#9472; src
```
If it were me, I'd use *-I include/* and assume the PWD was the project top and let the makefile determine the real top directory at build time. Then inside my code, the headers would be 
```

#include "dirA/donbass.h" 
#include "dirB/donesk.h" 
```
But that's me.  Lots of reasons for this, but non-professionals are usually struggling with other coding issues so making a great makefile/Cmakefile that does lots and lots of things automatically isn't normal.

---

