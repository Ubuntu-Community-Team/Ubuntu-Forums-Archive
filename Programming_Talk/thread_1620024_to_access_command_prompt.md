---
title: "to access command prompt"
date: 2010-11-12
forum: Programming Talk
---

### Post by c2tarun on 2010-11-12
hi friends is there a way that i can access command prompt from a C program.
I mean i want to pass some commands to terminal of command prompt via a C program

---

### Post by TiBaal89 on 2010-11-12
> **c2tarun said:**
> hi friends is there a way that i can access command prompt from a C program.
I mean i want to pass some commands to terminal of command prompt via a C program

Yes, indeed... system("blah") will run the blah command.  If you're running your program from the terminal, the results will be output to that terminal.

Try this out: 

```
#include <stdlib.h>

int main() {

  system("ls");

}
```

EDIT:  oops! :D

---

### Post by hakermania on 2010-11-12
You have to
```
#include <stdlib.h>
```
to use system()

---

