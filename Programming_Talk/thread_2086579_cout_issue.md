---
title: "cout issue"
date: 2012-11-21
forum: Programming Talk
---

### Post by toontastic on 2012-11-21
I've decided to try and learn a programming language. I used C++ many moons ago at Uni and thought if I'm going to start somewhere might as well be there. So I've installed Eclipse along with the extra C++ files. I've have written the following code:

```
#include <iostream.h>
#include "stdafix.h"

int main()
{
	cout << "Hello World!\n";
		return 0;
}

```

which I assumed would simply work. Unfortunatly I get the error '"Symbol 'cout' could not be resolved." - Resource hello.cpp, path /hello, line 12, Type semantic error'.
I figured it would be something I had written wrong so I rang the C++ Hellow World example that comes in Eclipse but this also fails to run with the same error. 

Have I missed something somewhere ? :confused: 

Thanks.

---

### Post by ssam on 2012-11-21
cout is in the std namespace. either you need to give the full address to it
```
std::cout << "Hello World!\n";
```
or you can put
```
using namespace std
```
after the includes, to tell the compile to search std for identifiers.

---

### Post by steeldriver on 2012-11-21
I think your confusion arises because <iostream[COLOR=Red]**.h**[/COLOR]> is non-standard (and deprecated - in fact I'm not even sure it's included in modern distributions) - iirc it predated the adoption of namespaces so plain 'cout' used to work back in the day

You should probably be using <iostream> (without the .h) - in which case you will need to specify the namespace, as ssam says

```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}
```

See article here for more info / background --> [http://members.gamedev.net/sicrane/articles/iostream.html](http://members.gamedev.net/sicrane/articles/iostream.html)

EDIT: not sure what your "stdafix.h" is - maybe you are trying to mimic Visual Studio's "stdafx.h" convention?

---

### Post by toontastic on 2012-11-22
Thank you both very much for your help. Seems it was further back when I used it than my brain cells first thought. That has worked perfectly for me thanks. 
As for the stdafix.h, I found it in a C++ ebook I was reading and it was suggested as part of the test code for Hello World so I wasn't sure if it was something I was missing. Needless to say I have not stuck with that book.

---

### Post by toontastic on 2012-11-22
> **toontastic said:**
> Thank you both very much for your help. Seems it was further back when I used it than my brain cells first thought. That has worked perfectly for me thanks. 
As for the stdafix.h, I found it in a C++ ebook I was reading and it was suggested as part of the test code for Hello World so I wasn't sure if it was something I was missing. Needless to say I have not stuck with that book.

Actually I was wrong, that hasn't worked either. Still getting an error about cout. If I try to build the code I get.

```
**** Build of configuration Debug for project Hello ****

make all 
Building file: ../hello.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"hello.d" -MT"hello.d" -o "hello.o" "../hello.cpp"
../hello.cpp: In function ‘int main()’:
../hello.cpp:6:2: error: ‘cout’ was not declared in this scope
../hello.cpp:6:2: note: suggested alternative:
In file included from ../hello.cpp:1:0:
/usr/include/c++/4.7/iostream:62:18: note:   ‘std::cout’
```

What I now have written is 

```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}


```

---

### Post by SuperCamel on 2012-11-22
There is nothing wrong with that code. It should just compile and run. There must be something else going wrong.

---

### Post by steeldriver on 2012-11-22
Agreed - it builds and runs for me [NB on gcc/g++ 4.6.3 not 4.7] even with all of your extra compile options

How did you install the build tools? maybe something is misconfigured?

EDIT: just tried it in a crunchbang (Debian) VM with gcc/g++ 4.7.1 and it works there as well

---

### Post by lisati on 2012-11-22
@OP: Do you have build-essential installed?

---

### Post by Zugzwang on 2012-11-23
> **toontastic said:**
> Actually I was wrong, that hasn't worked either. Still getting an error about cout. If I try to build the code I get.

```
**** Build of configuration Debug for project Hello ****

make all 
Building file: ../hello.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"hello.d" -MT"hello.d" -o "hello.o" "../hello.cpp"
../hello.cpp: In function &#8216;int main()&#8217;:
../hello.cpp:6:2: error: &#8216;cout&#8217; was not declared in this scope
../hello.cpp:6:2: note: suggested alternative:
In file included from ../hello.cpp:1:0:
/usr/include/c++/4.7/iostream:62:18: note:   &#8216;std::cout&#8217;
```

What I now have written is 

```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}


```

Are you sure that you pasted the correct contents of "hello.cpp"? Your compilation error message says that "cout" was not declared in line 6, but line 6 is actually "return 0;". Is it possible that in fact your IDE tries to compile your old code?

---

### Post by toontastic on 2012-11-24
> **lisati said:**
> @OP: Do you have build-essential installed?

Not sure, I installed all the extras that mentioned C++

---

### Post by toontastic on 2012-11-24
> **Zugzwang said:**
> Are you sure that you pasted the correct contents of "hello.cpp"? Your compilation error message says that "cout" was not declared in line 6, but line 6 is actually "return 0;". Is it possible that in fact your IDE tries to compile your old code?

Hmmmm not sure, I'll try again deleting everything and creating a new project and let you know.

---

### Post by toontastic on 2012-11-24
Right tried again, I had it set to Build Automatically so didn't get the build error but got the error 

Description	Resource	Path	Location	Type
Symbol 'cout' could not be resolved	brandnew.cpp	/Brand New	line 5	Semantic Error

Code I used was ```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}


```

---

### Post by steeldriver on 2012-11-24
> **toontastic said:**
> Right tried again, I had[COLOR=Red] it set to Build Automatically[/COLOR] so didn't get the build error but got the error 

[COLOR=Red]Description    Resource    Path    Location    Type
Symbol 'cout' could not be resolved    brandnew.cpp    /Brand New    line 5    Semantic Error[/COLOR]

Code I used was ```
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}


```

So you are using some kind of IDE (code::blocks maybe?) - what happens if you just open a terminal, cd to the directory containing the file 'brandnew.cpp', and try to compile and link on the command line

```
g++ -o brandnew brandnew.cpp
```

---

### Post by toontastic on 2012-11-24
Ok I did 

cd Brand\ New

Then I wrote

g++ -o brandnew brandnew.cpp 

and I got no response at all. So I tried 

g++ -o brandnew.cpp 

and I got the error 
```
g++: fatal error: no input files
compilation terminated.

```

---

### Post by steeldriver on 2012-11-24
g++ will give no response if compilation succeeds - basically that means there were no errors and it was able to resolve std::cout correctly

Unfortunately

```
g++ -o brandnew.cpp 
```probably overwrote your source code file (-o means **o**utput so it will try to create the executable program but give it the name 'brandnew.cpp' instead of plain 'brandnew')

I suggest creating the .cpp file again,  running

```
g++ -o brandnew brandnew.cpp 
```and then checking if the executable was produced

```
ls -l
```and if so trying to run it

```
./brandnew
```BTW if your IDE uses Makefiles under the hood you may run in to trouble if your build directory name contains spaces - just a heads up

---

### Post by toontastic on 2012-11-24
> **steeldriver said:**
> g++ will give no response if compilation succeeds - basically that means there were no errors and it was able to resolve std::cout correctly

Unfortunately

```
g++ -o brandnew.cpp 
```probably overwrote your source code file (-o means **o**utput so it will try to create the executable program but give it the name 'brandnew.cpp' instead of plain 'brandnew')

I suggest creating the .cpp file again,  running

```
g++ -o brandnew brandnew.cpp 
```and then checking if the executable was produced

```
ls -l
```and if so trying to run it

```
./brandnew
```BTW if your IDE uses Makefiles under the hood you may run in to trouble if your build directory name contains spaces - just a heads up


Oooooo excellent that worked I was able to finally see Hello World! :guitar:
Ok I'll make sure I leave out the spaces now.

Right it seems I've done something funny in terms of IDEs in Eclipse. Is there a way to fix this so I don't have to use terminal and can infact just run the programs in Eclipse ?

---

### Post by toontastic on 2012-11-24
Ok very strangly after doing that in terminal it now builds fine and returns Hello World! in Eclipse as well now. 

Thank you all very much for your help.

---

