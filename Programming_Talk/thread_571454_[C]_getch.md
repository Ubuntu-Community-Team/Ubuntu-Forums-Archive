---
title: "[C] getch"
date: 2007-10-09
forum: Programming Talk
---

### Post by qscomputing on 2007-10-09
Hello,

I'm trying to write a C program using the getch() function. On other platforms I've used (ie Windows), getch() waits for a keypress and then returns it. On Linux, getch() (using the curses library) returns immediately and doesn't seem to give any opportunity at all to enter a character, even by holding down the key.

How can I re-create the same behaviour as the Windows getch()? I'm currently using Ubuntu 7.04.

Thanks.

---

### Post by LaRoza on 2007-10-09
> **qscomputing said:**
> Hello,

How can I re-create the same behaviour as the Windows getch()? I'm currently using Ubuntu 7.04.

Thanks.

getch() isn't standard. This topic came up, and an alternative was given. Look for that post, it is here somewhere.

---

### Post by gnusci on 2007-10-09
Try this code:

[PHP]
#include<stdio.h>

int main(void){
    char buff[1024];
    printf("Write something? ");
    fflush(stdout);
    read(0,buff,1024);
    printf("You've written %s",buff);
    return 0;
}
[/PHP]

---

