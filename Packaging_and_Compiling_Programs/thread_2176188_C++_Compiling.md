---
title: "C++ Compiling"
date: 2013-09-23
forum: Packaging and Compiling Programs
---

### Post by sverrirkr on 2013-09-23
Hi

Sorry for the total newbie question here, couldn't find answer with Google.

Here's my C++ code:
```
#include <iostream>
using namespace std;

int main()
{
  int a;

  cout << "hello world \n";
  cin >> a;

  return 0;
}
```

And here's my output:
```
svkrlin@ubuntu:~/cplusplus$ gcc helloworld.cpp
/tmp/cceUc2pD.o: In function `main':
helloworld.cpp:(.text+0xe): undefined reference to `std::cout'
helloworld.cpp:(.text+0x13): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
helloworld.cpp:(.text+0x1f): undefined reference to `std::cin'
helloworld.cpp:(.text+0x24): undefined reference to `std::istream::operator>>(int&)'
/tmp/cceUc2pD.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld.cpp:(.text+0x5c): undefined reference to `std::ios_base::Init::Init()'
helloworld.cpp:(.text+0x6b): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cceUc2pD.o:(.eh_frame+0x13): undefined reference to `__gxx_personality_v0'
collect2: error: ld returned 1 exit status

```

build-essential is installed, but I'm making some fundamental (newbie) error.

What is it?

Using Ubuntu 13.04 64bit.

---

### Post by apmcd47 on 2013-09-23
Just a simple one:
```
$[COLOR="#FF0000"] g++[/COLOR] helloworld.cpp 
$ ./a.out 
hello world 
hello you

```
You used gcc instead of g++. I would have said it thought it was compiling C code rather than C++ but I'm not sure what is going on there.

Andrew

---

### Post by sverrirkr on 2013-09-23
I'm getting no output whatsoever from g++.

Just looking to get things started with any simple C++ file.

---

### Post by UlTroX2000 on 2013-09-23
If you get no output after compiling the file with g++ everything went right.
Type ```
./a.out
``` to run your program (a.out is the default filename for g++, if you don't specify one with the -o flag).

---

### Post by sverrirkr on 2013-09-23
Ok, it did work after all.

But mainly I want to use emacs in the future.

When I run
```
M-x compile RET g++ -o helloworld.cpp RET
```
I get
```
-*- mode: compilation; default-directory: "/home/svkrlin/cplusplus/" -*-
Compilation started at Mon Sep 23 11:49:46

g++ -o helloworld.cpp
g++: fatal error: no input files
compilation terminated.

Compilation exited abnormally with code 4 at Mon Sep 23 11:49:46
```

---

### Post by steeldriver on 2013-09-23
The -o switch specifies the OUTPUT file (i.e. what you want the compiled executable to be called) - if you name the output file the same as the source (.cpp) file it will overwrite it with an empty file

---

### Post by UlTroX2000 on 2013-09-23
I know nothing about emacs, but the problem with your code is that you did not specify a filename for the -o flag. The flag has to be followed by the name you want your executable to have and then the files you want to compile, e.g.
```
g++ -o myFilename myFile.cpp
```
So in your case the compiler took helloworld.cpp as the filename and didn't have any file left to compile.

---

### Post by sverrirkr on 2013-09-23
So, how do I make the output appear in the terminal window, or the other buffer in emacs?

---

### Post by steeldriver on 2013-09-23
The output of the compile command should appear in a new buffer automatically. If you want to run the resulting executable from within emacs, you can do that by invoking a shell (M-!) and then giving the name of the executable (with relative path ./ so that the shell can find it)

```
M-! ./myFilename
```

---

### Post by oldos2er on 2013-09-23
Moved to Packaging & Compiling Programs.

---

### Post by sverrirkr on 2013-09-23
> **steeldriver said:**
> The output of the compile command should appear in a new buffer automatically. If you want to run the resulting executable from within emacs, you can do that by invoking a shell (M-!) and then giving the name of the executable (with relative path ./ so that the shell can find it)

```
M-! ./myFilename
```

For some reason, the output doesn't appear in the other buffer:
```
-*- mode: compilation; default-directory: "/home/svkrlin/cplusplus/" -*-
Compilation started at Mon Sep 23 17:46:45

g++ -o myfile helloworld.cpp 

Compilation finished at Mon Sep 23 17:46:46

```

I did however open up a shell and ./myfile works, but it's a bit inconvenient that I have to compile first in the file buffer and then switch to the buffer to run another command.

---

### Post by sverrirkr on 2013-09-23
Ok, I think I get it now. The compile command is not compile and execute, just compile the execution file, if that makes sense.

Then, I have to execute the file seperately.

---

