---
title: "Gmp"
date: 2011-10-24
forum: Programming Talk
---

### Post by 7cardcha on 2011-10-24
I am wondering how to add a couple dozen 50 digit integers in GMP. I know how to use C++ just not gmp. When I try to use any calculator etc etc. It just gives me a non-precise number.

---

### Post by gsmanners on 2011-10-24
This is covered in chapter 12 of gmp-doc, you know. It doesn't look all that tough.

---

### Post by 7cardcha on 2011-10-24
Yeah but I am a n00b and need extra help. So far I have this

```



#include <iostream>
#include <gmp.h>
using namespace std;

int main()
{
    mpz_t num;
    mpz_init(num);
}


```


How to do I add an integer to that num. I don't understand the documentation.

---

### Post by 7cardcha on 2011-10-24
Oh common just provide me with an example of creating a GMP int and adding a number to it. PWEESE?

---

### Post by gsmanners on 2011-10-24
Well for c++, you don't use gmp.h. It should be something more like:

```
#include <gmpxx.h>
#include <iostream>
using namespace std;

int main (void)
{
  mpz_class a, b, c;
  a = 1234;
  b = "-5678";
  c = a+b;
  cout << "sum is " << c << "\n";
  cout << "absolute value is " << abs(c) << "\n";
  return 0;
}
```

(The above is straight out of the chapter I mentioned.)

EDIT: Here's a compile line:

```
g++ -o sum sum.cc -lgmpxx -lgmp
```

Then, when you run it:

```
$ ./sum
sum is -4444
absolute value is 4444
```

Pretty easy, I'd say (if you opened the doc, that is).

---

