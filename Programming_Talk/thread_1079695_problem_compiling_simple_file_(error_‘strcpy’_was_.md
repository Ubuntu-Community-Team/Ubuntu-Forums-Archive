---
title: "problem compiling simple file (error: ‘strcpy’ was not declared in this scope)"
date: 2009-02-24
forum: Programming Talk
---

### Post by eylkrn on 2009-02-24
Hi All,

I have a problem compile this files in ubuntu. it compile great under centos.
however, in ubunto I get the following error:
test.cpp:17: error: &#8216;strcpy&#8217; was not declared in this scope


can anyone tell me whats the problem and how to fix this? 
thanks.

here is the file:

#include <stdlib.h>
#include <signal.h>
#include <string>
#include <stdarg.h>



using namespace std;

void test(char *name)
{

      string strTemp;


      strcpy(name,"bb");
}

---

### Post by PandaGoat on 2009-02-24
You need to include either cstring or string.h (they're different ways to write the same thing).  These are different than string;  cstring and string.h are c libraries; just string is a c++ library.

Generally, in c++ you include a c header by adding .h (#include <stdlib.h>) or prepending a c (#include <cstdlib>).  When including a c++ header, always leave off the .h (#include <string>).

Anyway, you are mixing c and c++ too much.  Either use strictly c and char* for strings or use c++ and use [std::string.]("http://www.cplusplus.com/reference/string/string/")

---

### Post by Can+~ on 2009-02-24
The string.h library originally is for plain character arrays. On the other hand, C++ strings are instances of a string class which has it's own methods.

On C++ you can copy C-strings into C++ strings with just the "=" operator.

---

### Post by eylkrn on 2009-02-25
great PandaGoat and Can+~. it work well.

Thanks a lot!

PandaGoat, I'll your comment taken, I'll try to avoid mixing C and C++ code.

---

