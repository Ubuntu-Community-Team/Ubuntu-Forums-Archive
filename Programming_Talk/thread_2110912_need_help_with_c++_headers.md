---
title: "need help with c++ headers"
date: 2013-01-31
forum: Programming Talk
---

### Post by wingnut2626 on 2013-01-31
Ok i am programming in C++ and im trying to implement a header file....here is my code for the main function:

```
#include <iostream>
#include "printsomething.h"

using namespace std;

int main(){

printsomething ps;
return 0;
}
```

and here is my header file (printsomething.h):

```
#ifndef PRINTSOMETHING_H
#define PRINTSOMETHING_H


class printsomething
{
    public:
        printsomething();

};

#endif // PRINTSOMETHING_H

```

here is my header source:

```
#include "printsomething.h"
#include <iostream>

using namespace std;

printsomething::printsomething()
{
    cout << "Don Juan with Don Cannon!" << endl;
}

```

when i try to build and run ( via codeblocks):

I get the error:

**'undefined reference to 'printsomething::printsomething()'**

WHYYYYYYYYYYYY

---

### Post by wingnut2626 on 2013-01-31
that is a double colon btw not a smiley face lol

---

### Post by dwhitney67 on 2013-01-31
> **wingnut2626 said:**
> ]
WHYYYYYYYYYYYY
You have to compile both of your source files.

```

g++ main.cpp printsomething.cpp

```

---

### Post by wingnut2626 on 2013-01-31
how come the codeblocks doesnt do that automatically?  and when i compile them both, it works but still cannot execute....

---

### Post by dwhitney67 on 2013-01-31
I suspect that CodeBlock (CB) is compiling each file, thus producing individual object files.  These two object files should then be linked together to form the executable program.

If this is not transpiring, then undoubtedly there is a configuration issue with your project.

I can only advise you about building projects from the command line; I disdain using an IDE for development, so I personally will not be able to help you with CB.  Perhaps someone else can.

---

### Post by wingnut2626 on 2013-01-31
yes, ive been reading that IDE's are the "lazy man's method" so i think im going to begin to use command line resources to code.  What do you reccommend?

---

### Post by dwhitney67 on 2013-01-31
> **wingnut2626 said:**
> yes, ive been reading that IDE's are the "lazy man's method" so i think im going to begin to use command line resources to code.  What do you reccommend?

I recommend that you use the command line too.

---

### Post by r-senior on 2013-01-31
These commands are all you really need to start with:

[http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

(Example 2 is what you are trying to do at the moment).

Once you are comfortable with those, have a look at 'make' and how to create Makefiles that automate the above. (There is a crude Makefile in the stuff I posted on your Tictactoe thread).

Once you understand 'make' you can move on to the intimidating (but actually not that bad) task of setting up a project with GNU Autotools.

---

### Post by wingnut2626 on 2013-01-31
thanks! ill look into that now. you guys are very helpful!

---

### Post by wingnut2626 on 2013-01-31
And there are no code errors with my code is there?

---

### Post by wingnut2626 on 2013-01-31
Thank you guys so much!  I just compiled it using your way r-senior and it worked!  Thank you thank you thank you!  Until the next time.....(which will be sooner than later).  Another question...i remember someone suggested that i learn python instead of c++...but at this stage would that be detrimental?  Because im already into the c++........

---

### Post by satsujinka on 2013-02-01
> **wingnut2626 said:**
> Thank you guys so much!  I just compiled it using your way r-senior and it worked!  Thank you thank you thank you!  Until the next time.....(which will be sooner than later).  Another question...i remember someone suggested that i learn python instead of c++...but at this stage would that be detrimental?  Because im already into the c++........

If you're having fun, then keep at it!

Especially in the beginning having fun is the most important part. So keep learning C++ and some day when you have time or the desire you can learn python (or whatever language looks interesting to you.)

---

