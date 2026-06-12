---
title: "Doubt wiht system() function in C"
date: 2010-04-27
forum: Programming Talk
---

### Post by indarkness on 2010-04-27
HI!!
 
I've got a doubt using the system() function in C and GNU.
 
I'd like calling it to delete a file,but,and here is muy doubt, the name of the file is a characters string which changes in the program. 
 
For example if my file's name is "hi.txt",and the string is "fname",then I've got:
 
strcat(fname,"hi.txt");
 
How can I delete the file "fname" using system()?
 
ThankS!!:P:P

---

### Post by Bachstelze on 2010-04-27
Why not use unlink()?

---

### Post by indarkness on 2010-04-27
> **Bachstelze said:**
> Why not use unlink()?
 
I don't know that function how could I use it? What library needs?

---

### Post by dwhitney67 on 2010-04-27
> **indarkness said:**
> I don't know that function how could I use it? What library needs?

In regards to unlink(), read the man-page!  As for the library, it is part of the C standard library.

```

#include <unistd.h>
#include <string.h>

int main(int argc, char** argv)
{
   char fname[256];

   snprintf(fname, sizeof(fname) - 1, "%s", "hi.txt");

   unlink(fname);

   return 0;
}

```

---

### Post by lisati on 2010-04-27
> **indarkness said:**
> I don't know that function how could I use it? What library needs?

From [http://www.delorie.com/gnu/docs/glibc/libc_280.html:](http://www.delorie.com/gnu/docs/glibc/libc_280.html:)

> int unlink (const char *filename)

Edit: Thanks, dwhitney67, for the example. Saves me from bothering! :)

---

### Post by Bachstelze on 2010-04-27
man unlink is your friend :) For example a very simple rm command would look like this:

```
#include <errno.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char **argv)
{   
    char *filename;

    if (argc == 2) {
        filename = argv[1];

        if (unlink(filename) == -1) {
            int errsv = errno;
            fprintf(stderr, "Couldn't delete file: %s\n", strerror(errsv));
            return 1;
        }
    } else {
        fprintf(stderr, "Only one argument please!\n");
        return 2;
    }
}

```

---

### Post by MindSz on 2010-04-27
> **indarkness said:**
> HI!!How can I delete the file "fname" using system()?ThankS!!:P:P

You could do this:
```
#include <stdio.h>
#include <string.h>

int main(int argc, char** argv)
{
   char fname[256];
   char command[256];

   strncpy(command, "rm ", sizeof(command)-1);
   strcat(command, fname);
   strcat(command, "hi.txt");

   system(command);

   return 0;
}

```

---

### Post by wmcbrine on 2010-04-27
Don't use system(); that's silly. You add a huge overhead (spawning a shell, and then the rm executable) for no good reason.

I wouldn't use unlink(), either (although it's much better than using system()), since it's only a POSIX function. Use remove(), which is ANSI C (i.e., it's portable).

---

### Post by indarkness on 2010-04-28
Thanks everyone !!!!

---

