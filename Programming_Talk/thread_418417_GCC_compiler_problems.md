---
title: "GCC compiler problems"
date: 2007-04-22
forum: Programming Talk
---

### Post by Nunyah on 2007-04-22
Hello, I've recently started out with the C language and I'm currently learning it from [http://beej.us/guide/bgc/]("http://beej.us/guide/bgc/") and I got a  question with a error message produced by GCC on my Ubuntu 7.04 box.

Consider this code from a tutorial at it's site:
[PHP]
#include <stdio.h>

main()
{
        int num = 10;

        for(int i=0;i<num;i++) {
                printf("Number is %d.\n", i);
        }
}
[/PHP]

Results in the following error message when compiling with GCC:
> error.c: In function main:
error.c:7: error: for loop initial declaration used outside C99 mode


If i declare the i variable before the for loop, it will compile as it should:
[PHP]#include <stdio.h>

main()
{
        int num = 10;
        int i;
        for(i=0;i<num;i++) {
                printf("Number is %d.\n", i);
        }
}
[/PHP]

Is it something wrong with my GCC settings since the first one won't work?

---

### Post by duff on 2007-04-22
Like the warning says, that's a C99 extension.  Compiling with "-std=c99" should get rid of it.

---

### Post by Nunyah on 2007-04-22
> gcc error.c -o -std=c99 error
gcc: error: No such file or directory
error.c: In function âmainâ:
error.c:6: error: âforâ loop initial declaration used outside C99 mode


Can I save std=c99 so I won't have to pass it as a parameter all the time?

---

### Post by DoktorSeven on 2007-04-22
gcc -std=c99 -o error error.c

And no, you'll have to declare std=c99 every time.

---

### Post by Nunyah on 2007-04-22
Thank you both.

---

