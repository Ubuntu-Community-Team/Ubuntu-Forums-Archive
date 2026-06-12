---
title: "FLT_MAX not working"
date: 2009-01-23
forum: Programming Talk
---

### Post by monkeyking on 2009-01-23
I'm having troubles getting the FLT_MAX

```

#include <iostream>
#include <cmath>
#include <limits>
#include <cfloat>
using namespace std;

typedef unsigned int uint;

int main(){
  int var=0;
	printf("float max is:%d\n",FLT_MAX);
	return 0;
}

```
Program compiles with cfloats, but when running it just throws random values.

---

### Post by johnl on 2009-01-23
Try compiling with -Wall:

> warning: format %d expects type int, but argument 2 has type double

You should pass %f to printf to specify that you are printing a floating point number instead of %d, which indicates an integer.

---

### Post by monkeyking on 2009-01-23
ohh, god,
that was embarassing.

Thanks

---

