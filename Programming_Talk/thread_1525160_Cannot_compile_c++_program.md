---
title: "Cannot compile c++ program"
date: 2010-07-06
forum: Programming Talk
---

### Post by Ekant on 2010-07-06
I  am trying to compile the C++ using Kdevelop4 but can't do. The code is :-
#include<iostream>
*#include<conio*>---_Shows error here_

void main()
{
int a, *ptr1, **ptr2;
clrscr();
ptr1=&a;
ptr2=&ptr1;
cout << "The address of a : "<< ptr1 << "\n";
cout << "The address of ptr1: "<< ptr2 ;
cout << "\n\n";
cout << "After incrementing the address values:\n\n";
ptr1+=2;
cout<<"The address of a : " << ptr1 << "\n";
ptr2+=2;
cout << "The address of ptr1 : " << ptr2 << "\n";
}
help!!

---

### Post by unknownPoster on 2010-07-06
you don't need to include conio. That's typically used for MS-DOS, if you're on Linux you probably won't need it.

[http://en.wikipedia.org/wiki/Conio.h](http://en.wikipedia.org/wiki/Conio.h)

---

### Post by Ekant on 2010-07-06
thanks for replying.
your advice was good. But u didn't tell as to how to compile the above program.
Thanks in advance.

---

### Post by jrothwell97 on 2010-07-06
> **Ekant said:**
> thanks for replying.
your advice was good. But u didn't tell as to how to compile the above program.
Thanks in advance.
They did, s/he said you don't need to include conio.

So, remove #include <conio> and try again.

---

### Post by Ekant on 2010-07-06
I did that to before you told me.
It's showing error statements containing [U][I]cout.
[/I][/U][I]_can u please guide me how to compile the program._
i have saved file in documents folder with .cpp extension.
errors:
include path resolver: make file is missing.
could not find clrscr, cout.
[/I]

---

### Post by Simian Man on 2010-07-06
You have two problems.  First the easy one: replace "cout" with "std::cout".  cout is in the standard namespace now so you must tell the compiler so.

For the hard one, you will either need to delete "clrscr" or find a version of conio.h for Linux.  I'd recommend deleting clrscr.

---

### Post by slooksterpsv on 2010-07-06
Until you have a line containing:
using namespace std;
cout will be unrecognized, it would be std::cout instead of cout.

Once you type using namespace std; the cout errors will go away.

To compile, in a terminal go to where the file is located via cd then type in g++ -o outputname filename.cpp
E.g.
[php]
cd Developer/C++/MyProgram
g++ -o testapp main.cpp
./test.app
[/php]

---

### Post by gsocker on 2010-07-06
Three problems:
1. void main is not legal C++ according to the standard. Change to int main, as g++ v3 and up will complain that main must return int. 
2. conio is a DOS/Windows platform specific include. It does not exist in Linux.
3. cout is in namespace std.   Use std::cout.

If whatever book/website you are using uses void main, cout without the namespace part, and conio, I suggest you find something else, as it obviously does not teach standard C++.

---

### Post by Ekant on 2010-07-06
Thanks to you all.
the _cout _error does not exist any more. thanks for that.
But still i am having: 
**Include path resolver: Make file is missing in "/home/user_name/documents" Preprocessor ./pointer.cpp**

---

### Post by RiceMonster on 2010-07-06
> **Simian Man said:**
> You have two problems.  First the easy one: replace "cout" with "std::cout".  cout is in the standard namespace now so you must tell the compiler so.

Or more simply, you can put this above main:
```
using namespace std;
```

main should also be written as "int main (void)" and you should include "return 0" at the end of the main function. Please use << endl; instead of << "\n"; to create a new line as well.

---

### Post by Ekant on 2010-07-07
shows error:
**Include path resolver:** *make file is missing in folder /home/user/documents ./pointer*.cpp

---

### Post by Ekant on 2010-07-07
using namespace std;
#include<iostream>

int main(void)
{
int a, *ptr1, **ptr2;
ptr1=&a;
ptr2=&ptr1;
cout << "The address of a : "<< ptr1 << endl;
cout << "The address of ptr1: "<< ptr2 ;
cout << endl;
cout << "After incrementing the address values:";
ptr1+=2;
cout<<"The address of a : " << ptr1 << endl ;
ptr2+=2;
cout << "The address of ptr1 : " << ptr2 << endl ;
return 0;
}
the above code shows error:
**Include path resolver:** *make file is missing in folder /home/user/documents ./pointer*.cpp
Now what can be the problem!

---

### Post by lisati on 2010-07-07
Moved to "Programming talk"

Suggestion: if it's a relatively small file, use the "g++" command instead of the "make" command to compile it. Also check that build-essential is installed.

Edit:
For future reference, if you wrap your code with [noparse]"```
" and "
```" tags to help preserve the formatting.

---

### Post by Ekant on 2010-07-07
using namespace std;
#include<iostream>

int main(void)
{
int a, *ptr1, **ptr2;
ptr1=&a;
ptr2=&ptr1;
cout << "The address of a : "<< ptr1 << endl;
cout << "The address of ptr1: "<< ptr2 ;
cout << endl;
cout << "After incrementing the address values:";
ptr1+=2;
cout<<"The address of a : " << ptr1 << endl ;
ptr2+=2;
cout << "The address of ptr1 : " << ptr2 << endl ;
return 0;
}
shows me make file error:
**include path resolver: make file error in folder**.
also the solution requires to work on the command line, i have no experience of working on it .
i need serious help!

---

### Post by Tony Flury on 2010-07-07
What command are you typing at the terminal to try to build this ?

---

### Post by ashokiiit on 2010-07-07
I didnt get any error when i tried the code u posted. Please check whether all the files included or not.....

---

### Post by Ekant on 2010-07-07
well actually i am not trying to compile it at command line.
i am using Kdevelop4 IDE to work it out and it shows me error.

---

### Post by Ekant on 2010-07-07
nice to hear that.
can n you tell me how did you compile it.  i tried to **launch** it from **run** tab.
your advice is deeply required as i am new to ubuntu and trying hard to compile it.
thanks in advance

---

### Post by dwhitney67 on 2010-07-07
IMO, before you start depending on an IDE to do the compiling for you, you should learn to do it yourself.  Countless beginners make the same 'mistake' as you; it's quite apparent from the weekly postings on this forum.

Follow these commands, by using a terminal/console/gnome-terminal:
```

cd /home/user/documents       # I got this from your other thread

g++ -Wall -c pointer.cpp      # This compiles the source code

g++ pointer.o -o pointer      # This links the object file to form an executable

```

Alternatively:
```

cd /home/user/documents

g++ -Wall pointer.cpp -o pointer    # Recommended when you only have one source file.

```

Another alternative:
```

cd /home/user/documents

make CXXFLAGS=-Wall pointer

```

---

### Post by lisati on 2010-07-07
Threads merged

---

### Post by Ekant on 2010-07-07
> **dwhitney67 said:**
> IMO, before you start depending on an IDE to do the compiling for you, you should learn to do it yourself.  Countless beginners make the same 'mistake' as you; it's quite apparent from the weekly postings on this forum.

Follow these commands, by using a terminal/console/gnome-terminal:
```

cd /home/user/documents       # I got this from your other thread

g++ -Wall -c pointer.cpp      # This compiles the source code

g++ pointer.o -o pointer      # This links the object file to form an executable

```Alternatively:
```

cd /home/user/documents

g++ -Wall pointer.cpp -o pointer    # Recommended when you only have one source file.

```Another alternative:
```

cd /home/user/documents

make CXXFLAGS=-Wall pointer

```


thank you. 
but i have tried it.
it surely works but all i want to do is to work on kdevelop4 IDE as its seems to be more user-friendly.

---

### Post by dwhitney67 on 2010-07-07
> **Ekant said:**
> thank you. 
but i have tried it.
it surely works but all i want to do is to work on kdevelop4 IDE as its seems to be more user-friendly.

Does it rub your hand as you are writing code?

Look at the project settings; surely a user-friendly app will clearly indicate which options are for compiling the source code, and which are necessary for linking the project to form the executable.

Another alternative is to click on the "Help" pull-down menu so you can peruse the documentation; perhaps there's a section on "How to get started".

---

### Post by Ekant on 2010-07-07
actually i am scratching my head for a few days now as ubuntu is entirely new experience to me and most of all people in ubuntu forums are awesome!!
they help you a lot.
well i get your point. i have searched through many forums before posting my question here. I have had a pretty good experience working on programs/applications under windows os but with kde in ubuntu my head is rolling.
thanks for your advice. i see what can i do..:)

---

