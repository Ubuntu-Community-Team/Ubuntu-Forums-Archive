---
title: "[SOLVED] C++ help!!!"
date: 2008-11-15
forum: Programming Talk
---

### Post by phantomgunex on 2008-11-15
Hey everyone, i am a beginner in C++ and borrowed a book on C++ from the library. I am using Geany as my IDE. When i tried to compile this code i get this error 
project.cpp:33: error: no match for ‘operator>’ in ‘std::cin > i
Can someone help???](*,)](*,)](*,)]
[PHP]#include <iostream>
#include <cstdlib>
#include <stdlib.h>
#include <string.h>

using namespace std;

int main(int argc, char** argv)
{
	int i;
	cin > i;
	if (i > 10)
	{
		cout << "It's greater than 10." << endl;
	}
	else 
	{
		 cout << "It's not greater than 10." << endl;
	}
	return 0;
}[/PHP]

---

### Post by hessiess on 2008-11-15
its:

```
cin >> i;
```
;)

---

### Post by rzrgenesys187 on 2008-11-15
replace cin > with cin >> at line 11

---

### Post by phantomgunex on 2008-11-15
Thanks! stupid book gave me the wrong info. But i cant blame it cuz the IDE mentioned in the book is dev-C++.

---

### Post by rzrgenesys187 on 2008-11-15
That shouldn't matter since I think dev-C++ uses g++ to compile which is the same as geany.  I'd bet it's just a typo.

---

