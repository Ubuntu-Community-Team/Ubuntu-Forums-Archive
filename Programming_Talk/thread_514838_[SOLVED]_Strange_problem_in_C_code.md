---
title: "[SOLVED] Strange problem in C code"
date: 2007-08-01
forum: Programming Talk
---

### Post by xavier_r on 2007-08-01
> #include <stdio.h>
#include <unistd.h>
#include <string.h>
char * home, * curdir, * sfdir;
char * gethomedir(void);
char * getcurdir(void);
char * getsfdir(void);

main()
{
        home = (char *)gethomedir();
        curdir = (char *)getcurdir();
        sfdir = (char *)getsfdir();

        printf("\nH:[%s] C:[%s] S:[%s]\n",home,curdir,sfdir);
}

char * gethomedir()
{
        char *s;
        s = (char *)getenv("HOME");
        return s;
}

char * getcurdir()
{
        char *t;
        t = (char *)getenv("PWD");
        return t;
}

char * getsfdir()
{
        char *v,*w;
        w = (char *)getenv("HOME");
        v = "/.ScrnFc";
        strcat(w,v);
        return w;
}


As you can understand, it should print HOME DIRECTORY, CURRENT DIRECTORY, and SCR DIRECTORY
But what happens is it prints

SCR DIRECTORY, CURRENT DIRECTORY and SCR DIRECTORY
Where's the bug?

Here:
HOME DIRECTORY = /home/username
SCR DIRECTORY = /home/username/.ScrnFc

---

### Post by PaulFr on 2007-08-01
```
char * getsfdir()
{
char *v,*w;
w = (char *)getenv("HOME");
v = "/.ScrnFc";
strcat(w,v);
return w;
}
``` is the source of your problem - you are concatenating the **"/.ScrnFc"** to the HOME environment variable. Therefore the pointer returned by gethomedir will also print this concatenated value. I think you want to make a copy of the HOME environment variable and concatenate **"/.ScrnFc"** to the **copy**. Something like```
char * getsfdir()
{
    char *v,*w, *copy;
    w = (char *)getenv("HOME");
    copy = malloc(strlen(w) + 16);
    strcpy(copy, w);
    v = "/.ScrnFc";
    strcat(copy,v);
    return copy;
}
```Please add **#include <stdlib.h>** to get definition of malloc, and be sure to free the returned pointer (using **free(sfdir);**) after you have finished using it in main.

---

### Post by moma on 2007-08-01
I think that:
char *getenv(const char * name) saves the string value in an internal (static) char[] buffer. 
[COLOR="Red"]This buffer is reused by all subsequent getenv() or putenv() calls[/COLOR].  That's why, only the value from the last [COLOR="Gray"]latest[/COLOR] getenv() call will be correct.

Read: [http://www.cplusplus.com/reference/clibrary/cstdlib/getenv.html](http://www.cplusplus.com/reference/clibrary/cstdlib/getenv.html)

You must save the value in a new char string. Duplicate the char string with **strdup()** function like this;

char *home = strdup( gethomedir() ) ;
or better
char *home = strdup( getenv("HOME")) ;

....
Free the memory allocated by strdup() before the program quits.
free(home);
-----------------------------

**Note also:**
Your char * getsfdir() function is especially dangerous because you cannot know the length of getenv()'s internal buffer.  Therefore strcat(w,v); is hazardous. 

Again, you must allocate your own char buffer with calloc() or malloc().
Something like this:
 
char *v,*w;
w = (char *)getenv("HOME");
v = "/.ScrnFc";

unsigned int length = strlen(w) + strlen(v) + 1;     
/*    +1 for the final \0 */
mybuff = calloc(1,  length);

strcpy(mybuff, w);
strcat(mybuff, v);

Do not forget to free the memory at the end.
free(mybuff);

---

### Post by xavier_r on 2007-08-01
Thanks :)
Both of your methods worked perfectly

---

