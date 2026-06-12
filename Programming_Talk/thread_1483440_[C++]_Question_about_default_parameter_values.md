---
title: "[C++] Question about default parameter values"
date: 2010-05-14
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-05-14
This is a question that's been bugging me for a long time. Let's say we have this function definition:

```
void foo(int first, int second=5, int third=555)
```

Then let's say I want to call it and set the 'first' and 'second' parameters, I will simply do:
```
 foo(1, 7);
```

My question is what do I do if I want to change only the 'first' and 'third' parameter but leave the default value for the 'second' parameter?

---

### Post by robots.jpg on 2010-05-14
I don't think that's possible.  If you find yourself needing the default value for 'second' more than the default value for 'third', switch them.  Or you could take away the defaults and overload the function for two values.  Otherwise you'll have to supply all three.

---

### Post by lisati on 2010-05-14
> **robots.jpg said:**
> I don't think that's possible.  If you find yourself needing the default value for 'second' more than the default value for 'third', switch them.  Or you could take away the defaults and overload the function for two values.  Otherwise you'll have to supply all three.

I agree. 

My experience with C++ is minimal so I looked this up. If you omit a parameter, you have to omit all the parameters to the right.

Have a look here: [http://www.learncpp.com/cpp-tutorial/77-default-parameters/](http://www.learncpp.com/cpp-tutorial/77-default-parameters/)

Edit:
 Here's an example of using default arguments, from "Wiley's Teach Yourself C++", 7th edition

```

// Example program 3-6 from "Wiley's Teach Yourself C++, 7th edition

#include <iostream>

// Prototype with default arguments
void show(int = 1, float = 2.3, long = 4);

int main()
{
    show();              // all three arguments default
    show(5);             // provide 1st argument
    show(6, 7.8);        // provide 1st two
    show(9, 10.11, 12L); // provide all three arguments
	return 0;
}

void show(int first, float second, long third)
{
    std::cout << "  first = "  << first;
    std::cout << ", second = " << second;
    std::cout << ", third = "  << third << std::endl;
}

```

---

### Post by Seal Daemon on 2010-05-14
[http://www.lix.polytechnique.fr/~liberti/public/computing/prog/c/C/EXAMPLES/var_func.c](http://www.lix.polytechnique.fr/~liberti/public/computing/prog/c/C/EXAMPLES/var_func.c) - is this what you were looking for ?

---

