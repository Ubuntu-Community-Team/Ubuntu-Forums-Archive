---
title: "C++ double to string drops final zeroes"
date: 2009-11-29
forum: Programming Talk
---

### Post by jondiced on 2009-11-29
Hi helpful Ubuntu-ers,

I'm trying to convert doubles to strings in order to dynamically generate new filenames. My code works well except that my conversion function drops the trailing 0's from my doubles. For example, 3.0 becomes 3 after being converted to a string. I would like to keep the 0's. 


Here is my code: 
[PHP]
string dtos(double dbl)
{
  ostringstream strs;
  strs << dbl;
  string str = strs.str();

  return str;
}
[/PHP]

Thanks for your help! I'd be grateful even if you just point me to the right resource to read. Unfortunately, I've hit the limit of my patience today for searching through unhelpful documentation :-/

---

### Post by MadCow108 on 2009-11-29
```

#include <iomanip>
sstream ss;
double d = 3.0;
ss << fixed << setprecision(3) << d;

```
output: 3.000
[http://www.cplusplus.com/reference/iostream/manipulators/fixed/](http://www.cplusplus.com/reference/iostream/manipulators/fixed/)
[http://www.cplusplus.com/reference/iostream/manipulators/setprecision/](http://www.cplusplus.com/reference/iostream/manipulators/setprecision/)

I don't recall of a quick method to just get a single zero with a higher precision setting. You'll probably have to parse the string for that.

---

### Post by jondiced on 2009-11-30
Hi MadCow108, thanks for the quick reply! I haven't had time to test it yet, but I'll let you know if it worked as soon as I do.

---

### Post by jondiced on 2009-11-30
Great, that totally worked. I want all the numbers to be of equal length, so different numbers of 0's isn't a problem. Here is my new code: 

[php]
#include <iomanip>

string dtos(double dbl)
{
  ostringstream strs;
  strs << fixed << setprecision(3) << dbl; // the only line I changed
  string str = strs.str();

  return str;
}
[/php]

Thanks so much for your help!

---

