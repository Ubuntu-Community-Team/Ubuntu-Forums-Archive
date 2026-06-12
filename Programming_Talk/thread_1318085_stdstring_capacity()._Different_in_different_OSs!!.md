---
title: "std::string capacity(). Different in different OSs?!?!"
date: 2009-11-07
forum: Programming Talk
---

### Post by Swerve1000 on 2009-11-07
Hi, I have a question.

Using the following code:

```

#include <iostream>
int main()
{
	std::string s1;
	std::cout << s1.capacity() << std::endl;

	system ("PAUSE");
	return 0;
}

```

In Ubuntu/KDevelop the output is 0.

In Windows/V.Studio the output is 15.

Can anyone suggest why it happens?

I'm somewhat stumped by it's occurrence.

Thanks very much, much appreciated.

---

### Post by dwhitney67 on 2009-11-07
Happy reading:
[http://www.cplusplus.com/reference/string/string/capacity/](http://www.cplusplus.com/reference/string/string/capacity/)

P.S.  You should include <string> in your code.

---

### Post by MadCow108 on 2009-11-07
the default capacity is implementation dependent (as a lot of other stuff concerning strings, like structure size, reference counting, number of dynamic allocations etc.)
so its no surprise that you see differences in different systems.

as with the 15 default size it is very well possible that the 15 spaces can be used without a dynamic allocation because they fit into the structure of string itself. But you'll have to look that up in the implementation docs to be sure.

If you need smaller or bigger starting capacity just call the appropriate constructor

---

