---
title: "C++ standards and Ubuntu"
date: 2009-06-02
forum: Programming Talk
---

### Post by Chrus on 2009-06-02
Im teaching myself how to program in C++ and im getting a little confused.

C++ has a set of standards, right? Im using g++ to compile my programs. Does g++ comply with these standards, or does it do things a bit differently?

The reason I ask... Take this for example

```
1: #include <iostream.h>
2:
3: int main()
4: {
5:    cout << "Hello World!\n";
6:        return 0;
7: } 

```

from every thing ive been reading on the net, that looks like it pretty much complies with C++ standards. But in ubuntu, to get that to work i need to drop the ".h" in line 1 and add "std::" to the beginning of line 5 before "cout".

So whats the go? is the standard a little flexible? are programs i write in ubuntu going to compile on other compilers, or will i have to go in and edit code? Am i going to teach myself bad habbits if i learn in ubuntu?

Cheers

Chrus

---

### Post by x33a on 2009-06-02
gcc follows ansi standards, and the programs should compile on any unix system.

and put this line in every program, under the headers and you won't have to put std before every cout.

> using namespace std;

---

### Post by ad_267 on 2009-06-02
You are going to teach yourself bad habits if you use websites that tell you to write C++ like that. If you write ANSI C++ you won't have any problem compiling with different compilers on different operating systems.

---

### Post by Chrus on 2009-06-02
Well I was using [http://newdata.box.sk/bx/c/index.htm]("http://newdata.box.sk/bx/c/index.htm")... It looked like a well written site... but i guess not? Guess ill have to find another site, eh?

Cheers

---

### Post by samjh on 2009-06-02
> **Chrus said:**
> ```
1: #include <iostream.h>
2:
3: int main()
4: {
5:    cout << "Hello World!\n";
6:        return 0;
7: } 

```

from every thing ive been reading on the net, that looks like it pretty much complies with C++ standards. But in ubuntu, to get that to work i need to drop the ".h" in line 1 and add "std::" to the beginning of line 5 before "cout".

Your information is wrong.

The standard form for that program is this:
```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}
```

In C++, system header files are written without .h at the end, and you need to define the namespace for your standard functions and objects, such as cout (the namespace for that is std, hence the reason why you need to prefix the cout with std::[noparse])[/noparse]

The program may also be written as (in accordance with the standard):
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello World!\n";
    return 0;
}
```
or
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello World!" << endl;
    return 0;
}
```
or
```
#include <iostream>

int main()
{
    using std::cout;
    using std::endl;

    cout << "Hello World!" << endl;

    return 0;
}
```...among other variations.

I suggest: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) for a tutorial on C++, and [http://www.cppreference.com/wiki/](http://www.cppreference.com/wiki/) for function references.  Also look at [http://www.icce.rug.nl/documents/cplusplus/](http://www.icce.rug.nl/documents/cplusplus/) for more detailed information on C++ usage.

---

### Post by ad_267 on 2009-06-02
It's just an old site, there was a lot of stuff which was changed before the standard was finalised. This includes the removal of the ".h" and the use of namespaces.

---

### Post by Chrus on 2009-06-02
So, without making you read the entire guide on that site, does that look like something i could work with as long as i keep in mind the .h and the std things? Or am i gonna come across more problems later on? Should i find another site?

---

### Post by Ulrik04 on 2009-06-02
The site seems old, with code that doesn't follow today's standarts. I would find another that followed the newer standarts, learning the old ones could lead to confusion.
You can also buy a book from amazon, books are generally better than online tutorials in my opinion.

---

### Post by ad_267 on 2009-06-02
I'd say find another site. You might be ok using that one, but you could run into a few more problems. I used a book myself, but I'm sure there must be plenty of good up to date sites out there. The cpluplus.com one looks pretty good.

---

### Post by krazyd on 2009-06-02
> **Chrus said:**
> So, without making you read the entire guide on that site, does that look like something i could work with as long as i keep in mind the .h and the std things? Or am i gonna come across more problems later on? Should i find another site?
I'd advise getting a book, purely from my own experience of finding online resources incomplete, poorly written, and almost always containing code of questionable quality.
The book I picked up was [Accelerated C++]("http://www.acceleratedcpp.com/") and it's just fantastic. Couldn't recommend it highly enough.

---

### Post by abhilashm86 on 2009-06-02
using namespaces in c++ has lot of advantages, you can assign same function name in headers and access them.

---

### Post by Chrus on 2009-06-02
Thanks guys. I appreciate the help.

Guess ill look into getting a book then.

---

