---
title: "C - float data type and void main()"
date: 2009-08-23
forum: Programming Talk
---

### Post by Nugget_Mon on 2009-08-23
Ubuntu 9.04
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

Hello,
I have a couple of noob questions. I was following the C tutorial from Dev-C++ 4.9.9.2 (PortableApps) and ran into a couple of errors. I then switched over to GCC and got the same errors.

```

#include <stdio.h>

void main()
{
	float a=10/3;
	printf("a=%f\n\n",a);
	return 0;
}


```

The terminal output is :

> 
~/My_C_Programs$ gcc -o program1 program1.c
program1.c: In function ‘main’:
program1.c:7: warning: ‘return’ with a value, in function returning void
program1.c:4: warning: return type of ‘main’ is not ‘int’

~/My_C_Programs$ ./program1
a=3.000000



If I change the code as follows there are no errors and the output is correct:
```

#include <stdio.h>

int main() // changed void to int
{
	float a=10.0/3.0; //added decimals to integers
	printf("a=%f\n\n",a);
	return 0;
}


```

> 
~/My_C_Programs$ gcc -o program1 program1.c

~/My_C_Programs$ ./program1
a=3.333333



At first I thought the "return 0;" was the issue with the "void main()" error, but when removed it the error persists.
The error with the float variable. I got the idea to add the decimals from my TI-89. But if I have a more complicated code, how do I ensure that if my code ends up dividing two integers that I actually get a float answer?

Thank you,
Mon

---

### Post by MindSz on 2009-08-23
In C, when you divide two integers it gives you a truncated int value as you saw in your code.

A way to avoid this with int variables is to type-cast one of the variables (If one of the variables is a float, then the output will be a float)

```
#include <stdlib.h>
#include <stdio.h>

int maint(){
  int aNum = 3;
  int bNum = 6;

  printf("Truncated Output: %d\n", aNum/bNum);
  printf("Float Output %f\n", (float)aNum/bNum);

  return 0;
}
```

---

### Post by pepperphd on 2009-08-23
You can ensure that you get a float answer like this:

```
float a = (float)b/c;
```
This is called a typecast. 
Also, although C will let you compile a program with a void main, C++ will not. You should get into the habit of using int main()'s.

---

### Post by lensman3 on 2009-08-23
You can also initialize a float value using:

  float aNum = 3.0f;
  float bNum = 6.0f;

There is also a L for long and but for double/float number it is sometimes easier just to exponential notation like: 1.0E+308 .

Recall that the above assignments are generally done during compilation so there is no run-time penalty for casting the value to another type.  In this case the compiler has already do the conversion before the execution. That was why your 10/3 was already wrong.  The 10/3 was done  and THEN cast to a float.  You need the decimal  point to force the math to floating point math

---

### Post by Nugget_Mon on 2009-08-24
> **lensman3 said:**
> That was why your 10/3 was already wrong.  The 10/3 was done  and THEN cast to a float.  You need the decimal  point to force the math to floating point math


Ah, thank you. I was assuming the float declaration determined the operation, not as a typecast after the operation was complete.

Thank you, 
Mon

---

