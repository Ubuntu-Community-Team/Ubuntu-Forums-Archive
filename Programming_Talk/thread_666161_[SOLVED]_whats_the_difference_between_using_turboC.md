---
title: "[SOLVED] whats the difference between using turboC and gcc"
date: 2008-01-13
forum: Programming Talk
---

### Post by Harish Prabhu on 2008-01-13
i wrote the following C code and tried to run it but its not even getting compiled

#include<stdio.h>
main ()
{char arr[6],int i;
for (i=0;i<4;i=i+1)
arr[i]='$';
arr[i]='/0';
for (i=0;i<4;i=i+1)
printf("element#%dis%c/n",i+1,arr[i]);
getch();
}

When i wrote the same code in TurboC,it works perfectly
why is it so?
Plealse help me:(

---

### Post by nrs on 2008-01-13
Turbo C is like, how old? I'm pretty sure it pre-dates C89. If that is valid code, even for  < C89, it isn't anymore.

---

### Post by nrs on 2008-01-13
[PHP]#include<stdio.h>
int main ()
{
  char arr[6]; int i;
  
  for (i=0;i<4;i=i+1)
    arr[i]='$';
  arr[i]='\0';
  
  for (i=0;i<4;i=i+1)
    printf("element#%dis%c\n",i+1,arr[i]);
  
  getchar();
}[/PHP]
minimum correction, just compiles without warning.

---

### Post by Kadrus on 2008-01-13
> **Harish Prabhu said:**
> i wrote the following C code and tried to run it but its not even getting compiled

#include<stdio.h>
main ()
{char arr[6],int i;
for (i=0;i<4;i=i+1)
arr[i]='$';
arr[i]='/0';
for (i=0;i<4;i=i+1)
printf("element#%dis%c/n",i+1,arr[i]);
getch();
}

When i wrote the same code in TurboC,it works perfectly
why is it so?
Plealse help me:(

Your code is badly organised,and instead of writing '/0' it should be '\0' and instead of /n..you should write \n..and getch(); is a unrecognised function by the GNU C compiler..so getchar(); instead..

---

### Post by Compyx on 2008-01-13
If the original code compiled on TurboC then TurboC is seriously broken.

Also, the 'corrected' version still doesn't compile without warnings:
```

$ gcc -Wall -Wextra -pedantic -ansi -g crap2.c
crap2.c: In function `main':
crap2.c:14: warning: control reaches end of non-void function

```

To the OP: I assume this is one of your first C-programs? Usually when incrementing a value by one, you would write 'i++;' or '++i;', not ' i = i + 1'.
Proper indentation and a little use of whitespace  makes the code a lot clearer to read and easier to debug.

---

