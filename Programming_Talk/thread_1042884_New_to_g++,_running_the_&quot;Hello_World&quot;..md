---
title: "New to g++, running the &quot;Hello World&quot;."
date: 2009-01-18
forum: Programming Talk
---

### Post by Swerve1000 on 2009-01-18
Hi there :)

I'm trying to use g++, but am experiencing some difficulty despite following what the tutorials describe. I must be going wrong somewhere.

I am using Ubuntu 8.10 32bit Desktop.

I first open a Terminal and then enter:

```
gedit myhello.cpp
```

Into the editor I enter:

```

#include <iostream>

using namespace std;

int main()
{
int a = 0;
cout << "enter a number";
cin >> a;

return 0;
}

```

I then click save, which then re-activates the Terminal window, so I see the following:

```

me@me-desktop:~$ gedit myhello.cpp
me@me-desktop:~$ 


```

Then to compile the program I enter into the terminal:

```
gcc myhello.cpp -o myhello
```


Which gives the following output:

```

/tmp/ccz6Pxs1.o: In function `__static_initialization_and_destruction_0(int, int)':
myhello.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
myhello.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccz6Pxs1.o: In function `main':
myhello.cpp:(.text+0x7f): undefined reference to `std::cout'
myhello.cpp:(.text+0x84): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
myhello.cpp:(.text+0x92): undefined reference to `std::cin'
myhello.cpp:(.text+0x97): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
/tmp/ccz6Pxs1.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
me@me-desktop:~$ 




```

I attempt to run the program by entering:


```
myhello
```

which gives:

```
bash: myhello: command not found
```

and also when I try:


```
./myhello
```

It also gives:


```
bash: ./myhello: No such file or directory 
```

I'm clearly doing something wrong, but from what I have read, this should work.

Could someone please take a second and tell me where my error is?

Many thanks!

Swerve1000

---

### Post by scourge on 2009-01-18
> **Swerve1000 said:**
> I'm trying to use g++
Actually, you're not. Try using the g++ command instead of gcc.

> 
It also gives:
```
bash: ./myhello: No such file or directory
```


That's because the compilation failed miserably. Can't have an executable if the compiler doesn't like your code.

---

### Post by Swerve1000 on 2009-01-18
Yey, I've figured it out.

There was nothing wrong with the code, it was because I was compiling using 'gcc' instead of 'g++'.

Worked first time. :)

---

### Post by stderr on 2009-01-18
> **Swerve1000 said:**
> t was because I was compiling using 'gcc' instead of 'g++'.

The number of times I've done that...

Another oldie but goodie:

```
g++ -o srcfile1.cpp srcfile2.cpp srcfile3.cpp ....
```

(-o to specify output filename, but forgetting to put the filename afterwards)

So it initially removes the existing srcfile1.cpp in preparation for writing the executable, then tries to compile but finds it's missing source code (srcfile1.cpp) and fails.

The result: you've deleted the first source file in the compilation list ;)

It's normally a good idea to write a little compilation script so that you don't make random mistakes like that (and the gcc/g++ one):

```
#!/bin/bash
g++ -o myfile srcfile1.cpp ....etc
```

You can save it as, say, 'compile' and make it executable with

chmod +x compile

---

