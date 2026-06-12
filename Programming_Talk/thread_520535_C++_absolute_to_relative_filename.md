---
title: "C++: absolute to relative filename"
date: 2007-08-08
forum: Programming Talk
---

### Post by mahy on 2007-08-08
Hello everybody,

i've got an absolute filename, of type char[]. I need to get a relative (local) filename out of it, i.e. only the part AFTER the last "/". I prefer creating a new variable altogether. What's the best and easiest approach? TIA

---

### Post by DMills on 2007-08-08
Untested, but how about the Posix function 

char *basename (char *path) 
 declared in libgen.h. 

Failing that a simple while loop to scan backward thru the string and return a pointer the the last character it hits before finding a / (or the beginning of the string) is almost as trivial.

Regards, Dan.

---

### Post by PaulFr on 2007-08-08
Assuming fullPath and fileName are char[] arrays, ```
char* sp = strrchr(fullPath, '/'); strcpy(fileName, sp+1); /* include <string.h> */
```Of course this is not safe since **fileName** may not be large enough. If that matters, use ```
char* sp = strrchr(fullPath, '/');  /* include <string.h> */
memset(fileName, 0, sizeof(fileName));
strncpy(fileName, sp+1, sizeof(fileName)-1);
``` Do not forget to handle case where sp is NULL (i.e. '/' is not part of the fullPath).

---

### Post by mahy on 2007-08-08
> **DMills said:**
> Untested, but how about the Posix function 

char *basename (char *path) 
 declared in libgen.h. 

Failing that a simple while loop to scan backward thru the string and return a pointer the the last character it hits before finding a / (or the beginning of the string) is almost as trivial.

Regards, Dan.

Thank you very much! I had some initial worries, coz i need to use it on an old Tru64, but it works there as well! :KS

---

