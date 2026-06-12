---
title: "iostream alternative in ubuntu"
date: 2010-03-25
forum: Programming Talk
---

### Post by ltoso on 2010-03-25
Hi,
i am learning c++ programming and i can do the basic on windows on turbo c++, i am running ubuntu on my home system and i want to learn to use c++ on ubuntu, i have downloaded the buil-essential pacakge so that i can compile c++ programs, but it gives the error that there is no 
iostream.h header file 
and hence undeclared cout and cin which are there present in windows

please suggest
Regards
ltoso

---

### Post by snova on 2010-03-25
> **ltoso said:**
> Hi,
i am learning c++ programming and i can do the basic on windows on turbo c++, i am running ubuntu on my home system and i want to learn to use c++ on ubuntu, i have downloaded the buil-essential pacakge so that i can compile c++ programs, but it gives the error that there is no 
iostream.h header file 
and hence undeclared cout and cin which are there present in windows

please suggest
Regards
ltoso

Installing build-essential will pull in the C++ standard library, so if it's not there, you did something else. What *exactly* did you do?

Also, don't use **iostream.h**; use **iostream**.

---

### Post by johnl on 2010-03-25
iostream.h is an out-dated, legacy header file.  As snova pointed out, you should be using <iostream>.  In fact, all the C++ standard library header files are extension-less.

You will also need to write:

```

std::cout << ... << std::endl

```

or 

```

using namespace std;

cout << ... << endl;

```

or

```

using std::cout;
using std::endl;

cout << ... << endl;

```

---

