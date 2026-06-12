---
title: "C - casting as unsigned"
date: 2010-09-28
forum: Programming Talk
---

### Post by marshmallow1304 on 2010-09-28
```

int a = -1;
unsigned b = (unsigned)a;
printf("%d %d\n", a, b);
```

The output is
-1 -1


Why?  I was under the impression that converting from signed to unsigned would, well, drop the sign.

---

### Post by worksofcraft on 2010-09-28
%d interprets the parameter as signed decimal.
If you want unsigned format, then use %u

Note: functions like printf that have variable number of parameters do not recognize the type of their parameters and it is up to the programmer to interpret correctly. If you were writing in C++, then the output stream does understand about type:
```

// g++ unsigned.cc; ./a.out
#include <iostream>
using namespace std;

int main() {
	unsigned U = (unsigned) -1;
	signed D = -1;

	cout << "unsigned:"<< U << " signed:" << D << endl;
}

```

---

### Post by marshmallow1304 on 2010-09-28
Thank you.  That really cleared it up for me.

---

