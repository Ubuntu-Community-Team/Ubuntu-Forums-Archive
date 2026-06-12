---
title: "C strange strlen behaviour in loop"
date: 2008-02-27
forum: Programming Talk
---

### Post by Cene on 2008-02-27
Hello. 

Imagine I have a function like this:
```

void cmd_topic(int sock, char *from, char **args, int arg_count, int own) {
  if (own == 1) {
    char *tmp = NULL;
    int len = 0;
    for(i = 4; i < arg_count; i++)
      len += (strlen(args[i]) + 1);

#ifdef DEBUG
    printf("%i %i\n",len, (strlen(args[4]) + 1));
#endif

    tmp = malloc(len * sizeof(char) + 1);

    for(i = 4; i < arg_count; i++)
      strcat(tmp, args[i]);
#ifdef DEBUG
    printf("%s\n", tmp);
#endif
    sendl(sock, "TOPIC %s :%s", from, tmp);
  }
  else
    NOAUTH;
}

```
The strange thing here is that the "len" variable stays at zero, so I cannot malloc enough space to tmp which leads to unwanted behaviour.
Upon running running the program, when printing len (on the DEBUG part) I get 0, but (strlen(args[4]) + 1) returns the correct value, as does strlen on any other args[] value if I specify the number myself.

Anyone care to enlighten me why is this happening?

Edit: Solved. Don't know what was causing that.. I rewrote parts of the code and it worked.

---

### Post by WW on 2008-02-27
Is the arg_count argument getting the correct value when the function is called? Is it greater than 4?

There is another unrelated potential bug in your code.  malloc() does not initialize the memory that it allocates, so it may contain garbage.  strcat expects a null-terminated string.  Either use calloc to allocate tmp, or explicitly set the first byte to null (i.e. something like **tmp[0]=(char) 0;** after the malloc statement.

---

### Post by Cene on 2008-02-27
> **WW said:**
> Is the arg_count argument getting the correct value when the function is called? Is it greater than 4?
Yes. In every possible case it is at least 5.

> There is another unrelated potential bug in your code.  malloc() does not initialize the memory that it allocates, so it may contain garbage.  strcat expects a null-terminated string.  Either use calloc to allocate tmp, or explicitly set the first byte to null (i.e. something like **tmp[0]=(char) 0;** after the malloc statement.
Ok, done. Now the tmp string strcat forms is empty.. And "len" still stays at zero. Thanks for the tip though, haven't played much with (m|l)alloc even though I'm pretty familiar with many other aspects of C.

---

### Post by WW on 2008-02-27
Hmmm... seems to work for me...

atest.c:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void cmd_topic(int sock, char *from, char **args, int arg_count, int own)
{
if (own == 1)
    {
    int i;
    char *tmp;
    int len = 0;
    for(i = 4; i < arg_count; i++)
        len += (strlen(args[i]) + 1);
    printf("%i %li\n",len, (strlen(args[4]) + 1));
    tmp = malloc(len * sizeof(char) + 1);
    *tmp = '\0';
    for(i = 4; i < arg_count; i++)
        strcat(tmp, args[i]);
    printf("%s\n", tmp);
    free(tmp);
    }
}


int main(int arc, char *argv[])
{
char *a[] = {"zero","one","two","three","four","five","six","seven"};
    
cmd_topic(0,"",a,8,1);

return 0;
}

```

Compile and run:
> $ gcc -Wall atest.c -o atest
$ ./atest
20 5
fourfivesixseven
$ 


---

