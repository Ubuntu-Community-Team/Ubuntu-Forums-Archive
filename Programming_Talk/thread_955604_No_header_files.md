---
title: "No header files"
date: 2008-10-22
forum: Programming Talk
---

### Post by kulwant on 2008-10-22
I am trying to compile a C source file
but for some reason it doesnt recognise stdio.h or math.h

heres my code:
/* hello.c */
#include <stdio.h>

void main(void)
{
    /* Defining hello() */

    printf("Hello from hello.c!");
}

i get an error:
stdio.h : no such file or directory


i think its because i might not have the header files in my library
can someone tell me how can i get them??

thanks in advance

---

### Post by Rich78 on 2008-10-22
Do you have build-essential installed?

sudo apt-get install build-essential

---

### Post by kulwant on 2008-10-22
LOL
yea that was the problem. i guess i have a lot to learn in linux

---

### Post by Nemooo on 2008-10-22
It looks like you need build-essential as Rich says:

[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

On a sidenote, main should always return an int, so you want it to be:

```
#include <stdio.h>

int main()
{
    /* Some code */

    return 0; /* Tells the OS you're program ended as expected. */
}
```

---

