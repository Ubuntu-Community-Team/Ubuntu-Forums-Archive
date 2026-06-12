---
title: "c++: coping with out-of-memory errors"
date: 2009-10-13
forum: Programming Talk
---

### Post by manualqr on 2009-10-13
I'm doing image analysis on massive data sets in C++. I've implemented and checked my code on smaller subsets, but when I try and test it on the whole thing - the program craps out.

1 img = 2 * (512 * 512 bytes) = 524288
approx. 300 images = 157286400
vectors = 3 * (157286400 / 2) = 235929600
sum = 236453888 bytes, or 225.5 MB.

I'm sure linux supports heap sizes larger than this.. I have 4GB of memory, so it really shouldn't be an issue. Does anyone know how I can get my program to finish? Will I need to write a custom allocator?

thanks

---

### Post by manualqr on 2009-10-13
update:

So apparently, the following code works;
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main() {
	char* buf = (char*) malloc(236453888);
	memset(buf, 7, 236453888);

	unsigned long long i;
	for (i=0; i < 236453888; ++i) {
		buf[i] ^= i;
	}
	
	return 0;
}

```

This means that c/++ can handle that size of data; it's just a matter of allocating enough memory once and then handing out addresses to bits of it.

This will involve custom allocators, so here's a great reference;
[http://www2.roguewave.com/support/docs/leif/sourcepro/html/toolsug/12-6.html](http://www2.roguewave.com/support/docs/leif/sourcepro/html/toolsug/12-6.html)

---

### Post by napsy on 2009-10-13
This is C code that your'e writing in not C++. If malloc() fails it will return NULL. That's why you should check your returned buffer at least with assert().

---

### Post by dwhitney67 on 2009-10-13
> **manualqr said:**
> I'm doing image analysis on massive data sets in C++. I've implemented and checked my code on smaller subsets, but when I try and test it on the whole thing - the program craps out.

1 img = 2 * (512 * 512 bytes) = 524288
approx. 300 images = 157286400
vectors = 3 * (157286400 / 2) = 235929600
sum = 236453888 bytes, or 225.5 MB.

I'm sure linux supports heap sizes larger than this.. I have 4GB of memory, so it really shouldn't be an issue. Does anyone know how I can get my program to finish? Will I need to write a custom allocator?

thanks

Depending on your system's configuration, you may not have support for large stack sizes.  You mentioned the heap in your OP, however you have presented zippo with respect to code, thus who knows if this is really a heap issue, a stack issue, or a combination of both in the form of poor coding.

If you need to increase your system's stack size, you can configure it using 'ulimit', although I do not know if this will resolve the issue with your application.

P.S.  If your C++ application were using "new", and it were to fail to allocate memory, an exception would be thrown.
```

#include <new>
#include <stdexcept>
#include <iostream>
#include <cstdlib>

int main(int argc, char** argv)
{
   const size_t memorySize = (argc > 1 ? atoi(argv[1]) * 1024 : 236453888);

   try {
      char* ptr = new char[memorySize];

      delete [] ptr;
   }
   catch (std::exception& e) {
      std::cerr << "Exception: " << e.what() << std::endl;
      return 1;
   }
}

```

---

