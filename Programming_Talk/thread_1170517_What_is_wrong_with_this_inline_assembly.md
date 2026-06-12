---
title: "What is wrong with this inline assembly?"
date: 2009-05-26
forum: Programming Talk
---

### Post by grubby23 on 2009-05-26
Hi

I am running gcc on an Intel Dual Core and what I am trying to do now is
to find out how I can pass an array to an inline assembly routine. I tried to do it the following way:

#include <stdio.h>


int array[3] = {111, 222, 333};

int main(void)
{
   int out = 0;
   __asm__ __volatile__ (
      ".intel_syntax noprefix           \n\t"
       "lea         eax, [array]        \n\t"
       "mov         eax,[eax]            \n\t"
       "inc         eax                  \n\t"
       ".intel_syntax prefix             \n\t"
     : "=a" (out)
     :   [array]  "m"  (*array)
   );


printf("out = %i\n", out);

   return 0;
}

Then I get the following weird output

Error: operation combines symbols in different segments
/tmp/ccd2NExl.s:36: Error: no such instruction: `movl %eax,-8(%ebp)'
/tmp/ccd2NExl.s:37: Error: no such instruction: `movl -8(%ebp),%eax'
/tmp/ccd2NExl.s:38: Error: no such instruction: `movl %eax,4(%esp)'
/tmp/ccd2NExl.s:39: Error: no such instruction: `movl $.LC0,(%esp)'
/tmp/ccd2NExl.s:41: Error: no such instruction: `movl $0,%eax'
/tmp/ccd2NExl.s:42: Error: no such instruction: `addl $36,%esp'
/tmp/ccd2NExl.s:43: Error: no such instruction: `popl %ecx'
/tmp/ccd2NExl.s:44: Error: no such instruction: `popl %ebp'
/tmp/ccd2NExl.s:45: Error: no such instruction: `leal -4(%ecx),%esp'

Any idea what could be wrong?

Many thanks

---

### Post by Zugzwang on 2009-05-26
Modified code:
```

#include <stdio.h>


int array[3] = {111, 222, 333};

int main(void)
{
int out = 0;
__asm__ __volatile__ (
"lea eax, [array] \n\t"
"mov eax,[eax] \n\t"
"inc eax \n\t"
: "=a" (out)
: [array] "m" (*array)
);


printf("out = %i\n", out);

return 0;
}

```

Compile with:
```

g++ -masm=intel test.c

```

---

### Post by grubby23 on 2009-05-27
Thanks a lot, that works now ;)

---

