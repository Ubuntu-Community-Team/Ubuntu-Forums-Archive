---
title: "Ubuntu 11: can't compile basic C++ program (iostream.h)"
date: 2011-05-03
forum: Programming Talk
---

### Post by heysimo on 2011-05-03
hello guys.
today I installed Ubuntu 11.04 (was used to 9.10) and I'm trying to compile my very first C++ program (never did this before, I'm a C programmer).
I'm trying to compile with the line

cc helloworld.cc   (how could it be simpler than this?)

and I got the error the compiler can't find the library iostream.h (if I put #include <iostream.h> in the header)
and doesn't give error on the library but does give it on the function cout if I put #include <iostream> in the header.

now, the iostream library is present in the folder usr/include/c++

what's wrong?

btw, the code I'm trying to compile is a *.cc file containing:

#include <iostream>

int main( void )
{
    cout << "welcome to C++\n";

   return 0;
}

thanks!

---

### Post by Zugzwang on 2011-05-03
> **heysimo said:**
> 
#include <iostream>

int main( void )
{
    cout << "welcome to C++\n";

   return 0;
}

thanks!

I don't know where you have your code from, but it is very outdated: You are using the "cout" object without referring to its namespace. Fix this by writing "std::cout" instead of "cout" *or* by adding the "using namespace std;" directive after the #include line. As at some point you will want to access stuff from the namespace "std" in your header files, and it is *very* bad style to add "using namespace std;" in header files, you might want to get used to the former style.

Also, you should always link C++ code with "g++". Since you were using the compile-and-link-in-one-go function of the GCC in your example command, you should replace "cc" by "g++" when making the executable out of your code.

---

### Post by krishnandu.sarkar on 2011-05-03
#include<iostream>
int main()
{
std::cout<<"Hello World"<<std::endl;
return 0;
}

OR

#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World"<<endl;
return 0;
}


Now save the file say with helloworld.cpp

Compile with:
g++ -o helloworld helloworld.cpp

Run with:
./helloworld

Compiling with cc will also work.

Happy Coding :D

---

### Post by heysimo on 2011-05-03
hello mates!
thank you soso much for your fast and kind replies, Ima try this straight away!

a lil OT considering what you noted on my code:
I'm studying C++ on the book "programming in C++" by Deitel & Deitel...
I got the 2001 edition from a friend.
do you think it's too old? will I soon encounter difficulties like this?
ty!

S

---

### Post by krishnandu.sarkar on 2011-05-03
Yup, see many things has been changed, and the things you are learning are outdated.

So why learn something which is outdated and present and future versions of compilers will throw error??

---

### Post by cgroza on 2011-05-03
> **krishnandu.sarkar said:**
> Yup, see many things has been changed, and the things you are learning are outdated.

So why learn something which is outdated and present and future versions of compilers will throw error??

I learned C++ from a 1997 book and never had a compiler error because the standard's have changed.

---

### Post by ve4cib on 2011-05-03
A 2001 book on C++ will work.  It may not have all the latest-and-greatest bleeding edge stuff, but if you're starting out and need to understand the basics it'll do just fine.

---

### Post by stchman on 2011-05-05
You are missing the namespace std line.  Also use .cpp as your C++ file extension.

[PHP]
#include <iostream>
using namespace std;

int main( void )
{
         cout << "welcome to C++\n";

         return 0;
}

[/PHP]Do you have the build-essential package installed?  This is needed to compile C/C++ programs.  To install, do the following:

```

sudo apt-get install build-essential

```After that use the g++ command to compile the program.

```

g++ -o hello hello.cpp

```

---

### Post by axi.torvalds on 2011-05-05
> **heysimo said:**
> hello mates!
thank you soso much for your fast and kind replies, Ima try this straight away!

a lil OT considering what you noted on my code:
I'm studying C++ on the book "programming in C++" by Deitel & Deitel...
I got the 2001 edition from a friend.
do you think it's too old? will I soon encounter difficulties like this?
ty!

S

Yes probably the book uses the old compiler!

---

