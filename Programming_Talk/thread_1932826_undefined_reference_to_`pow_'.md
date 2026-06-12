---
title: "undefined reference to `pow '"
date: 2012-02-28
forum: Programming Talk
---

### Post by bunny1 on 2012-02-28
Can anyone please tell me why the following code gives errors ? Iv tried changing the code but got nowhere. Im on Xubuntu with GCC.

#include <math.h>
#include <stdio.h>

int main()
{
	int i=2;

     printf( "%f\n", pow(i,2) );/*    This fails if 2 is any higher ?    */ 
  return 0;
}




The error is..........

In function `main':
test1.c: (.text+0x23): undefined reference to `pow'
collect2: ld returned 1 exit status

---

### Post by Hetepeperfan on 2012-02-28
Did you link to the math library?

compile as:

```
gcc test.c -o your_program_name -lm
```this should help. the -lm switch tell gcc it should link to the math library this is where the function is defined. without the -lm switch gcc doesn't know how to put in the pow() function in you program.

kind regards,

Maarten

---

### Post by bunny1 on 2012-02-28
> **Hetepeperfan said:**
> Did you link to the math library?

compile as:

```
gcc test.c -o your_program_name -lm
```this should help. the -lm switch tell gcc it should link to the math library this is where the function is defined. without the -lm switch gcc doesn't know how to put in the pow() function in you program.

kind regards,

Maarten

Thank you so much. That work like a dream.

---

### Post by cgroza on 2012-02-28
> **bunny1 said:**
> Thank you so much. That work like a dream.
Then mark the thread as [SOLVED]. :D

---

