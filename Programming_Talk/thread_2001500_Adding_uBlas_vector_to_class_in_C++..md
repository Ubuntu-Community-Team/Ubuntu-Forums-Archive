---
title: "Adding uBlas vector to class in C++."
date: 2012-06-11
forum: Programming Talk
---

### Post by jsmidt on 2012-06-11
Hey everyone.  I would like to make a class in C++ that has a uBlas vector 'price' of length 100 each time the class is created. (I currently always want the length to be 100 and see [http://www.boost.org/doc/libs/1_49_0/libs/numeric/ublas/doc/vector.htm#vector](http://www.boost.org/doc/libs/1_49_0/libs/numeric/ublas/doc/vector.htm#vector) for more info on uBlas vectors.)  If I don't specify 'price' has 100 elements it compiles just fine assuming I have this:

Stocks.hpp
```
#include <boost/numeric/ublas/vector.hpp>
using namespace boost::numeric::ublas;

class Stock
{
private:
   char name[50];
   vector<double> price;

public:
   Stock(char *n);
   ~Stock();
};
```

Stocks.cpp
```
#include<iostream>
#include "Stocks.hpp"
using std::cout;
using std::endl;

Stock::Stock(char *n)
{
   strcpy(name,n);
}

Stock::~Stock()
{
   cout << "Object has been destroyed" << endl;
}
```

and compile as:
```
g++  -I/usr/local/include/ -c Stocks.cpp
```

So again this compiles just fine.  However, just like I want 'name' to have 50 elements in the .hpp file, I would like to hard-code 'price' having 100 elements and have tried this:

Stocks.hpp
```
#include <boost/numeric/ublas/vector.hpp>
using namespace boost::numeric::ublas;

class Stock
{
private:
   char name[50];
   vector<double> price(100);

public:
   Stock(char *n);
   ~Stock();
};
```

I get the following error:
```
Stocks.hpp:8: error: expected identifier before numeric constant
Stocks.hpp:8: error: expected ‘,’ or ‘...’ before numeric constant
```

Any ideas how to make 'price' be a uBlas vector of length 100 just like 'name' was successfully compiled with length 50?  Thanks.

---

### Post by the_unforgiven on 2012-06-11
> **jsmidt said:**
> 
Stocks.hpp
```
#include <boost/numeric/ublas/vector.hpp>
using namespace boost::numeric::ublas;

class Stock
{
private:
   char name[50];
   vector<double> price(100);

public:
   Stock(char *n);
   ~Stock();
};
```


vector being a template based class, it cannot be initialized in the class *declaration*. You need to initialize it either in the constructor or in the initializers list.
Check the following codes which are working:
stocks.hpp
```

#ifndef __STOCKS_HPP_
#define __STOCKS_HPP_

#include <boost/numeric/ublas/vector.hpp>

using namespace boost::numeric::ublas;

class Stock
{
private:
    char name[50];
    vector<double> price;

public:
    Stock(char *n);
    size_t size();
    const char* get_name() { return name; }
    ~Stock();
};

#endif /* __STOCKS_HPP_ */

```

stocks.cpp - the initialization of **price** using initializer list is indicated in bold:
```

#include <iostream>
#include <cstring>
#include "stocks.hpp"

using std::cout;
using std::endl;
using std::strcpy;

Stock::Stock(char *n) : **price(100)**
{
   strcpy(name, n);
}

Stock::~Stock()
{
   cout << "Object '" << name << "' has been destroyed" << endl;
}

size_t Stock::size()
{
    return price.size();
}

```

main.cpp:
```

#include <iostream>
#include "stocks.hpp"

int main()
{
    Stock s("Test");
    std::cout << "Stock '" << s.get_name() << "' has " << s.size()
                << " elements " << std::endl;
    return 0;
}

```

Compile it as:
```
g++ stocks.cpp main.cpp -o stocks
```

HTH ;)

---

### Post by jsmidt on 2012-06-11
Thanks a lot!

---

