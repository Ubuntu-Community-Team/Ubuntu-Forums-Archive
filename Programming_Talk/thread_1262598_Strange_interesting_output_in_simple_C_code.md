---
title: "Strange interesting output in simple C code"
date: 2009-09-10
forum: Programming Talk
---

### Post by bilol on 2009-09-10
Hi all,
Do you agree that the output of the following code is 

[B]before funny n=7
after funny n=7[/B]

irrespective of the function body of funny()?

```
main()
{
        int arr[]={19,16,122,14,13,12,11},n=7;
        printf("before funny n=%d\n",n);
        funny(arr,n);
        printf("after funny n=%d\n",n);
        return 0;
}

```
However, the output can be

[B]before funny n=7
after funny n=122[/B]

provided the function body of funny() is as below:

```
void funny(int a[],int size)
{
        int i,j,temp;
        for(i=0;i<size-1;i++)
        {
                for(j=0;j<size-i;j++)
                {
                        if(a[j]>a[j+1])
                        {
                                temp=a[j];
                                a[j]=a[j+1];
                                a[j+1]=temp;
                        }
                }
        }

}
```

Can anybody explain the reason?????
And more importantly, is it a drawback of C ?

---

### Post by frenkel on 2009-09-10
One of your loops writes in arr[7], but that one doesn't exist, so it writes to the next int variable behind it (in this case n). So basically, check that funny never writes in arr[7] and your problem is solved.
I believe the stop condition for the second for loop should be j < size - i - 1.

---

### Post by bilol on 2009-09-10
frenkel, you are dead -right.
But my point is , since the variable 'n' is called by value,why should we bother about the function body of funny()? Even if the array size exceeds its limitation within funny(), it should never leave its impact on the variable 'n',which is accessed (not modified) within main().
So, can we come to the conclusion that ,*a variable's value can be change (may be not as per your desire)even if it called "by value", with the help of some specific function call.*

---

### Post by frenkel on 2009-09-10
The array is passed by reference. And as it happens to be, n is right after that array, so arr[7] points to n. C allows you to do this, Java would have cried about "array out of bounds". It has nothing to do with the size variable. You can even remove it and replace it with some hardcoded number. It won't effect the result.

---

### Post by dribeas on 2009-09-10
It is a bug in your application, just as if you just define a pointer, assign it a random value and write there. The fact is that the modified value does not need to be a parameter to the function: you are mistakenly writing in a wrong position in memory.

```

int main()
{
   int array[] = { 1, 2, 3, 4, 5, 6, 7 }, x=0, n=7;
   funny( array, n );
}

```

With the same bug in funny, you would be overwritting the x variable in this case, and that is not even a parameter to the function. The point here is that the code is erroneously fiddling with memory bits that do not belong to the array. The fact that the buffer overrun happened to change a variable that was passed by value is just incidental, and thus passing by value or passing a pointer by value (or equivalently passing by reference in c++) does not matter. You are not modifying the argument, but the real variable.

The fact that you are passing by value in this case is what makes the program not die in a harder way. If you modify as to pass the n parameter (in your original code) by pointer and change size into *size in your funny() function you will be hit hard: after the first time you hit the buffer overrun the loop conditions will be changed for a fun time in undefined behavior land.

BTW, to be precise arrays are not passed by reference, but rather a pointer to the first element of the array is passed by value. While it may seem equivalent, they are slightly different (for example, you can change the pointer received and that won't change anything in the array). C only has pass-by-value semantics, anything else is achieved by passing pointers to variables (by value) instead of passing the real variables.

---

### Post by bilol on 2009-09-10
Thank you all for your valuable comments.
Now from this discussion,we may generate the following swap function,that deals with one "by value" and one "by ref" parameters instead of the conventional both "by ref" parameters.

```
dhiman@dhiman-desktop:~$ cat swap.c
#include<stdio.h>
void funnySwap(int *p,int q)
{
        *(p-1)=*p;*p=q;      
}
main()
{
	int a=5,b=1;
        printf("before swap a=%d b=%d \n",a,b);
        funnySwap(&a,b);
        printf("after swap  a=%d b=%d \n",a,b);
        return 0;
}

dhiman@dhiman-desktop:~$ gcc swap.c
dhiman@dhiman-desktop:~$ ./a.out
before swap a=5 b=1 
after swap  a=1 b=5 

```

Humm...this code only works if a and b are contiguously placed in memory.

---

### Post by frenkel on 2009-09-10
You may never assume that, if you define int a,b; a and b are placed after each other. These kinds of tricks may work on your system, but might not working if the compiler optimizes the thing differently for example.

---

### Post by johnl on 2009-09-10
> **frenkel said:**
> You may never assume that, if you define int a,b; a and b are placed after each other. These kinds of tricks may work on your system, but might not working if the compiler optimizes the thing differently for example.

Exactly.  I would suspect that most compilers here wouldn't even allocate space on the stack for **n**, but would either keep it in a register or treat it as a constant.  It looks like gcc will do this even at the lowest optimization level:
```

~$ gcc -Wall -O1  -c main.c -o main.o
~$ gcc  -Wall -O1  main.o   -o test
~$ ./test
before funny n=7
after funny n=7

```

In this case you are lucky your program doesn't crash, since you are writing to some random area of the stack, and could easily clobber the stack frame.

---

### Post by dribeas on 2009-09-10
Using erroneous code to achieve some intended operation leads inexorably to windows. In the bad sense: tons of code added to the operating system just so application X that uses invalid tricks to its advantage does not break when the user upgrades from one version of windows to the next. But then again, in the open source world, it would be up to you to fix the mistake.

---

