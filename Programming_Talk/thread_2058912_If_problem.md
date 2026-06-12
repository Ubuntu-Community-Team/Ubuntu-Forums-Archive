---
title: "If problem"
date: 2012-09-16
forum: Programming Talk
---

### Post by manudo on 2012-09-16
I have a problem with my code because it doesn't work as I want to.
Here's the code.

```
#include <stdio.h>
#include <stdlib.h>

int main()
{

    int st, nd;
    printf("Hello!\a");
    getchar();
    printf("I'm the manudo's (iMnd) multiplicator 2.0\n");
    getchar();
    system("clear");
    printf("Enter the first number \n");
    scanf("%d", &st);
    printf("0K, now give me the second number \n");
    scanf("%d", &nd);
    if (st || nd == 0) printf("Any product of 0 is \"0\"\n");
    else printf("The result of the multiplication is \"%d\"\n", st*nd);
    return 0;
}
```This code is for the multiplication of two numbers, but there's an if that has to check if any of the numbers that the user entered is 0, if yes, program return a message saying that any product of 0 is 0 and if it's not, return the result message. Well that's it has to do.

The problem is if I put 0 and 2 it shows the result and the else message, and for this case I want to the program shows the else message ONLY.

Here's an screenshot of the result: [http://s13.postimage.org/j024g6yyd/screenshot.png](http://s13.postimage.org/j024g6yyd/screenshot.png)

Please be patient for my English and my "n00bness". Thanks in advance! :D 

*PS: I use Ubuntu 12.04 and Anjuta to compile. Dev-C++ in Windows return with the same problem.*

---

### Post by Bachstelze on 2012-09-16
```
#include <stdio.h>
#include <stdlib.h>

int main(void)
{

    int st, nd;
    printf("Hello!\a");
    getchar();
    printf("I'm the manudo's (iMnd) multiplicator 2.0\n");
    getchar();
    system("clear");
    printf("Enter the first number \n");
    scanf("%d", &st);
    printf("0K, now give me the second number \n");
    scanf("%d", &nd);
    if (st == 0 || nd == 0) {
        printf("Any product of 0 is \"0\"\n");
    } else {
        printf("The result of the multiplication is \"%d\"\n", st*nd);
    }
    return 0;
}
```

---

### Post by manudo on 2012-09-16
Why the void in int main()?

Whatever, really thank you bro.  :)

---

