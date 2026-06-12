---
title: "C++ help"
date: 2008-03-13
forum: Programming Talk
---

### Post by smc18 on 2008-03-13
Hi, I am stuck with some math, I'm not sure if I just need to format the output or if there is a problem with something else.

Here is an excerpt of the code,

[INDENT]sum = 3/15;[/INDENT]
[INDENT]cout << sum << endl;[/INDENT]

will just return a value of 0.

or

[INDENT]sum = 3/15 + 2;[/INDENT]
[INDENT] cout << sum << endl;[/INDENT]

will return a value of 2


However the code,

     [INDENT]sum = 10 + .5;[/INDENT]
     [INDENT]cout << sum << endl;[/INDENT]

will return a value of 10.5

Why is 3/15 returning a value of 0?

I'm programming this on a Windows machine, using Dev-C++,  I have included 
#include <iostream>
#include <iomanip>
#include <fstream>
#include <cmath>
and declared sum as a float data type, not an int.  Any help is appreciated, thanks.  If you need more information please just ask.

---

### Post by slavik on 2008-03-13
when you do 3/15, what really happens is integer division (the one with a remainder).

what you want to do is 3.0/15, this will force real division and you will get the expected 0.2.

3/15 is 0 with 3 as remainder

---

### Post by smc18 on 2008-03-13
Haha it worked, that simple eh?, Thanks alot.

---

