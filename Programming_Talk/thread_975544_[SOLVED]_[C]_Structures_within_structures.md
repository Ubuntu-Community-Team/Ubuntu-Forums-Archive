---
title: "[SOLVED] [C] Structures within structures"
date: 2008-11-08
forum: Programming Talk
---

### Post by swappo1 on 2008-11-08
Hello,

I am having a problem with this program.  I am not sure how to do a structure within a structure.  I am getting multiple errors.  Any ideas?
[PHP]#include <stdio.h>
 
struct Distance
	{
	int feet;
	float inches;
	};
	
struct Room
	{
	
	Distance length;
	Distance width;
	};
	
int main(void)
{
	
	struct Room dining;
	
	dining.length.feet = 13;
	dining.length.inches = 6.5;
	dining.width.feet = 10;
	dining.width.inches = 0.0;
	
	float l = dining.length.feet + dining.length.inches/12;
	float w = dining.width.feet + dining.width.inches/12
	
	printf("\nDining room area is %.1f square feet", l*w);
		
	return 0;
}[/PHP]

---

### Post by slavik on 2008-11-08
try "struct Distance length;" :)

---

### Post by swappo1 on 2008-11-08
Ok, that worked.  I actually tried that before posting but had a misspelling I wasn't aware of that threw up a bunch of errors.  Thanks for the help.

---

