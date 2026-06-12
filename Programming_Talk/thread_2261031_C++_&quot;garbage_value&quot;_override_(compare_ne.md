---
title: "C++ &quot;garbage value&quot; override (compare new/old libraries)"
date: 2015-01-15
forum: Programming Talk
---

### Post by haplorrhine on 2015-01-15
```
int kook = 1000;
cin>>kook;
cout<<"You entered "<<kook<<".\n";
```

It will return a 0 if I enter a string instead of an integer.
Bjarne & Stroustrup imply that an int prompt, if given a non-integer  value, will revert to a prior default value if provided in the code.   I'm getting the garbage value zero regardless.

---

### Post by spjackson on 2015-01-16
I am pretty sure this behaviour has changed in one of the C++ standards, but I don't recall the details off hand. g++ 4.4.3 with libstdc++6 v4.4.3 prints 1000, whereas g++ 4.8.2 with libstdc++6 v4.8.2 prints 0. Which edition of The C++ Programming Language are you using and which g++/libstc++6 version? If you using a -std flag, then what's the value? If you are using the first edition of TC++PL and a recent g++ and standard then you are likely to find discrepancies.

---

### Post by haplorrhine on 2015-01-16
g++ 4:4.8.2 and libstdc++6 4.8.2.
Is there any way I could switch between versions at will, maybe with a simple directives change?  Then I could distinguish logic errors from library differences.

The Bjarne Stroustrup site gives a list of recommended C++ compilers (that might run separately), some of which are free, but the only one that's explicitly Linux-compatible requires payment.
[http://www.stroustrup.com/compilers.html](http://www.stroustrup.com/compilers.html)

I should note that the book, printed in 2008, uses
```
#include "std_lib_facilities.h"
```

whereas I'm using
```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<cmath>
using namespace std;
```

---

### Post by haplorrhine on 2015-01-26
I'm encountering more similar problems as I move through this book &#8212; titled *Programming: Principles and Practice using C++.*  I'm about 150 pages in, and I can write *exceptions* that work properly, but my programs won't catch the "out_of_range" error from the vector function.  It's assigning this *garbage value* of 0 to the out of range vectors rather than throwing the exception.

```

int main()
{
vector<int> v(5,1);     //the 1 is optional
int i;
cin>>i;
v[i]=v[i]+1;
try{cout<<v[i]<<"\n";}
catch (out_of_range) {cout<<"Oops!\n";};
}

```

In addition to (out_of_range) I have also tried:
(out_of_range_error)
(out_of_range& ex)
(std:: out_of_range)
(std:: out_of_range& ex)
etc.

The program returns a 2 (1+1) if within range, or a 1 (0+1) if out of range.

Also, it wouldn't even compile until I included <stdexcept>. I've also started including <cstdlib> since it's standard. I found all the libraries in /usr/include/c++/4.8/ using the "locate" command.  Unfortunately, I couldn't find the vector function &#8212; to check it for the throw statement&#8212;  since I'm not familiar with the language of the libraries.

---

### Post by spjackson on 2015-01-26
It should not compile without stdexcept being included. So that's ok.

Assuming you are using std::vector rather than some other class that happens to be called "vector", the [] operator does not throw: it provides unchecked access. If you want checked access, use at() which throws.

If [] did throw, then you would get a throw on the line before your try block, which would be an uncaught exception resulting in terminate.

---

### Post by haplorrhine on 2015-01-30
link about the at() function.
[http://www.cplusplus.com/reference/string/string/at/](http://www.cplusplus.com/reference/string/string/at/)

example:

```

string koo = "01234";
cout<<"Enter an index.\n";
int i;
cin>>i;
try{cout<<koo.at(i)<<"\n";}
catch (out_of_range) {cout<<"Oops! Out of range!\n";};

```

It does "catch" the range error, although it isn't quite the same as a vector.  It's limited to single character data points, such as digits.  Furthermore, integers aren't conserved in the int-to-char conversion.

---

