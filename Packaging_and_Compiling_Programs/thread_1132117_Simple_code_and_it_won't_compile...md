---
title: "Simple code and it won't compile.."
date: 2009-04-21
forum: Packaging and Compiling Programs
---

### Post by spdaniel91 on 2009-04-21
I've got this code I just wrote:

```

#include <stdio.h>

bool isprime(int num)
{
	int i,count=0;
	
	if(num % 2 == 0) {
		return false;
	}

	for(i=1;i<=num;i++)	{
		if(num%i==0)
		count++;
	}

	if(count==2) {
		return true;
	}
	else {
		return false;
	}


... Rest of code.


```


(By the way, yes, I know it's a stupid way to check a prime number, but it works...)

Anyway, when I try to compile my prime number generator , gcc returns:

> primenumber.c:3: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘isprime’


It compiled just fine on Windows, not sure what's wrong.

---

### Post by mali2297 on 2009-04-21
Are you writing a C program? (Not C++.) In such case, you need to include the header file **stdbool.h** to use the Boolean type.

---

### Post by spdaniel91 on 2009-04-21
> **mali2297 said:**
> Are you writing a C program? (Not C++.) In such case, you need to include the header file **stdbool.h** to use the Boolean type.

Works like a charm :D Thanks alot.

---

