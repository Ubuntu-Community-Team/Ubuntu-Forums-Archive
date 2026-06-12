---
title: "Question about &quot;fgets&quot; and buffer sizes"
date: 2014-03-18
forum: Programming Talk
---

### Post by donsy on 2014-03-18
According to my copy of K&R the library function "fgets" has the following prototype and, at most, maxline-1 characters will be read:
```
 char *fgets(char *line, int maxline, FILE *fp) 
```

Then why does the following program work at all? First, BUFFSIZE is only 2 in malloc, and second, the fgets function is returning the complete line length of all the lines even when maxline (BUFFSIZE) is only 2.

Here is the output of the program which reads and prints itself:
```

$ ./a.out
/*******************
* Program: popen.c *  
*******************/
#include <stdio.h>
#include <stdlib.h>

// BUFFSIZE changed for debugging only! Normally would be 256.
#define  BUFFSIZE  2

int main() 
{
    FILE *in;
    char *buff = malloc( BUFFSIZE * (sizeof(char)) );

    if(!(in = popen("cat popen.c", "r"))){
        exit(1);
    }

    while(fgets(buff, BUFFSIZE, in)!=NULL){
        printf("%s", buff);
    }

    pclose(in);
    free(buff);    
    return 0;
}

```

---

### Post by spjackson on 2014-03-18
> **donsy said:**
> 
Then why does the following program work at all? First, BUFFSIZE is only 2 in malloc, and second, the fgets function is returning the complete line length of all the lines even when maxline (BUFFSIZE) is only 2.

It works because each call to fgets in your program reads a single character (BUFFSIZE-1 is 1). Perhaps you are expecting the rest of the line to be discarded, but that isn't what fgets does. If you add an extra character after each print you will see this extra character after every character in the file.
```

    while(fgets(buff, BUFFSIZE, in)!=NULL){
        printf("%s.", buff);
    }

```

---

### Post by donsy on 2014-03-18
Thanks, I guess I got too hung up on the "line" part of the "maxline" in the prototype.

---

### Post by squakie on 2014-03-18
Easy to demostrate as well - put a \n at the end of the printf.

---

