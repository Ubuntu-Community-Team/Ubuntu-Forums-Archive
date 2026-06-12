---
title: "get ctrl + key in C"
date: 2011-12-07
forum: Programming Talk
---

### Post by chuchi on 2011-12-07
Hi Friends!!

I am developing a command-line user interface in C using readline, and I have to add a function so that when the user press a shortcut, one editor is opened. For example CTRL + s. 

Is there anyway to get CTRL + s in linux as a signal?? so that a function is launched and open the editor??

Thank you very much!

---

### Post by Bachstelze on 2011-12-07
```
#include <stdio.h>

int main(void)
{
        for (;;) {
                printf("Enter a Ctrl character, then Return: ");
                int n = getchar();
                if (n == EOF) {
                        break;
                }
                n = n-1+'A';
                printf("Entered: Ctrl+%c\n", n);

                /* Flush input buffer */
                while ((n = getchar()) != '\n' && n != EOF)
                        ;
        }
}

```

Not all of them will work, depending on your terminal.

---

### Post by slavik on 2011-12-07
> **Bachstelze said:**
> ```
#include <stdio.h>

int main(void)
{
        for (;;) {
                printf("Enter a Ctrl character, then Return: ");
                int n = getchar();
                if (n == EOF) {
                        break;
                }
                n = n-1+'A';
                printf("Entered: Ctrl+%c\n", n);

                /* Flush input buffer */
                while ((n = getchar()) != '\n' && n != EOF)
                        ;
        }
}

```

Not all of them will work, depending on your terminal.
are you sure that -1 is needed?

ctrl+a == null, no?

---

### Post by Bachstelze on 2011-12-08
No, Ctrl+A is 1. null is Ctrl+@ (and it also works):

```
firas@av104151 ~ % cat test.c
#include <stdio.h>

int main(void)
{
        for (;;) {
                printf("Enter a Ctrl character, then Return: ");
                int n = getchar();
                if (n == EOF) {
                        break;
                }
                printf("Entered: Ctrl+%c, ASCII code %d\n", n-1+'A', n);

                /* Flush input buffer */
                while ((n = getchar()) != '\n' && n != EOF)
                        ;
        }
}
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@av104151 ~ % ./test
Enter a Ctrl character, then Return: ^A
Entered: Ctrl+A, ASCII code 1
Enter a Ctrl character, then Return: ^@
Entered: Ctrl+@, ASCII code 0

```

---

### Post by chuchi on 2011-12-09
Hi friends!! thank you all very much!!!

I found the solution by myself. All I have to do is call to

```

    rl_bind_key(0x05,myfunction); // ctrl+e will launch myfunction

```

Which will launch myfunction when ctrl + e is pressed.

---

