---
title: "Doubt with declarations of arrays in C"
date: 2015-11-09
forum: Programming Talk
---

### Post by mfvpcrec on 2015-11-09
Hello! , I have a doubt with  declarations of arrays in C.
Why gcc without -Wpedantic  allows compile this program? 

```

#include <stdio.h>

int main (void)
{
        int a;
        int i;
        scanf("%d",&a);
        int array[a];

        for(i=0;i<a;i++)
        {
                array[i]=i;
                printf("%d\n",array[i]);
        }
}


```


 How compiles that? 
The resulting program is interpreted in part? 
The array variable is in the heap?

Thanks!

---

### Post by ofnuts on 2015-11-10
None.... ***int array[a] ***imples that the value of "a" is known at compile time which isn't the case. You have to allocate the array dynamically (see malloc()/calloc() functions).

---

### Post by spjackson on 2015-11-10
Variable length arrays were introduced in C in the C99 standard. Whether this program compiles or not depends on the standard you use. The default is gnu90 which includes some aspects of C99, including variable length arrays. The -pedantic flag causes the compiler to warn about the use of such extensions. If you use -std=c99 or -std=c11 the program compiles cleanly even with -pedantic.

---

### Post by thisisbasil on 2015-11-10
Its a gotcha in gcc. I figured this out in undergrad and used it a few time. You're *not* technically supposed to be able to do this, but gcc allows for it.

---

### Post by mystics on 2015-11-10
> **ofnuts said:**
> None.... ***int array[a] ***imples that the value of "a" is known at compile time which isn't the case. You have to allocate the array dynamically (see malloc()/calloc() functions).

I've confirmed that it compiles and runs as expected. According to GCC documentation, C90 with GCC or C99 in general would allocate the memory at the declaration of the array:

[https://gcc.gnu.org/onlinedocs/gcc/Variable-Length.html](https://gcc.gnu.org/onlinedocs/gcc/Variable-Length.html)

As for being on the heap or stack, I'm not 100% sure, and I haven't been able to find a definite answer. The fact that this appears dynamic and is a replacement for using malloc/calloc makes it appear that it will go on the heap. However, other stuff I've read indicates that this is an exception to the usual rules of the stack of needing to be known at compile time. Hopefully, someone can clear this up.

---

### Post by mfvpcrec on 2015-11-10
Thank you , your answers were very useful

---

### Post by Rocket2DMn on 2015-11-11
According to the almighty Wikipedia, gcc allocates dynamic sized arrays on the stack - [https://en.wikipedia.org/wiki/Variable-length_array#Allocation](https://en.wikipedia.org/wiki/Variable-length_array#Allocation)
Of course, this means that if you try to make it too large, you could get a stack overflow and your program will crash (unlike with malloc where you can check for a NULL return value and possibly handle the situation without failing).

---

