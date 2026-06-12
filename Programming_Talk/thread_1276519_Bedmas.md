---
title: "Bedmas"
date: 2009-09-27
forum: Programming Talk
---

### Post by dE_logics on 2009-09-27
In the following sources -

```
#include<stdio.h>
main()
{
	char a = 2^2/2*2+5-1;
	printf("%d \n", a);
	//Expected - ((((2^2)/2)*2)+5)-1
	//Expected result -- 8
	//Actual result -- 4
	a = 1 - 5+2*2/2^2;
	printf("%d \n", a);
	//Expected - ((((2^2)/2)*2)+5)-1
	//Expected result -- 8
	//Actual result -- -4
}
```

I expect a result 8 after computation of 2^2/2*2+5-1 or 1 - 5+2*2/2^2 since 1 - 5+2*2/2^2 will mean -
((((2^2)/2)*2)+5)-1 and 2^2/2*2+5-1 will mean -
((((2^2)/2)*2)+5)-1

Which yields 8.

---

### Post by CptPicard on 2009-09-27
You're probably expecting ^ to mean exponentiation, which it doesn't. :)

---

### Post by dE_logics on 2009-10-05
> **CptPicard said:**
> You're probably expecting ^ to mean exponentiation, which it doesn't. :)

Yes, you are right.

---

