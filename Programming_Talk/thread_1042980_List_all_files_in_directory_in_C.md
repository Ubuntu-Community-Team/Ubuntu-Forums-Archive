---
title: "List all files in directory in C"
date: 2009-01-18
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-18
How to list any files in any directory with C?
(no need to list folders, just the files)

And maybe get a neat array which contains the filenames?

---

### Post by crazyfuturamanoob on 2009-01-18
This seems to list all files in current directory:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <glob.h>

int main( int argc, char *argv[] )
{
    glob_t data;
    
    switch( glob("*.*", 0, NULL, &data ) )
    {
        case 0:
            break;
        case GLOB_NOSPACE:
            printf( "Out of memory\n" );
            break;
        case GLOB_ABORTED:
            printf( "Reading error\n" );
            break;
        case GLOB_NOMATCH:
            printf( "No files found\n" );
            break;
        default:
            break;
    }
    
    int i;
    for(i=0; i<data.gl_pathc; i++)
    {
        printf( "%s\n", data.gl_pathv[i] );
    }
    
    globfree( &data );
    
    
    return 0;
}

```

But I want to list all files in a subdirectory. How to change working directory?

---

### Post by mdurham on 2009-01-18
glob("sub1/sub2/sub3/*.*", 0, NULL, &data )

---

### Post by Compyx on 2009-01-18
Google for 'dirent.h'.

---

### Post by nvteighen on 2009-01-18
If you have the manpages-dev package installed:

```

man 3 readdir

```

---

### Post by crazyfuturamanoob on 2009-01-18
> **mdurham said:**
> glob("sub1/sub2/sub3/*.*", 0, NULL, &data )
Exactly what I was looking for!

> **Compyx said:**
> Google for 'dirent.h'.
> **nvteighen said:**
> If you have the manpages-dev package installed:

```

man 3 readdir

```

An example I found segfaulted, and debugger said it doesn't work in 64bit. 
I probably missed something or did something wrong but whatever, glob does it with less work.

Wohoo I got 800 posts!

---

### Post by nvteighen on 2009-01-18
> **crazyfuturamanoob said:**
> 
An example I found segfaulted, and debugger said it doesn't work in 64bit. 
I probably missed something or did something wrong but whatever, glob does it with less work.


You surely missed something, as readdir() involves the use of a pointer to a directory "class"/structure created by opendir(). It's actually similar to fopen() and such.

EDIT:
An example that doesn't segfault nor leaks memory. It lists the elements on / (root directory).

```

#include <stdio.h>

#include <sys/types.h>
#include <dirent.h>

int main(void)
{
    DIR *mydir = opendir("/");

    struct dirent *entry = NULL;
    
    while((entry = readdir(mydir))) /* If we get EOF, the expression is 0 and
                                     * the loop stops. */
    {
        printf("%s\n", entry->d_name);
    }

    closedir(mydir);

    return 0;
}

```

---

