---
title: "Problems with a C++ tutorial"
date: 2008-03-20
forum: Programming Talk
---

### Post by wiscados on 2008-03-20
I'm in the process in teaching myself C++ by following [this book]("http://openbookproject.net//thinkCS/cpp/english/index.htm").

I am now at chapter 7, "Strings and things", and I have a problem.

> 7.2 pstring variables

You can create a variable with type pstring in the usual ways:
  pstring first;
  first = "Hello, ";
  pstring second = "world.";

The first line creates an pstring without giving it a value. The second line assigns it the string value "Hello." The third line is a combined declaration and assignment, also called an initialization.

Normally when string values like "Hello, " or "world." appear, they are treated as C strings. In this case, when we assign them to an pstring variable, they are converted automatically to pstring values.

We can output strings in the usual way:
  cout << first << second << endl;

In order to compile this code, you will have to include the header file for the pstring class, and you will have to add the file pstring.cpp to the list of files you want to compile. The details of how to do this depend on your programming environment.

Before proceeding, you should type in the program above and make sure you can compile and run it.

My problem is with pstring. I have searched the net and only found very little about pstring. I found a source three of pstring on [gna.org]("http://svn.gna.org/viewcvs/ndv/trunk/src/pbase/") and tried to the best of my ability to get it working, but I could not.

When I compile just pstring.cpp I get this error message:
> $ g++ pstring.cpp
pstring.h:71: error: extra qualification &#8216;PString::&#8217; on member &#8216;hash&#8217;


When I compile just str.cpp I get:
> $ g++ str.cpp -o str :
str.cpp:5: error: &#8216;pstring&#8217; was not declared in this scope
str.cpp:5: error: expected `;' before &#8216;first&#8217;
str.cpp:6: error: &#8216;first&#8217; was not declared in this scope
str.cpp:7: error: expected `;' before &#8216;second&#8217;
str.cpp:9: error: &#8216;second&#8217; was not declared in this scope


"g++ pstring.cpp str.cpp -o str" gives both error messages.


Any help would be much appreciated.

--
An other question: How common is pstring?


EDIT:
Here's my source.
```
#include <iostream.h>

int main ()
{
  pstring first;
  first = "Hello, ";
  pstring second = "world.";

  cout << first << second << endl;
  return 1;
}
```

---

### Post by mike_g on 2008-03-20
I havent seen pstring either. Maybe its a custom class inheriting string properties the author made or something? Have you tried just using the standard string class instead?

IE: removing the 'p's

Edit: for strings you will also need to stick:
```
using namespace std;
```
before main, OR prefix them each time with std::

---

### Post by LaRoza on 2008-03-20
[php]#include <iostream>

int main (void)
{
  std::pstring first;
  first = "Hello, ";
  std::pstring second = "world.";

  std::cout << first << second << std::endl;
  return 1;
}[/php]

I never heard of pstring, but I know of "string", so I don't know if that will compile. If it doesn't, replace "pstring" with "string"

(It doesn't work on my end, use "string")

---

### Post by WW on 2008-03-20
> **wiscados said:**
> 
An other question: How common is pstring?

I've never heard of it until now.  I don't know if that is a good book or not, but I would recommend finding one that uses the standard **string** C++ class.

---

### Post by LaRoza on 2008-03-20
> **WW said:**
> I've never heard of it until now.  I don't know if that is a good book or not, but I would recommend finding one that uses the standard **string** C++ class.

Note: the OP used iostream.h, not iostream. pstring isn't in iostream, which should be used.

@OP You are using an outdated and possibly non standard tutorial. See my wiki for a better one.

---

### Post by wiscados on 2008-03-20
Thanks all!!

This worked.
```
#include <iostream>

int main ()
{
  std::string first;
  first = "Hello, ";
  std::string second = "world.";

  std::cout << first << second << std::endl;
  return 1;
}


```

And also I diged on the Open Book Project page and found [this]("http://openbookproject.net/thinkCS/cpp.php"), > English
[ html tarball | ps | LaTeX ] (updated 08/07/01)
2001!! It's waaay outdated, I didn't know that. Now I know why the email I sent to the maintainer bounced.

---

### Post by wiscados on 2008-03-20
> **LaRoza said:**
> @OP You are using an outdated and possibly non standard tutorial. See my wiki for a better one.

I looked at you page and at the top of the "Learning" list on the C++ page is the book that I used: How to Think Like a Computer Scientist: C++ Version.

There was an other book that looked interesting: Thinking in C++. But that assumed you knew C first, which I don't. 

Then there's a tutorial on cprgramming.com which looks promising and I'll be going through. Unless someone has a better suggestion...

---

### Post by LaRoza on 2008-03-20
> **wiscados said:**
> I looked at you page and at the top of the "Learning" list on the C++ page is the book that I used: How to Think Like a Computer Scientist: C++ Version.

There was an other book that looked interesting: Thinking in C++. But that assumed you knew C first, which I don't. 

Then there's a tutorial on cprgramming.com which looks promising and I'll be going through. Unless someone has a better suggestion...

In the header for each language (above the lists of links) there is a  "Learn <language" link, that I recommend for each language. 

This was that link: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by DublinPCservices on 2008-03-20
> **wiscados said:**
> I'm in the process in teaching myself C++ by following [this book]("http://openbookproject.net//thinkCS/cpp/english/index.htm").

I am now at chapter 7, "Strings and things", and I have a problem.



My problem is with pstring. I have searched the net and only found very little about pstring. I found a source three of pstring on [gna.org]("http://svn.gna.org/viewcvs/ndv/trunk/src/pbase/") and tried to the best of my ability to get it working, but I could not.

When I compile just pstring.cpp I get this error message:


When I compile just str.cpp I get:


"g++ pstring.cpp str.cpp -o str" gives both error messages.


Any help would be much appreciated.

--
An other question: How common is pstring?


EDIT:
Here's my source.
```
#include <iostream.h>

int main ()
{
  pstring first;
  first = "Hello, ";
  pstring second = "world.";

  cout << first << second << endl;
  return 1;
}
```

The .cpp and .h for pstring are defined in either chapter 1-6.
When you find that, be sure to include the header for pstring.
It's mostly like a very basic class.

---

### Post by wiscados on 2008-03-20
> **LaRoza said:**
> In the header for each language (above the lists of links) there is a  "Learn <language" link, that I recommend for each language. 

This was that link: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

That one looks pretty good too. I think I'll read the first few chapters of each to get a feel of them and see which I like best.

---

### Post by samjh on 2008-03-20
pstring.h is a C++ string library specifically for the US Computer Science AP exam.

I'd rather recommend the tutorial at [www.cplusplus.com](www.cplusplus.com) someone else posted earlier: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Also recommended is: [http://www.amazon.com/Accelerated-Practical-Programming-Example-Depth/dp/020170353X](http://www.amazon.com/Accelerated-Practical-Programming-Example-Depth/dp/020170353X)

---

### Post by pmasiar on 2008-03-20
> **wiscados said:**
> There was an other book that looked interesting: Thinking in C++. But that assumed you knew C first, which I don't. 


Thinking in.... series are for advanced programmers, explains how stuff works "under the hood" , design decisions made when designing language, and deeper consequences.

Is C++ your first language?

---

