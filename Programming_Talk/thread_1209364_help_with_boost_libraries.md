---
title: "help with boost libraries"
date: 2009-07-10
forum: Programming Talk
---

### Post by darthshak on 2009-07-10
I recently downloaded the boost v1.39 libraries for some projects of mine. I wanted to test the incomplete gamma function, which is supposed to be gamma_p. 

The following is my code snippet :
```
#include <iostream>
#include <boost/math/special_functions/gamma.hpp>
using namespace std;

int main() {
        cout << gamma_p(2,1) << endl;
return 0;
}

```

The boost libraries are installed in /opt/boost. The command I used to compile this program was :
```
g++ gammainc.cpp -I /opt/boost/include/boost-1_39/ -L /opt/boost/lib/ -lboost_math_c99f-gcc43-mt-1_39
```

I got the following error :
```
gammainc.cpp: In function ‘int main()’:
gammainc.cpp:7: error: ‘gamma_p’ was not declared in this scope
```

The include files are located in /opt/boost/include/boost-1_39/boost/math/special_functions/ (in this case, the file gamma.hpp)

Now, the gamma.hpp header seems to contain the definition of gamma_p, but somehow, I am unable to get it to work. The library which I am using is libboost_math_c99f-gcc43-mt-1_39.so. What exactly is the problem?

---

### Post by Zugzwang on 2009-07-10
> **darthshak said:**
> What exactly is the problem?

Boost functions are in the boost namespace. Try referencing to your function as "boost::gamma_p".

---

### Post by darthshak on 2009-07-10
> Boost functions are in the boost namespace. Try referencing to your function as "boost::gamma_p"

It completely slipped my mind...thanks a lot! Problem solved.

For the record, it turned out to be boost::math::gamma_p

---

