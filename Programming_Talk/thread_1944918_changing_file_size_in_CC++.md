---
title: "changing file size in C/C++"
date: 2012-03-22
forum: Programming Talk
---

### Post by UncleRoy on 2012-03-22
In Windows one used (int handle) and chsize(handle,newsize) to either truncate or extend the size of a file.
Now in Ubuntu / Unix one uses (FILE* fp) for most IO. What is the equivalent FILE* function for chsize ?

---

### Post by CynicRus on 2012-03-22
```
**#include <unistd.h>**  
 **#include <sys/types.h>**   **int truncate(const char ****path***, off_t ***length***);**  
 **int ftruncate(int ***fd***, off_t ***length***);**    

```

---

### Post by Bachstelze on 2012-03-22
Note that if you want to use ftruncate(), you must open the file with open(), not fopen(). (If the file is already opened with fopen(), you can use fileno() to get the file descriptor associated with it without open()ing it again.)

---

### Post by UncleRoy on 2012-03-22
Many thanks. It worked with open (which i didn't know was available in ubuntu and i prefer anyway).
But , please (out of interest) what is the exact syntax for getting a handle(fd) out of a FILE*(fp) 

File* fp = fOpen (... etc )
int fd = fp->fileno(); // ?? compiler error

---

### Post by Bachstelze on 2012-03-22
FILE *fp = fopen(...);
int fd = fileno(fp);

---

### Post by UncleRoy on 2012-03-22
Touche. Clearly that is the last word.

---

### Post by ofnuts on 2012-03-22
> **Bachstelze said:**
> Note that if you want to use ftruncate(), you must open the file with open(), not fopen(). (If the file is already opened with fopen(), you can use fileno() to get the file descriptor associated with it without open()ing it again.)
Wouldn't that be dangerous to truncate the file unbeknownst to the code that uses the fopen()'ed descriptor?

---

### Post by Bachstelze on 2012-03-22
> **ofnuts said:**
> Wouldn't that be dangerous to truncate the file unbeknownst to the code that uses the fopen()'ed descriptor?

I can't see why, unless the program is multithreaded and one thread truncates the file while the other is in the middle of a fread/fwrite operation maybe. I suspect that a subsequent call to fread or fwrite would simply behave as it normally does when end-of-file is reached.

---

### Post by ofnuts on 2012-03-22
> **Bachstelze said:**
> I can't see why, unless the program is multithreaded and one thread truncates the file while the other is in the middle of a fread/fwrite operation maybe. I suspect that a subsequent call to fread or fwrite would simply behave as it normally does when end-of-file is reached.My question is really if
```

    char *abcdef="abcdef";
    char *ghijkl="ghijkl";

    FILE* f=fopen("data","w");
    fwrite(abcdef,1,strlen(abcdef),f);
//    fflush(f);
    ftruncate(fileno(f),3))
    fwrite(ghijkl,1,strlen(ghijkl),f);
    fclose(f);

```
creates a file with "abcdefghijkl", "abc___ghijkl" (with whatever (all zeroes?) in the "_") , or "abcghijkl". It turns out that  it creates "abcdefghijkl" without the fflush(), and "abcghijkl" with the fflush() . So it's not exactly the problem I expected (write pointer past the current end of file) but truncating an fopen()ed file still requires some care.

---

