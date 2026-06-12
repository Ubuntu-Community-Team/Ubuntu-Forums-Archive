---
title: "Input string in gcc"
date: 2007-02-06
forum: Programming Talk
---

### Post by konst88 on 2007-02-06
Hello.
I need help with programming in c under linux(gcc)
I am using the gets(str) function in order to get input string.
But sometimes it skips this because of a buffer.
In windows, i used the flushall() function in order to clear the buffer, but it seemes not be recognized by gcc...
So, how do i get input string, which may contain spaces in c?

---

### Post by lnostdal on 2007-02-06
never ever use gets, to understand why see man 3 gets

you do not mention what you are trying to read in, so i'll just assume you want to read a whole line from standard input .. try something like this:

```

#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>

int main(){
  char* line = NULL;
  size_t len = 0;
  size_t read = 0;

  while((read = getline(&line, &len, stdin)) != -1){
    printf("Read line of %u characters: %s\n", read, line);
  }
  
  if(line)
    free(line);
  
  return(0);
}

```

---

### Post by konst88 on 2007-02-06
Thx for the reply.
First of all, man 3 gets doesnt work..
Second, I would like to get a little explanation about this program.
How it can exit the loop? It seems this function never returns something below 1...
What is the purpose of the len variable? why it contains zero, and you send the address of it.
Why do you free the line variable?
Is this C and not C++?
Thx.

---

### Post by lnostdal on 2007-02-06
> **konst88 said:**
> Thx for the reply.
First of all, man 3 gets doesnt work..


you're probably missing some man-pages:
```
sudo aptitude install manpages-dev
man 3 gets

```


> How it can exit the loop? 
```

#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(){
  char* line = NULL;
  size_t len = 0;
  size_t read = 0;

  while((read = getline(&line, &len, stdin)) != -1){
    printf("Read line of %u characters: %s\n", read, line);
    if(strncmp(line, "end\n", 4) == 0)
      break;
  }
  
  if(line)
    free(line);
  
  return(0);
}

```


> 
It seems this function never returns something below 1...
What is the purpose of the len variable? why it contains zero, and you send the address of it.
Why do you free the line variable?


man 3 getline provides information about these things


> 
Is this C and not C++?


This is C.

---

### Post by konst88 on 2007-02-06
OK, thx for the explanations, i think i got it.
The problem is, that this function works only on unix...
I need something that works on both windows and linux, like the gets function, with all the the security problems, which i don't care about them now, it is just for school..
How can I make the gets function always work? Is there something similar to flushall()?

---

### Post by konst88 on 2007-02-07
Update: Searching in the man pages you installed me, I found this function:
__fpurge(stdin);
Which is doing exactly what i needed.
Thx for helping, bye.

---

### Post by loneowais on 2009-05-13
Now you can use all the Turbo C (conio.h) functions in GCC. Using the gconio.h header file.
> 
wget [http://www.wence.vandermeersch.org/gconio/gconio.h](http://www.wence.vandermeersch.org/gconio/gconio.h) && sudo cp gconio.h /usr/include


---

### Post by Zugzwang on 2009-05-13
> **loneowais said:**
> Now you can use all the Turbo C (conio.h) functions in GCC. Using the gconio.h header file.

Interesting project. Since you might be the developer, I mention some bugs here. If not, someone could package it for Ubuntu (since its GPL). However, it has some bugs, but these are relatively easy to fix.

First of all, the implementation and declaration are not separated. This leads to multiple definition when compiling a project containing several .c files. Example

test1.c:
```

#include "gconio.h"

int hello() {
    return 4;
}

```

test2.c:
```

#include "gconio.h"

int main() {
    return 4;
}

```

compiling with:
```

gcc test1.c test2.c

```

You get the problem that all the methods are multiply defined. One easy way to fix it is by declaring them all to be inlined (not a nice way of fixing it, but since all methods are relatively small, this should be ok).

Second, in the GCC version, the user gets a lot of warnings that a void() function returns some value, for example:
```

void gotoxy (int x, int y)
{
#ifdef __GNUC__
    if ( (x <= get_screen_columns()) && (y <= get_screen_rows()) )
        printf("\033[%d;%dH", y, x);
    else
        return -1;
#endif
#ifdef WIN32
    ...
#endif
}

```

The "return -1" statement does not make sense for "void gotoxy()".

Finally, never one should require installing something to "/usr/include" if it is not packaged. The right position to put manually installed stuff would be "/usr/local/include", or, even better, locally in the projects using it.

---

### Post by JackKDBA on 2009-12-12
Could one put a correct version of **gconio.h**, please?

---

### Post by PmDematagoda on 2009-12-12
Please open a new thread about this issue if you must instead of resurrecting threads more than a year old.

Thread closed.

---

