---
title: "Armadillo Matrix Library"
date: 2010-08-13
forum: Programming Talk
---

### Post by adhika on 2010-08-13
Hi,

I would like to use the Armadillo C++ matrix library for my code and I find some difficulties when I organize my class files into separate headers and source files.

This is a short code that I wrote.

testing.h file
```

#ifndef INC_
#define INC_


using namespace arma;

class testing {
	public:
		double x;
                mat C(5,5);
		void set_x(void);
};

#endif

```

testing.cpp file:
```

#include <iostream>
#include <armadillo>
#include "testing.h"


using namespace std;
using namespace arma;

void testing::set_x(void) {
	x = 5;
	cout <<"x = "<< x << endl;
}

```

And the main program:
```

#include <iostream>
#include <armadillo>
#include "testing.h"

using namespace std;

int main(void) {
	testing a;
	
	a.set_x();

	return 0;

}

```

The problem appears to be when I declared the type ```
mat C(5,5)
```

The following error codes appear when I use the makefile:
```

g++ -c main.cpp
In file included from main.cpp:3:
testing.h:11: error: expected identifier before numeric constant
testing.h:11: error: expected ‘,’ or ‘...’ before numeric constant
make: *** [main.o] Error 1

```

Any advise on this issue? Thank you so much!

---

