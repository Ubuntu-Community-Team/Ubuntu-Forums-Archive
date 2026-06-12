---
title: "using iopl"
date: 2008-04-23
forum: Programming Talk
---

### Post by drinu21 on 2008-04-23
hi,
to use the function iopl() in c++, i only need to include unistd.h?? 
cause i when writing, 
```
#include <unistd.h>
#include <stdio.h>
#define extern static
#include <asm-i386/io.h>
#undef extern

#define PORT 0xd060
class pPort
{
	public:
	unsigned char data;
	void getdata()
	{	
		iopl(3);
		data = inb(PORT);	
	}
};
```

the program is giving me an error - iopl was not declared.
do i need to include something more??

thanks
adrian

---

### Post by drinu21 on 2008-04-23
ok i solved the problem. i needed to include sys/io.h for ioperm in kubuntu

---

