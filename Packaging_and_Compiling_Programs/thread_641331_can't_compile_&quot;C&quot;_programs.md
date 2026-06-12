---
title: "can't compile &quot;C&quot; programs"
date: 2007-12-15
forum: Packaging and Compiling Programs
---

### Post by dleroy on 2007-12-15
I am using "Gusty" and trying to compile this  very basic program 
"C" program named hello.c 

#include <iostream>

int main()

{
cout << "Hello World \n ";
return 0;
}

 I get the following error :

leroy@ub4:~/c++$ gcc hello.c
hello.c:1:20: error: iostream: No such file or directory
hello.c: In function ‘main’:
hello.c:6: error: ‘cout’ undeclared (first use in this function)
hello.c:6: error: (Each undeclared identifier is reported only once
hello.c:6: error: for each function it appears in.)

I have checked the library paths for the compiler and it uses /usr/include/c++/4.1.3 which includes the header iostream
no matter which compiler I try , c++,cpp,gpp,g++ I get various errors , all of which are related to header files. I read lots of posts about various compiler problems with Ubuntu. Can you actual compile code "C" on this Ubuntu system.  The build-essentials is installed and many other things which the posts say is a problem have also given no results.  Does this work ?? . Show an example of some actual code compiled on this OS.

Thanks

---

### Post by komputes on 2007-12-15
I'm no programmer, by any means, but I think it may be "count" instead of "cout" and I think you need to tell it where <iostream> is located (the full path) or you need to put it in the same directory as hello.c

Hope it helps (then again, I'm not sure if I know what I'm talking about)

---

### Post by rbprogrammer on 2007-12-15
well, first of all, that program is not C code, its C++ code. a hello world C program would look like this:

file: ~/hello.c
```

#include <stdio.h>
int main(int argc, char *argv[])
{
    printf("Hello World!\n");
    return 0;
}

```
then compile with:
```

gcc ~/hello.c

```

---

### Post by rbprogrammer on 2007-12-15
oh, i just realized this, your code is this:
```

#include <iostream>
int main()
{
    cout << "Hello World \n ";
    return 0;
}

```
this is C++ code, but it wont work since you did not put the .h at the end of iostream.  but this is good.  a standard way of creating C++ programs is to leave the .h out and then add this line:
file: ~/hello.cpp
```

#include <iostream>
**using namespace std;**
int main()
{
    cout << "Hello World \n ";
    return 0;
}

```
then compile with:
```

g++ ~/hello.cpp

```

---

### Post by Compyx on 2007-12-16
All of this doesn't solve the missing headers.

```

sudo apt-get install build-essential

```
will do the trick.

---

### Post by dleroy on 2007-12-16
Thanks for the input ,
 It worked fine. 
 I guess I can venture to the "C" program learning.  At 73 years old and still learning.  I know Basic, Fortran, Cobol and assembler, now I will try "c" coding.

Thanks for all the help

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by gjaffe on 2007-12-16
> **dleroy said:**
> Thanks for the input ,
 It worked fine. 
 I guess I can venture to the "C" program learning.  At 73 years old and still learning.  I know Basic, Fortran, Cobol and assembler, now I will try "c" coding.

Thanks for all the help

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Wow, you probably started before me.  I also started with Basic, Fortran, Cobol and assembler (BAL 360).  I'm 55 and started programming in 1970.

You might want to look at Python in addition to C.  I'm not trying to start a flame war here, but I've written many programs in C, and now I write almost everything in Python.  It's an interpretive language like Basic and even has a shell for playing around with it, like Basic.  Just type python at the command line.  To get out type control-D.  I find it much more forgiving (and enjoyable) than writing in C.

But again.  No flame war here.  C is a very powerful language and much faster than Python.

Gary

---

