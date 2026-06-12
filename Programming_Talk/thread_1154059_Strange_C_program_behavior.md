---
title: "Strange C program behavior"
date: 2009-05-09
forum: Programming Talk
---

### Post by namaku0 on 2009-05-09
Look at this code, this is a matrix multiplication
program. Also notice the commented line.

```
#include <stdio.h>

int main()
{
        int acol = 3;
        int arow = 2;
        int a[arow][acol];

        int bcol = 1;
        int brow = acol;
        int b[brow][bcol];

        int rcol = bcol;
        int rrow = arow;
        int r[rrow][rcol];

        int i, j, k;

        a[0][0] = 1;
        a[0][1] = 2;
        a[0][2] = 3;
        a[1][0] = 4;
        a[1][1] = 5;
        a[1][2] = 6;

        b[0][0] = 9;
        b[1][0] = 8;
        b[2][0] = 7;

/*        printf("%i %i", a[0][0], b[0][0]); */

        for (i = 0; i < arow; i++) {
                for (j = 0; j < bcol; j++) {
                        for (k = 0; k < acol; k++) {
                                r[i][j] += a[i][k] * b[k][j];
                        }
                }
        }

        for (i = 0; i < arow; i++) {
                printf(" \n");
                for (j = 0; j < bcol; j++) {
                        printf("%i ", r[i][j]);
                }
        }

        printf("\n");
        return 0;
}
```


The problem is, when I run this program with the
line commented it gives me a wrong result. But if
I remove the comment it will give me the correct
result (with additional "1 9" line of course).

```
user@desktop:~$ gcc mm.c -o mm && ./mm

-1207884624 
-1207984010 
user@desktop:~$ gcc mm.c -o mm && ./mm
1 9
46 
118 
user@desktop:~$ 

```

---

### Post by Bichromat on 2009-05-09
You did not initialize r, therefore it contains whatever garbage was in the memory your program allocated for it. Adding the printf instruction changed the position of the variable in your memory to a place where there was nothing. You got the right result by chance.

---

### Post by Arndt on 2009-05-09
> **Bichromat said:**
> You did not initialize r, therefore it contains whatever garbage was in the memory your program allocated for it. Adding the printf instruction changed the position of the variable in your memory to a place where there was nothing. You got the right result by chance.

A good tool to catch these things is 'valgrind'.

---

