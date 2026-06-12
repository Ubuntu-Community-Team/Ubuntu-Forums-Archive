---
title: "[C Code] How to check Endian-ness"
date: 2009-02-08
forum: Programming Talk
---

### Post by suncoolsu on 2009-02-08
Hi All,
I was wondering how to write a C-Code to check if a system is Little Endian or Big Endian?

Any help?

I know its simple - but I have no clue where to begin :-(

Thx

---

### Post by slavik on 2009-02-08
make an int*, put some pattern in there across 4 bytes, covert it to a char* and read one byte, see if it's the lowest signifact byte or not ... that or I think it's done through the preprocessor.

---

### Post by ymo on 2009-02-08
Create a union between a short and two bytes. Assign 0x1234 to the short and read the first byte. If it is 0x34 then LE, if 0x12 then BE.

---

### Post by suncoolsu on 2009-02-08
> #include <stdio.h>
#include <stdbool.h>


bool isBigEndian() 
{
	int no = 1;
    	char *chk = (char *)&no;

    	if (chk[0] == 1)
	{
        	return 0;
	}
    	else
	{
        	return 1;
	}
}

main()
{
	printf("this is %d \n",(int)isBigEndian());
	return 0;
}

this code works for me on my Intel Machine :D thx everyone

---

