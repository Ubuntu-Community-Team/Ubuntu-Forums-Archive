---
title: "typecasting for calculating sizeof int"
date: 2011-06-17
forum: Programming Talk
---

### Post by jamesbon on 2011-06-17
This is a C interview question

If you are not having a sizeof operator in C, how will you get to know the size of an int ?
One of the approach is 

```
#include<stdio.h>
int main ()
{
int i,a[2];
**i=(char *)(a+1) -(char *)(a);**
printf("%d\n",i);
}

```

Another approach is to 
have 
```
#include <stdio.h>

int size()
{
  int a = 1;
  int size = 1;
  while(a<<=1)
    size++;
  return size;
}

int main(int argc, char** argv)
{
  printf("Size of int: %d\n", size());
  return 0;  
} 
```

approach 2 is clear to me.
But approach 1 where the typecasting is done 
that part is not clear to me.

How does that part give and why can't int * be used instead of char * at that place?

---

### Post by dwhitney67 on 2011-06-17
With approach #1, all that is being done is pointer arithmetic.  Two ints, via the declaration of an array are declared.  If you subtract the address of the beginning of the array from the second element of the array, the result should tell you the size of the int.

Consider this, where the addresses are made up:
```

       +-------------+
1000   |    1234     |     <------ a[0]
       +-------------+
1004   |    8765     |     <------ a[1]
       +-------------+

```

If you take the address of a[1], which is 1004, and subtract the address of a[0], which is 1000, then you are left with the result of 4.  This would represent the size in bytes of one int.

Note the values 1234 and 8765 are merely shown for illustrative purposes for the values at a[0] and a[1], respectively.

---

### Post by Arndt on 2011-06-17
> **jamesbon said:**
> 
[...] why can't int * be used instead of char * at that place?

The reason we must cast the pointers to (char *) before taking the difference between them, is that pointer arithmetic in C/C++ always takes the size of the items pointed to into account. This simple relation always holds when a is a pointer: a[i] = *(a+i)

That means that taking the difference (a+j)-(a+i) = j-i is the same as the difference between the addresses of a[i] and a[j]. This is different for ints and chars.

---

### Post by ziekfiguur on 2011-06-17
Edit: oh wait, im wrong, never mind.

---

### Post by dwhitney67 on 2011-06-17
> **ziekfiguur said:**
> Edit: oh wait, im wrong, never mind.

:)  I was just about to correct you on the basics of arithmetic.

---

