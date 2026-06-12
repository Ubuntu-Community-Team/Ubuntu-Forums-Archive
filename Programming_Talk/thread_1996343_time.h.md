---
title: "time.h"
date: 2012-06-04
forum: Programming Talk
---

### Post by dep0 on 2012-06-04
Hi, i am having problem with libraries in c.
I have to write a program that uses the time.h library (in Borland). My compiler wont recognise these libraries.
Any suggestions?
Hint: I wanted the time.h function cause i had to calculate the time that a person enters and leaves a shop.
Any help is welcome.

---

### Post by 11jmb on 2012-06-04
Was time.h not recognized at compile time? or was this a link error?

compiler statements, error messages, and code always help as well :)

---

### Post by dep0 on 2012-06-04
I actually just got it to work. The problem is it's not working properly. It was suppose to give me the seconds that had passed from 1-1-1970 (i think), but it keeps giving me the same number.

My code is 
```
#include <stdio.h>
#include <time.h>

int main()
{
	float i;
	i=time(NULL);
	printf("seconds passed from 1-1-1970 are %f\n", i);
	return 0;
	
}


```

Sorry if it's a stupid mistake i am making it's the first time i use this function.

---

### Post by 11jmb on 2012-06-04
Not a stupid mistake, it's probably how printf is formatting i

try using ctime, and see if the problem persists

EDIT: When i said ctime, I meant the function in time.h, not the C++ header file. Sorry if that was confusing.

---

