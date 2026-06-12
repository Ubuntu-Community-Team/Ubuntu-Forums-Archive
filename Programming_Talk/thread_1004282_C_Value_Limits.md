---
title: "C Value Limits"
date: 2008-12-07
forum: Programming Talk
---

### Post by Masterofpsi on 2008-12-07
I've written a small program in C for my calculator. It's designed to prime factorize a number. It works fine as long as I give it good input. However, it obviously screws up if I give it a number that's too high. I want it to let me know if I do that, but for some reason it won't.

This is what I have:

```

#include <limits.h>
#include <stdio.h>
#include <stdlib.h>

#define LIMITERR 1

int main()
{
    unsigned long long x;
    unsigned long long i = 2;

    printf("Enter the number.\n");
    scanf("%llu", &x);
    if(x == ULLONG_MAX)
    {
        printf("Number is too high.");
        exit(LIMITERR);
    }
   
    while(x != 1)
    {
        if(x % i == 0)
        {
            printf("%llu ", i);
            x /= i;
        }
        else
        {
            i++;
        }  
    }
    printf("\n");
    
    return 0;
}

```

The problem is that it won't exit if x equals ULLONG_MAX. I don't think it's a problem with my limits.h file, because I ran GNU Debugger and figured out the value of x after I entered a ridiculously large number, and when I multiplied all of the output from that session (3 5 17 257 641 65537 6700417) it equaled that number (18446744073709551615).

---

### Post by pp. on 2008-12-07
What, exactly, is the value of ULLONG_MAX? Have you found out what your program does when you enter exactly that value?

---

### Post by Masterofpsi on 2008-12-07
The value of ULLONG_MAX is 18446744073709551615. When I enter a number higher than that, the program automatically reduces the value of x to that number. Interestingly, though, I just compiled it with the "-g" option, and that made it work, but . . . I shouldn't have to do that.

---

### Post by Masterofpsi on 2008-12-07
Just fixed it--optimization level -o2 was causing the problem.

EDIT: Never mind--I don't know what was causing the problem, but it's working with -o2 now anyway, so at least it works.

---

### Post by nvteighen on 2008-12-07
> **Masterofpsi said:**
> The value of ULLONG_MAX is 18446744073709551615. When I enter a number higher than that, the program automatically reduces the value of x to that number. Interestingly, though, I just compiled it with the "-g" option, and that made it work, but . . . I shouldn't have to do that.
Are you sure of that??? If you pass over a variable's limit you should get a segfault... or am I wrong?

---

### Post by dwhitney67 on 2008-12-07
> **nvteighen said:**
> Are you sure of that??? If you pass over a variable's limit you should get a segfault... or am I wrong?

If the code is written properly the value will either get truncated or set to the max value.  The latter occurs with unsigned int, unsigned long, unsigned long long; I would imagine the same occurs for the signed cousins of these data types.

Demonstration of how to read in an unsigned char, which shows truncation in action if the value entered is greater than 255:
[php]
#include <stdio.h>

int main()
{
  unsigned char value = 0;

  printf("Enter an 8-bit value: ");
  scanf("%hhu", &value);

  printf("You entered: %u\n", value);

  return 0;
}
[/php]

---

