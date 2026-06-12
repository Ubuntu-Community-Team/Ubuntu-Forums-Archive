---
title: "[C++] find a char into a string"
date: 2010-11-12
forum: Programming Talk
---

### Post by erotavlas on 2010-11-12
Hi,

I would like to find a char into a string. I have written the following code 

```

int CharCounter(std::string & input) {
    size_t found;
    int count = 0;
    found=input.find_first_of("()");
    while (found != std::string::npos) {
        found=input.find_first_of("()", found+1);
        count++;
    }
    return count;
}



int main ()
{
   string str ("A()(d1,d2)");
    int c = CharCounter(str);     
        
    cout << c << endl;
  
  return 0;
}


```Is there a better way?

Thank you

---

### Post by spjackson on 2010-11-12
> **erotavlas said:**
> Is there a better way?

It looks a perfectly reasonable way to me.

If you were looking for a single value, then std::algorithm::count could be considered. You could call count once for each of "(" and ")", but that means scanning the input twice. You could also use std::algorithm::count_if, but you'd need to set up a functor as the predicate, which I'd regard as overly complex in this case.

---

### Post by worksofcraft on 2010-11-12
To me it just doesn't feel right that you are doing a find_first_of both outside and inside the loop and also that the characters you search for are thus in two places. OTOH I think that it's not very likely to ever cause problems with such a simple loop :P

---

### Post by GeneralZod on 2010-11-12
> **spjackson said:**
> You could also use std::algorithm::count_if, but you'd need to set up a functor as the predicate, which I'd regard as overly complex in this case.

If usage of boost is an option, it can be made blissfully simple:

```

#include <boost/lambda/lambda.hpp>
#include <algorithm>
#include <iostream>

using namespace boost::lambda;
using namespace std;

int main()
{
    const string str ("A()(d1,d2)");
    const int numBrackets = count_if(str.begin(), str.end(), _1 == '(' || _1 == ')');

    cout << numBrackets << endl;

    return 0;
}

```

Edit:

Woah - blazing fast at -O2, too!

---

### Post by interval1066 on 2010-11-12
This is hardly rocket science. This is probably the fastest way of doing it short of inline assembler, and no 3rd party library needed;
```

int nlParen = 0;
const char *p = str.c_str();
for(int n = 0; n < str.length(); n++)
if(*(p + n) == '(') nlParen++;

```
Prolly better to copy the contents of str into a char array, pointers to std objects can be a little tricky.

---

### Post by spjackson on 2010-11-12
> **interval1066 said:**
> This is hardly rocket science. This is probably the fastest way of doing it short of inline assembler, and no 3rd party library needed;
```

int nlParen = 0;
const char *p = str.c_str();
for(int n = 0; n < str.length(); n++)
if(*(p + n) == '(') nlParen++;

```Prolly better to copy the contents of str into a char array, pointers to std objects can be a little tricky.
There's absolutely no point whatsoever in copying the string. It would also probably be better to deliver the same functionality as the original post.

---

### Post by interval1066 on 2010-11-12
You don't think using a char pointer would be faster than using a string object?

---

### Post by dwhitney67 on 2010-11-12
Another way, but based on the original:
```

int CharCounter(const std::string& input, const char* delim)
{
    size_t count = 0;
    size_t found = 0;
    while ((found = input.find_first_of(delim, found)) != std::string::npos)
    {
       ++found;
       ++count;
    }
    return count;
}

```

---

### Post by spjackson on 2010-11-13
> **interval1066 said:**
> You don't think using a char pointer would be faster than using a string object?
Not if you include the cost of copying it in the first place.

---

