---
title: "[SOLVED] Compiling c++ program"
date: 2008-11-13
forum: Programming Talk
---

### Post by Despot Despondency on 2008-11-13
Hi, I just started learning c++ and I'm trying to compile the following program

```

#include <iostream>

int main()
{
  std::cout << "Hello, world!" << std::endl;
  return 0;
}

```

Now when I try 

```

gcc -o  helloWorld helloWorld.c

```

I get the following error

```

helloWorld.c:1:20: error: iostream: No such file or directory
helloWorld.c: In function ‘main’:
helloWorld.c:5: error: expected expression before ‘:’ token

```

I have gcc and build-essential already installed and I've tried using <iostream.h> instead of <iostream>, but to no avail. Any help would be appreciated.

---

### Post by rbprogrammer on 2008-11-13
Your code, you need to do one of two things.  Make the header file:
```
#include <iostream.h>
```
or include the standard namespace globally, ie:
```
#include <iostream>
using namespace std;
```

---

### Post by cmay on 2008-11-13
use[php] g++  -o hello ./hello.cpp[/php]not [php]gcc -o hello ./hello.cpp[/php]gcc is the gcc compiler.

---

### Post by rbprogrammer on 2008-11-13
> **cmay said:**
> use[php] g++  -o hello ./hello.cpp[/php]not [php]gcc -o hello ./hello.cpp[/php]gcc is the gcc compiler.

Hahaha, yup that would solve the problem too. Good eye, cmay

---

### Post by stevescripts on 2008-11-13
use g++ to compile c++ source files - check this link:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html]("http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html")

Hope this helps a bit.

Steve
(who appears to be too slow this pm)

---

### Post by rbprogrammer on 2008-11-13
Also, not that this would matter too much on how things will work, but your file seems to have a C file extension (.c), rather than the C++ extension (.cpp).  But again, that would not affect your error message, but it is good practice to keep good file extensions, especially if you have a project that combines both C and C++ together.

---

### Post by stevescripts on 2008-11-13
Took me a couple of minutes to remember - but an alternative is to include the stdc++
lib on the command line as an option:

```

steveo@delldesktop:~$ gcc hw.cpp -o hello -lstdc++
steveo@delldesktop:~$ ./hello
Hello, world!

```


(BTW, If I recall correctly, the use of iostream.h is deprecated -
I do very little compiled language programming anymore)
Steve

---

### Post by Despot Despondency on 2008-11-13
Hi, thanks everyone. I didn't realize that c++ programs had to be compiled with the g++ command and not gcc. Cheers again.

---

