---
title: "[C++] Implict copy constructor"
date: 2010-10-09
forum: Programming Talk
---

### Post by dawwin on 2010-10-09
I didn't found anywhere, what is behaviour of implict copy constructor in this case
```

class test1
{
   string a;
   string b;
};

```

Will it copy content of class test1 as normal bytes or call copy constructor of each element?

---

### Post by worksofcraft on 2010-10-09
> **dawwin said:**
> I didn't found anywhere, what is behaviour of implict copy constructor in this case
```

class test1
{
   string a;
   string b;
};

```

Will it copy content of class test1 as normal bytes or call copy constructor of each element?

When in doubt...
Try it out...
```

#include <string>
#include <stdio.h>
#include <iostream>

using namespace std;

struct my_string: string {
	my_string() {}
	my_string(const my_string &Original): string((string) Original) {
		printf("copy constructing my_string\n");
	}
	my_string & operator=(const my_string &Original) {
		printf("copy assignment my_string\n");
	}
};

struct test1 {
   my_string A;
   my_string B;
};

int main() {
	test1 One;
	One.A += "One A";
	One.B += "to B or not two B?";
	test1 Two = One;
	cout << "Two A=" << Two.A << endl;
	cout << "Two B=" << Two.B << endl;
	return !printf("hasta la vista\n");
}

```

p.s. You have to compile and run it to get an answer ;)

---

### Post by dawwin on 2010-10-09
Thanks

---

