---
title: "C++ NewMat question"
date: 2008-11-14
forum: Programming Talk
---

### Post by justanotherhandle on 2008-11-14
I'm very confused.  I'm trying to use the newmat matrix library which I installed from the repositories.

At this point I'm just trying to create a matrix, but when I add size parameters the program won't compile. I've googled for hours and have gone through the examples provided with the library, but I'm still not understanding why this would be.

This compiles:
```
#include <iostream>
#include <stdio.h>
#include "/usr/include/newmat/newmatap.h"
#include "/usr/include/newmat/newmat.h"

using namespace std;
using namespace NEWMAT;

int main () {
	Matrix mat();
}
```

But this does not: (Only difference is size parameters)
```
#include <iostream>
#include <stdio.h>
#include "/usr/include/newmat/newmatap.h"
#include "/usr/include/newmat/newmat.h"

using namespace std;
using namespace NEWMAT;

int main () {
	Matrix mat(2,2);
}
```


The error I get is this:
```
$ g++ -o hmwk1 hmwk1.cpp
/tmp/ccUI3Lt1.o: In function `main':
hmwk1.cpp:(.text+0x1a4): undefined reference to `NEWMAT::Matrix::Matrix(int, int)'
/tmp/ccUI3Lt1.o: In function `NEWMAT::Matrix::~Matrix()':
hmwk1.cpp:(.text._ZN6NEWMAT6MatrixD1Ev[NEWMAT::Matrix::~Matrix()]+0x7): undefined reference to `vtable for NEWMAT::Matrix'
hmwk1.cpp:(.text._ZN6NEWMAT6MatrixD1Ev[NEWMAT::Matrix::~Matrix()]+0x17): undefined reference to `NEWMAT::GeneralMatrix::~GeneralMatrix()'
collect2: ld returned 1 exit status
```

Why? The documentation say that I should be able to create a matrix with a size. Why can I not?

Thanks for what ever help you can offer.

---

### Post by samjh on 2008-11-14
> **justanotherhandle said:**
> The error I get is this:
```
$ g++ -o hmwk1 hmwk1.cpp
/tmp/ccUI3Lt1.o: In function `main':
hmwk1.cpp:(.text+0x1a4): undefined reference to `NEWMAT::Matrix::Matrix(int, int)'
/tmp/ccUI3Lt1.o: In function `NEWMAT::Matrix::~Matrix()':
hmwk1.cpp:(.text._ZN6NEWMAT6MatrixD1Ev[NEWMAT::Matrix::~Matrix()]+0x7): undefined reference to `vtable for NEWMAT::Matrix'
hmwk1.cpp:(.text._ZN6NEWMAT6MatrixD1Ev[NEWMAT::Matrix::~Matrix()]+0x17): undefined reference to `NEWMAT::GeneralMatrix::~GeneralMatrix()'
collect2: ld returned 1 exit status
```

Why? The documentation say that I should be able to create a matrix with a size. Why can I not?

I suspect the problem is not your code, but your compilation command: you didn't link the library. ;)

---

### Post by dwhitney67 on 2008-11-14
From the error message, I would say that your program compiled perfectly.

What it did not do is link; that is what the "undefined reference error" is telling you.  You need to specify the newmat library (whatever its name is) with the g++ statement.

So for instance, if the library is called "libnewmat.so", then you would specify:
```

g++ hmwk1.cpp -lnewmat -o hmwk1

```

Look in /usr/lib for any library with the "newmat" name.

P.S.  Using the fully-qualified path name for header files in /usr/include is not necessary.  It would suffice for you to use
```

#include <newmat/newmatap.h>
#include <newmat/newmat.h>

```

P.S.S.  I found this reference on the web after Googling:  [http://www.robertnz.net/nm10.htm#refer](http://www.robertnz.net/nm10.htm#refer)

---

