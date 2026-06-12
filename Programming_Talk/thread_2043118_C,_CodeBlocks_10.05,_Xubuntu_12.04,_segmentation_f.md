---
title: "C, Code::Blocks 10.05, Xubuntu 12.04, segmentation fault (core dumped)"
date: 2012-08-15
forum: Programming Talk
---

### Post by FlameFactory on 2012-08-15
Trying to execute simple program, but result is "segmentation fault (core dumped)". what i'm doing wrong?)
[PHP]
/* In C */
#include <stdio.h>
#include <stdlib.h>

int main()
{
    unsigned long int i;
    unsigned long int max=9999999;
    unsigned short int N[max];
    for (i=0; i<max; i++)              
    {
        N[i]=1;
    };
    //printf("%d\n",N[max-1]);
    return 0;
}
[/PHP]

---

### Post by Some Penguin on 2012-08-15
Don't try to allocate massive arrays on the stack.

Also, trying to store a long int in space for a short int is trouble, and means that you'll be writing bytes outside of the array.  Don't do that.

---

### Post by FlameFactory on 2012-08-15
So what can I do if i need to store in memory array of at least 10^8 int values?

---

### Post by Bachstelze on 2012-08-15
> **Some Penguin said:**
> 
Also, trying to store a long int in space for a short int is trouble, and means that you'll be writing bytes outside of the array.  Don't do that.

I agree with "don't do that", but not with what precedes.

> **FlameFactory said:**
> So what can I do if i need to store in memory array of at least 10^8 int values?

Use malloc() to allocate memory on the heap, not on the stack.

---

### Post by Some Penguin on 2012-08-15
Hm, true.  C will simply drop the 'excess' bytes resulting in a horrible type conversion if you're doing a straight assignment and not, say, a memcpy.  The folks at Oracle recently found that there was a highly embarrassing bug for a related reason -- MySQL taking the return value of memcmp and shoving it into a byte, which in certain situations meant that an incorrect password would actually be treated as if it were correct.

---

### Post by FlameFactory on 2012-08-16
> **Bachstelze said:**
> I agree with "don't do that", but not with what precedes.



Use malloc() to allocate memory on the heap, not on the stack.

thanks.

---

