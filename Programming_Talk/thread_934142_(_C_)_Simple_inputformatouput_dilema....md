---
title: "( C ) Simple input/format/ouput dilema..."
date: 2008-09-30
forum: Programming Talk
---

### Post by Thesuperchang on 2008-09-30
Right, I've managed to isolate and write a short implementation of it.

[PHP]#include <stdio.h>

int main(void)
{
	char c1, c2;
	int value1, value2, value3;

	scanf("%c%c", &c1, &c2);
	printf("%c ",  c1);
	printf("%c\n",  c2);
	sscanf(&c1, "%d", &value1);
	sscanf(&c2, "%d", &value2);
	value3 = value1 + value2;
	printf("%d + %d = %d\n", value1, value2, value3);

	return 0;
}[/PHP]

What is happening
> 12
1 2
1 + 21 = 22


What I want to occur
> 12
1 2
1 + 2 = 3

What the heck is going on.

Thanks in advance,
~C. Anderson.

---

### Post by doorman on 2008-09-30
sscanf is meant to be used with char* arguments, not char arguments. My guess is that after the c1 (or c2) var in the memory there is no '\0', so sscanf keeps on reading the number. this way is quite unsafe since you can control only one memory location with char.

The way you should do it:
[php]value1 = c1 - '0';
value2 = c2 - '0';
value3 = value1 + value2;[/php]

chars are in fact ints, so you can easy substract characters from them ;)

hope this helps

---

### Post by nvteighen on 2008-09-30
> **doorman said:**
> 

chars are in fact ints, so you can easy substract characters from them ;)


What he means is that C doesn't really distinguish data by type, but by length. If some data uses 1 byte, it is a char, e.g. And it can be whatever you like it to be... That explains why C is weak typed by design... it actually has no types to enforce.

---

