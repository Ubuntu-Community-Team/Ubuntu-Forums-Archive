---
title: "cannot execute binary file error"
date: 2009-04-13
forum: Programming Talk
---

### Post by acmariner99 on 2009-04-13
I am compiling a C program. Below is what I use to compile and execute on the command line.

gcc -o programtorun programtorun.h

./programtorun

"cannot execute binary file" 


please help

---

### Post by lisati on 2009-04-13
I'm curious: why are you compiling a ".h" file?

---

### Post by acmariner99 on 2009-04-13
that was how I learned to compile. I set up main, and call a User interface function (within the .h file). I presume I can set up everything within the .c file without the UI function and compile and run that?

---

### Post by mltucker on 2009-04-13
Just put 

```

#include "myHeader.h"

```

(where myHeader.h has the UI function) at the top of the .c file, and then run your gcc command on the .c file.  You compile the file that has the main method.  This makes sense since lots of programs could use that header file.

-Mark

---

### Post by lisati on 2009-04-13
> **acmariner99 said:**
> that was how I learned to compile. I set up main, and call a User interface function (within the .h file). I presume I can set up everything within the .c file without the UI function and compile and run that?

As far as I know, it is more usual to have a ".c" file which you compile, and use C's "#include" to pull in extra stuff from ".h" files as required.

---

### Post by acmariner99 on 2009-04-13
problem solved thanks!

---

### Post by acmariner99 on 2009-04-13
I compiled the .c file instead and have an include to the UI function. Thank you!

---

### Post by hessiess on 2009-04-13
Dont put function implementations in header files, they are for function declarations, and preprosessor macros.

---

