---
title: "Initialising array of maximum size."
date: 2009-05-03
forum: Programming Talk
---

### Post by kcode on 2009-05-03
I want to have an array int - a[32000] but the tcwin45 compiler is not allowing that, while in g++ I am able to do that.

---

### Post by dwhitney67 on 2009-05-03
Show the actual code that you are compiling with tcwin45 and g++.

---

### Post by kcode on 2009-05-03
#include <iostream.h>

using namespace std;

int main()
{
	int a[100000];
	return 0;
}

As simple as that. Same for g++. In tcwin45 I am getting this error : 
Array size too large in function main.

---

### Post by dwhitney67 on 2009-05-03
See if this works:
```

//#include <iostream>    // btw, not needed, and iostream.h is the deprecated format

int main()
{
int* a = new int[100000];
//...
delete [] a;
}

```

P.S.  I do not know the inner-workings of tcwin45, but it is possible that it limits your stack size.  Perhaps there is a way to increase it?

---

### Post by Arndt on 2009-05-03
> **kcode said:**
> #include <iostream.h>

using namespace std;

int main()
{
	int a[100000];
	return 0;
}

As simple as that. Same for g++. In tcwin45 I am getting this error : 
Array size too large in function main.

You can try using 'static':

```
int main()
{
	static int a[100000];
	return 0;
}
```

Then it won't be allocated on the stack.

---

### Post by kcode on 2009-05-03
Pointer declaration of array did work, save static declaration.

Thanks.

---

