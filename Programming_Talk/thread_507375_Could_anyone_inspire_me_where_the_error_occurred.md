---
title: "Could anyone inspire me where the error occurred"
date: 2007-07-22
forum: Programming Talk
---

### Post by koala114 on 2007-07-22
[PHP]
/* Illustrates the modulus operator */
/* Input a number of seconds, and converts to hours, minutes, and seconds */

#include <stdio.h>

/* Define constants */

#define SECS_PER_MIN 60;
#define SECS_PER_HOUR 3600;

unsigned seconds, minutes, hours, secs_left, mins_left;

main()
{
    /* Input the number of seconds */
    printf("Enter number of seconds (< 65000): ");
    scanf("%d", &seconds);

    hours = seconds / SECS_PER_HOUR;
    minutes = seconds / SECS_PER_MIN;
    printf("%d  %d = %d\n", seconds, SECS_PER_MIN, minutes);
    printf("testing\n");
    mins_left = minutes % SECS_PER_MIN;
    secs_left = seconds % SECS_PER_MIN;

    printf("%u seconds is equal to ", seconds);
    printf("%u h, %u m, and %u s\n", hours, mins_left, secs_left);

    return 0;
}

[/PHP]
When I compiled this file get the message 

root@ford:~/Learning/21Days# gcc seconds.c
seconds.c: In function `main':
seconds.c:21: error: syntax error before ';' token

---

### Post by hod139 on 2007-07-22
You need to declare main to return an int.

```

int main()

```Also, this line is going to cause you some trouble:
```

printf("%d  %d = %d\n", seconds, SECS_PER_MIN, minutes);

```because SECS_PER_MIN is not #defined correctly.

[B]Edit: fixed my post after PaulFr found the real problem with the #define.
[/B]

---

### Post by tgalati4 on 2007-07-22
Beat me to it.  It compiles and runs without the offending printf statement.

---

### Post by PaulFr on 2007-07-22
I do not think you have a problem with the printf statement because is a #define - you have a problem because the define states ```
#define SECS_PER_MIN 60;
``` Note the **extra semi-colon** at the end of the code. When the C pre-processor runs, it will replace SECS_PER_MIN with **60;** inside the printf leading to the following line:```
printf("%d  %d = %d\n", seconds, 60;, minutes);
``` - the compiler will reject this obviously :-)The code will work with ```
#define SECS_PER_MIN      60
```, i.e. without that semi-colon.

---

### Post by Mr. C. on 2007-07-22
Remember that #defines are literal macro substitutions.  Everything after the token is used as the substitution:
```

#define TOKEN    *Stuff to end of line...*
```

MrC

---

### Post by koala114 on 2007-07-22
Great!!! I got it, thinks guys for your detailed explanation:guitar:

---

