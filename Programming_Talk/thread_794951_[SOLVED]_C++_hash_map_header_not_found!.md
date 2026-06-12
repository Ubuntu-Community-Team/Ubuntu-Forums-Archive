---
title: "[SOLVED] C++: hash_map header not found!"
date: 2008-05-15
forum: Programming Talk
---

### Post by donatell0 on 2008-05-15
I don't know whats wrong with my installation but I know that STL is installed, as I can compile codes that use  vector, string, queue, stack, etc

But this does not compile: 

```
#include <iostream>
#include <hash_map>

using namespace std;

int main() {
	hash_map<const char*, int> M;
	M["a"] = 2;
	cout << M["a"] << endl;
	
	return 0;
}
```

The errors i get are: 
```

a.cpp:2:20: error: hash_map: No such file or directory
a.cpp: In function ‘int main()’:
a.cpp:7: error: ‘hash_map’ was not declared in this scope
a.cpp:7: error: expected primary-expression before ‘const’
a.cpp:7: error: expected `;' before ‘const’
a.cpp:8: error: ‘M’ was not declared in this scope
make: *** [a] Error 1
```

---

### Post by gvoima on 2008-05-15
try this instead
```
#include <ext/hash_map>
```
hash_map is not part of the std namespace.
So add this too; namespace __gnu_cxx OR __gnu_cxx::hash_map

---

### Post by donatell0 on 2008-05-15
[EDIT] Never mind.

Thanks a lot. I got it all working!

---

### Post by sam1948 on 2010-06-19
> **donatell0 said:**
> [EDIT] Never mind.

Thanks a lot. I got it all working!

hi
how did u solved it?

---

### Post by neo unplugged on 2010-10-05
hey SAM1948
Add this 
#include <ext/hash_map>
using namespace __gnu_cxx;
and it works for me

---

