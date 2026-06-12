---
title: "Using KDevelop to compile and run C++ programs"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by ItecKid on 2008-09-28
So, I am having a problem getting KDevelop to compile my program:

```
#include <iostream>
using namespace std;
int main ()
{
cout << "Hello, World!" << endl;
return 0;
}
```

When attempting to compile with the command
```
cc helloworld.cpp
```

The compiler prints unfriendly messages about misplaced references to a function <std>

When compiling with 
```
g++ -o helloworld -Wall helloworld.cpp
```
It compiles, but when trying to run the program with
```
./a.out
```
It says that no such file exists.

When trying with
```
./helloworld.cpp
```
It says permission denied.

Any help is appreciated.

---

### Post by kjohansen on 2008-09-28
with g++ you named the output helloworld (the -o flag) so to run it you want to use 
```

./helloworld

```

without the .cpp


Part II:
and I cant swear to it, but I think explicit namespaces are a C++ thing, and "cc" only compiles C.  also in C you would need the old style header of 

```

#include <iostream.h>

```

---

### Post by ItecKid on 2008-09-28
That works.  Thank you!

---

