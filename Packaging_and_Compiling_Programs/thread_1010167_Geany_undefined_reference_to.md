---
title: "Geany: undefined reference to"
date: 2008-12-13
forum: Packaging and Compiling Programs
---

### Post by DrPepper836 on 2008-12-13
I've been trying to write a short, simple program, to see how well the Geany compiler works. I used the class creator to create a short test class, gave it a few methods, and then had it create an instance in my main function. That worked fine. However, whenever I try to actually use a method in the thing, it gives me the "undefined reference to" error. However, compiling the same files works fine with codeblocks. Is there anything that I need to or could do to get it to work with Geany?

main.cpp:
```
#include <iostream>

#include "testclass.h"

using namespace std;

int main(int argc, char** argv)
{
	TestClass t;
	t.Set(32);
	cout << t.Get() << endl;
	return 0;
}

```

testclass.h:
```
#ifndef TESTCLASS_H
#define TESTCLASS_H

class TestClass
{
	public:
		TestClass();
        void Set(int i);
        int Get();
	private:
		int n;
};

#endif /* TESTCLASS_H */

```

testclass.cpp:
```
#include "testclass.h"


TestClass::TestClass()
{

}

void TestClass::Set(int i)
{
    n = i;
}

int TestClass::Get()
{
    return n;
}

```

---

