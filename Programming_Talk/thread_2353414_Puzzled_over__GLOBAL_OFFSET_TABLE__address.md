---
title: "Puzzled over _GLOBAL_OFFSET_TABLE_ address"
date: 2017-02-21
forum: Programming Talk
---

### Post by mark allyn on 2017-02-21
Hello everyone,

I'm trying to understand how the address of the global offset table in x86 is computed.  The following apparently trivial program well-illustrates why I'm confused.
```


#include <stdio.h>

extern void * _GLOBAL_OFFSET_TABLE_;
extern void * _DYNAMIC;
void main(void)
{
printf("GOT is located at %p\n", &_GLOBAL_OFFSET_TABLE_);
printf("DYNAMIC is %p\n", &_DYNAMIC);
}
```

If I compile this simple program WITHOUT -fPICS option, when the code runs it identifies the address of the GOT as 0x1bdb and the DYNAMIC as 0x8049f08.  However, if I issue objdump -t got
the symbol for the GOT is located at 0x8049ff4.  Question 1:  Why am I seeing two different addresses for the GOT?

OK, Now suppose I compile with the -fPICS flag set.  Thusly:  cc -fPICS -g -c got.c  followed by cc -o got got.o.  The program reports that the GOT is at 0x8049ff4 and DYNAMIC is at 0x804f00.  Now when I investigate the got executable using objdump -t got I see that the GOT is at the same address as shown by the printed results.

To round out my confusion, when I disassemble the executable using objdump -d got, the disassembled code shows that the 0x1bdb value is in fact what is loaded before calling printf.

I can't figure out what's going on here.  Why two different values?  Could someone help clear this up for me.  I've looked all over the internet for an answer.

Thanks,

Mark Allyn

---

