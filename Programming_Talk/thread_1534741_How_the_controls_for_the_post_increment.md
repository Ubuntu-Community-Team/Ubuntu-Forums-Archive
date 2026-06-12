---
title: "How the controls for the post increment"
date: 2010-07-20
forum: Programming Talk
---

### Post by navaneethan on 2010-07-20
#include<stdio.h>
int main()
{
	int a=5;
	a=a++ * a++;
	printf("%d",a);
	return 0;
}


#include<stdio.h>
int main()
{
	int a=5;
	printf("%d",a=(a++ * a++));
	return 0;
}


Friends,
here i get the output 27 and 30 respectively Please may i know how the control goes I can able to understand the first one but How the 2nd one? what is the difference between both of them?

---

### Post by dwhitney67 on 2010-07-20
```

#include <stdio.h>

int main(void)
{
   int a = 5;
   int y = a++ * a++;

   printf("a = %d, y = %d\n", a, y);
   return 0;
}

```

```

gcc -Wall foo.c
foo.c: In function &#8216;main&#8217;:
foo.c:6: warning: operation on &#8216;a&#8217; may be undefined

```

Thus the final answer:  **operation on &#8216;a&#8217; may be undefined**

And because of such, you should not develop code like this.

---

### Post by MadCow108 on 2010-07-20
heres a little explanation why its undefined:
[http://en.wikipedia.org/wiki/Sequence_point](http://en.wikipedia.org/wiki/Sequence_point)

---

