---
title: "gcc / g++ question"
date: 2005-10-26
forum: Programming Talk
---

### Post by oldmanstan on 2005-10-26
I just started working through a c++ book and when I went to compile the quintessential "hello world" program I get crazy errors from gcc but it works fine when I run it directly through g++, is my gcc not configured correctly?

here is my code...```
#include <iostream>

int main()
{
std::cout << "Hello world!\n";
}
```

and here is the error messages from gcc...```
/tmp/ccFXEdrI.o: In function `main':
helloworld1.cpp:(.text+0x25): undefined reference to `std::cout'
helloworld1.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccFXEdrI.o: In function `__tcf_0':
helloworld1.cpp:(.text+0x47): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccFXEdrI.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld1.cpp:(.text+0x74): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccFXEdrI.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'collect2: ld returned 1 exit status
```

I tried running it with sudo too, same thing.  I understand gcc is a kind of wrapper for various compilers and whatnot but I always thought it basically passed the job off to g++ anyway... in any event, I got it to work using just g++ but I'd still like to know why it doesn't work the other way...

---

### Post by LordHunter317 on 2005-10-26
When you invoke "gcc" to have it compile and link a program, like you have, it doesn't pass the standard C++ libraries to the linker.  Meaning it doesn't try to include all the system code you need to run a C++ program.

Running "gcc" as "g++" causes it to include all the standard C++ libraries, rectifying this.  There are a few other minor differences between the two invocations, but that's by far the most important one.

---

### Post by Ride Jib on 2005-10-26
one of your errors is probably that you are not returning anything on a return type int.

---

### Post by LordHunter317 on 2005-10-26
[QUOTE=Ride Jib]one of your errors is probably that you are not returning anything on a return type int.[/QUOTE]In C++, if you don't return a value from main, it defaults to EXIT_SUCCESS.  It's not an error, just a language quirk.

---

### Post by Kyral on 2005-10-26
It would work if you made it void main()

I think

---

### Post by RastaMahata on 2005-10-26
```
#include <iostream>

int main()
{
std::cout<<"Hello world!"<<endl;
return 1;
}
```
Compilation:```
g++ FILE.gcc -o PROGRAMNAME
```

---

### Post by remin8 on 2005-10-26
I would just install Build-essiential & Anjuta and all its recomended bits. Using an IDE will save you time in the long run, I think. Also, you don't need std. Just use namespace std after your includes.

---

### Post by LordHunter317 on 2005-10-26
[QUOTE=Kyral]It would work if you made it void main()

I think[/QUOTE]Nope, this is illegal in C++.  Even if the code complies, the behavior is technically undefined.

RastaMahata,
Why are you returning an error state when there is no error?

---

### Post by darth_vector on 2005-10-26
[QUOTE=RastaMahata]```
#include <iostream>

int main()
{
std::cout<<"Hello world!"<<endl;
return 1;
}
```
Compilation:```
g++ FILE.gcc -o PROGRAMNAME
```[/QUOTE]

depending on how pedantic your compiler is this wont compile since endl is defined in the std namespace. you need:

std::cout<<"Hello world"<<std::endl;

its much easier to just put

using namespace std;

at the very top of your program, then you dont have to worry about namespaces.

---

### Post by oldmanstan on 2005-10-26
Thanks for the help all, I think it's funny that there are so many different thoughts on how to code / compile such a simple program... very interesting.

p.s. I had anjuta installed already so I sat down and gave that a look-see, now using it.

---

### Post by kudu on 2005-10-26
[QUOTE=oldmanstan]Thanks for the help all, I think it's funny that there are so many different thoughts on how to code / compile such a simple program... very interesting.

p.s. I had anjuta installed already so I sat down and gave that a look-see, now using it.[/QUOTE]

You were trying to use the C compiler (gcc) to compile C++ code (g++), that's all.

And it ain't a bad idea to get familiar with compiling/linking with the terminal rather than an IDE simply as an educational exercise. It's nice to know what's actually taking place under the hood. Good luck!

kudu

---

### Post by LordHunter317 on 2005-10-27
[QUOTE=darth_vector]its much easier to just put

using namespace std;[/quote]THis is terribly bad form, unless your program is very trivial, **especially** when you're declaring functions of the same name as the ones in std (common when writing algorithim template specializations) 

That being said, for a program this trivial, it's ok.    But it's better form to never have using at anything higher than function scope.

---

### Post by My8os on 2005-10-27
Another way is:
```

using std::cout;

```

---

### Post by RastaMahata on 2005-10-27
[QUOTE=darth_vector]depending on how pedantic your compiler is this wont compile since endl is defined in the std namespace. you need:

std::cout<<"Hello world"<<std::endl;

its much easier to just put

using namespace std;

at the very top of your program, then you dont have to worry about namespaces.[/QUOTE]
](*,) ](*,) My bad, forgot to write using namespace std :(

And yeah, I wrote return 1 just for the heck of it.

---

### Post by cyberkoa on 2005-10-28
I face the similar problem that a simpile C /C++ program won't compile.

My problem should be the one mentioned by LordHunter317

[QUOTE=LordHunter317]When you invoke "gcc" to have it compile and link a program, like you have, it doesn't pass the standard C++ libraries to the linker.  Meaning it doesn't try to include all the system code you need to run a C++ program.

Running "gcc" as "g++" causes it to include all the standard C++ libraries, rectifying this.  There are a few other minor differences between the two invocations, but that's by far the most important one.[/QUOTE]

Until now I still cannot set up an development environment for C++
The error list is too long , I extract the first few lines for reference, any help is welcomed.  Thanks.

```

super@ubuntu:~/testprog$ g++-4.0 test.cpp
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:35,                 from /usr/include/c++/4.0.2/iostream:43,
                 from test.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:41,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from test.cpp:1:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:42,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from test.cpp:1:
/usr/include/c++/4.0.2/cstdio:52:19: error: stdio.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:43

```

---

### Post by toojays on 2005-10-28
Did you install the build-essential package?

---

### Post by LordHunter317 on 2005-10-28
Yeah, it looks like you somehow have the standard C++ headers installed, but not the C ones.  I'm not exactly sure how that's possible (libc6-dev must be installed for libstdc++6-dev to function, and if that's not a dep, it's a bug) but try installing build-essential.

---

### Post by cyberkoa on 2005-10-29
[QUOTE=toojays]Did you install the build-essential package?[/QUOTE]

thx, I think this the reason. 

I have installed and tested ,it works ! :)

Thanks to Lordhunter also :)

Another question , I would like to install the gtk2 development environment, which package should I install ? 

I have searched the package list , could not find something like gtk2-dev

---

### Post by toojays on 2005-10-29
Look for libgtk-2.0-dev.

---

