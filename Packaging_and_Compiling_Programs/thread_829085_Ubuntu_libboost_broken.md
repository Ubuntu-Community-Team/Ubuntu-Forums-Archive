---
title: "Ubuntu libboost broken?"
date: 2008-06-14
forum: Packaging and Compiling Programs
---

### Post by attenpeter on 2008-06-14
Hi,

I'm trying to compile this simple "program" using boost under ubuntu:

```
#include <boost/tr1/utility.hpp>

int main()
{
    return 1234;
}
```

However, I get the following error: ```
/usr/include/boost/tr1/detail/config.hpp:60:26: error: no include path in which to search for utility
```

The boost website says to fix this, either ```
#define BOOST_TR1_DISABLE_INCLUDE_NEXT
``` or ```
#define BOOST_TR1_GCC_INCLUDE_PATH /usr/include/c++/4.2
``` but neither works. Both combined also won't work. It still outputs the same error.

So how do I fix this in ubuntu? (hardy heron) It flawlessly compiles on other distributions...

EDIT: I compile with the following command: ```
g++ test.cpp -I /usr/include/boost/tr1/tr1 -I /usr/include/boost -I /usr/include -o test
```

bye,
Peter

---

### Post by DarkerStar on 2008-07-01
i was having the same problem, but the modified command line didn't work for me.

Eventually i just said to hell with it, and i include in the form <tr1/utility>. It's non-standard, and it doesn't use Boost (it uses GCC's TR1 support, part of which was lifted from Boost anyway), but it works for me.

```
#include <tr1/memory>
#include <tr1/utility>

int main()
{
  std::tr1::shared_ptr<int> x(new int);
  return 0;
}
```

The above compiles without a complaint with "g++ -ansi -pedantic -Wall test.cpp". It's technically not Boost.TR1, but it does the job, and you can use the rest of Boost unhindered.

---

### Post by afoglia on 2010-03-03
I stumbled across this via Google, while dealing with the problem myself.  It's a problem with Boost (in particular when Boost is in /usr/include, as the package does).  They patched it and the bug fix should be in 1.43.

[Boost mailing list post with link to diff]("http://lists.boost.org/boost-users/2010/02/56820.php")

Is this worth making an Ubuntu bug report?  At the least that should help it get into 10.4, right?  Hopefully it can be back-ported to 9.10 as well.

---

