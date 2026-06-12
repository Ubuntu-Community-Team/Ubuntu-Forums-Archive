---
title: "g++ problem"
date: 2009-10-12
forum: Programming Talk
---

### Post by caelestis2 on 2009-10-12
The following code works fine with VC express, but not in GCC. Does anyone know why it won't compile? It gives this error:

```
conversion from ‘main()::functor’ to non-scalar type ‘std::tr1::function<void()>’ requested
```

Same thing happens if I use boost::function instead of std::tr1::function.

[PHP]#include <iostream>
#include <tr1/functional>
#include <tr1/functional_hash.h>

void callfunc(std::tr1::function<void()> func) {func();}

int main() {
	struct functor {
		void operator()(void) {std::cout << "lol" << std::endl;}
	};
	functor f;
	callfunc(f);
}
[/PHP]

---

### Post by manualqr on 2009-10-13
I think your nested functor struct has to be the same type as std::tr1::function<void()>. I've never used this before so I may be wrong.

My suggestion is to do it the C way;
```

void callf(void (*func)()) { func(); }

int main() {
  void my_func() {
    ...
  }

  callf(my_func);
}

```

---

### Post by MadCow108 on 2009-10-13
g++ < 4.4 does not to support local function object (aka "local and unnamed types as template arguments") yet
[http://gcc.gnu.org/gcc-4.4/cxx0x_status.html](http://gcc.gnu.org/gcc-4.4/cxx0x_status.html)

so you have to move the object to global scope or wait for gcc 4.5:
[http://gcc.gnu.org/gcc-4.5/cxx0x_status.html](http://gcc.gnu.org/gcc-4.5/cxx0x_status.html)
(or use development branch [not recommended])

in general the support of  TR1 and other c++0x related stuff varies greatly between compilers. Don't use it in the next few years if you need portable code.

---

