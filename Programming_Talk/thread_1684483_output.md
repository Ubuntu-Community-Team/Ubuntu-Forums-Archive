---
title: "output??"
date: 2011-02-09
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-09
[PHP]

#include<stdio.h>
void main()
{
float a[]={13.24,1.5,1.5,5.4,3.5};
float *j;
j=a;
j=j+4;
printf("%d%d%d",j,*j,a[4]);
}

[/PHP]

when i am running this programme on turbo c compiler, i am getting -1400.why???

---

### Post by fct on 2011-02-09
First, j is a pointer, print with "%x" to get the hex address.

Second, *j is a reference to a number in a[], that is a floating point number. Use "%f". Same for the next one.

Third, please use proper separators for different values. "\n" would be nice.

---

