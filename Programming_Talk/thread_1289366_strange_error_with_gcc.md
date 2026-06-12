---
title: "strange error with gcc"
date: 2009-10-12
forum: Programming Talk
---

### Post by swappo1 on 2009-10-12
Hello,

I am working on a program with multiple header files.  I ended up trying to track down a bug and in doing so I recopied one of my header and source files from file.h and file.c to file1.h and file1.c.  However, I forgot to change #ifndef _FILE_H_ and #define _FILE_H_ to reflect the added 1.  I was getting this compiler error: main.c:8: error: expected specifier-qualifier-list before ‘FileInfo’.  I ended up starting a third file, file2.h and file2.c with the correct #ifndef and #define statements before I figured out the problem.  Everything worked ok with this third file and the program compiled fine.  That's when I realized what the problem had been.  I went back and deleted the 2 in the #ifndef and #define statements to make sure this was what was causing the problem and I then got the compiler error again.  I changed the #ifndef and #define statements back to the correct statements and recompiled but I can't get rid of the error.  I also tried deleting the .o files thinking this might help as well as re-saving everything so everything is re-compiled.  Any ideas as to what is going on and why I can't get this to re-compile after files are corrected?

---

### Post by swappo1 on 2009-10-12
Ok, I think if figured the problem out.  I put a #include file4.h in main.c. 
main.c with my structure
```
#include "file4.h"
#include "signals1.h"
#include <gtk/gtk.h>

typedef struct
{
	MainWin *mw;
	FileInfo *fi;
}PublicData;
```

The structure for MainWin *mw is in window.h and the structure for FileInfo *fi is in file4.h.  I don't understand why I need to #include file4.h but not window.h.  I have never had an compiler errors with MainWin.  Anyway, It works now.

---

