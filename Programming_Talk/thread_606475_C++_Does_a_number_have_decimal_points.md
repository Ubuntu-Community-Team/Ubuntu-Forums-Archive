---
title: "C++ Does a number have decimal points?"
date: 2007-11-08
forum: Programming Talk
---

### Post by TreeFinger on 2007-11-08
How would I be able to write a statement that could check if a number has decimal places after it? I am trying to find factors of a very large number.

---

### Post by yabbadabbadont on 2007-11-08
If the type of the variable is not a floating point type, then it has no decimals.

---

### Post by dwhitney67 on 2007-11-08
Here's a ridiculously stupid way to find out:

```
#include <iostream>

using namespace std;

int main()
{
  double fValue = 5.676;

  if ( fValue - (int)fValue > 0.0 )
  {
    cout << "value has decimal places after it" << endl;
  }
  else
  {
    cout << "value does NOT have decimal places after it" << endl;
  }
}
```

---

### Post by TreeFinger on 2007-11-08
It is a long long / long long.

I am trying this, thanks for the tip dwhitney67 .
```

if ( (BIGNUM % isThisFactor) - static_cast<int>(isThisFactor) > 0 ){

```

---

### Post by dwhitney67 on 2007-11-08
A long long is a 64-bit integer.  When you divide (or add, subtract, or multiply) it with another long long (or other integer), you will always end up with an integer type.  There will never be values after the "decimal".

As an example,

```
int ten = 10;
int three = 3;

int result = ten / three;
```

The result will be 3; not 3.33333333...

---

### Post by yabbadabbadont on 2007-11-08
Never mind.

---

### Post by DavidBell on 2007-11-08
use either 

if (A - longlong(A / B) * B == 0)

or

if (A % B == 0)   // assuming modulus works for longlong

---

### Post by Rislone on 2007-11-08
Dwhitney

That's the same conclusion I came to also, easiest way at least.

---

### Post by Sporkman on 2007-11-08
if ( fval != floor(fval) )
{
   // fval has a fractional component.
}

---

