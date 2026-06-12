---
title: "collect2: ld returned 1 exit status     what the heck???"
date: 2009-06-22
forum: Programming Talk
---

### Post by helstreak on 2009-06-22
i have this little test program that simply finds prime numbers but i'm getting the titled error message.  The full error message is:

gcc prime.c -o prime

/tmp/ccQ0TGKV.o(.text+0x7e): In function `isPrime':
: undefined reference to `sqrt'
collect2: ld returned 1 exit status

The program that I am compiling is:

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int isPrime(int num);

int main() {

        int i;
        for(i=2; i<=10; i++) {
                if(isPrime(i)) {
                        printf("%d is prime", i);
                }
        }
}

int isPrime(int num) {
        int i, sqrtNum;
        if(num % 2 == 0) {
                return 0;
        }

        sqrtNum = (int) sqrt(num);
        for(i=3; i<=sqrtNum; i+=2) {
                if(num % i == 0) {
                        return 0;
                }
        }
        return 1;
}

I have no clue why this does not work because I can use sqrt in the main function but outside of the main it does not compile.

Thanks for your help

---

### Post by Can+~ on 2009-06-22
gcc -lm prime.c -o prime

---

### Post by helstreak on 2009-06-22
> **Can+~ said:**
> gcc -lm prime.c -o prime

what's -lm again? :)

---

### Post by Can+~ on 2009-06-22
> **helstreak said:**
> what's -lm again? :)

Add the math library to the linker's paths.

---

