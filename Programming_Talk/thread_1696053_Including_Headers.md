---
title: "Including Headers"
date: 2011-02-26
forum: Programming Talk
---

### Post by ZwertY on 2011-02-26
Hey guys,

i learned c for about a year now, and i want do make my own header. It should just be a function which ends the programm. So i already wrote one, but obviously there is something wrong with it...


```
#ifndef PROGCLOSE_H
#define PROGCLOSE_H

int closeProg()
{  int close123 = 0;

  printf("Press a buton to end the programm");

  scanf("%d", &close123);

if (close123 != 0)
{
  printf("Programm was closed \n \n");
  return 0;
}
}
#endif
```

So there it is. I want to just put int closeProg() into my source code. But if i do it just simply nothing happens. It's the complete same thing as if it was not in there. Of course i included the header file by putting #include "close.h" at the top of my source, but as i said nothing happens. So does anyone know why that is?

Thanks in advance.

Oh and by the way, it works perfectly if i just put 

```
int close123 = 0;

  printf("Press button bla bla");

  scanf("%d", &close123);

if (close123 != 0)
{
  printf("Programm was closed \n \n");
  return 0;
}
```
at the very end of my SC. But i want to simplify it by including the header file.

---

### Post by cariboo on 2011-03-14
A bump for the move.

---

### Post by cgroza on 2011-03-14
Never mind...

Declarations in the .h file, definition in the cpp file.

---

### Post by MadCow108 on 2011-03-14
header files usually should not contain any source code, just declarations.
the point of headers it is to provide the compiler with information about code defined in other compilation units it does not yet know about.

e.g. your example:

close.c, contains the code of the function which closes the program (via the exit system call from stdlib.h):
```

#include <stdlib.h>
#include <stdio.h>

void closeProg()
{
  int close123 = 0;

  printf("Press a buton to end the programm");

  scanf("%d", &close123);
  if (close123 != 0)
  {
    printf("Programm was closed \n \n");
    exit(0);
  }
}

```

close.h, the header containing the definition of closeProg so other files can use it:
```

#ifndef PROGCLOSE_H
#define PROGCLOSE_H
void closeProg();
#endif

```

main.c, the main program starting point:
```

// make signature of closeProg known to this file
#include "close.h"
#include <stdio.h>

int main(int argc, char * argv[])
{
  int close = closeProg();
  puts("not closed in closeProg");
  return 0; // but closed here
}

```

compile with:
```

#compile the close function
gcc -c close.c -o close.o
#compile the main function, gcc knows nothing of close.o but it knows the 
# signature of closeProg from including close.h
gcc -c main.c -o main.o
# link the objects to an executable
gcc main.o close.o -o output
```

or shorter
```

gcc main.c close.c -o output
```

---

