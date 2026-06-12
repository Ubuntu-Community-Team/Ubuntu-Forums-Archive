---
title: "compiling a program written in c++ using g++"
date: 2011-03-22
forum: Packaging and Compiling Programs
---

### Post by btf18 on 2011-03-22
Hey,

Im doing a programming tutorial and i have written my first program but it wont compile using g++. The tutorial told me to get and use borland compiler but i couldnt get that going, so i got g++

Heres my command and the shells reply:```

```ben@ubuntu:~$ g++ demo2.cpp -o demo2.cpp
demo2.cpp:1: error: expected constructor, destructor, or type conversion before ‘<’ token
```

```

Is the command right? Any ideas why it wont compile? i copied and pasted the written program from this tutorial [http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1](http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1)

Thanks heaps

---

### Post by ChipOManiac on 2011-03-22
> **btf18 said:**
> 
Heres my command and the shells reply:ben@ubuntu:~$ g++ demo2.cpp -o demo2.**cpp**
s

You're trying to compile to a *.cpp. I think this is the problem...
it should be:

> g++ demo2.cpp -o demo2.o

or just skip the -o part and g++ will compile the program to "a.out" in the current directory....

---

### Post by btf18 on 2011-03-22
hey, thanks, but if i just type g++ and the filename it just prints the same error message :-/

And its not the code because i just did another tutorial this time on how to compile and copied and pasted more code and saved and it did the same thing: ben@ubuntu:~$ g++ temp.cpp
temp.cpp:1: error: expected constructor, destructor, or type conversion before &#8216;<&#8217; token
temp.cpp: In function &#8216;int main()&#8217;:
temp.cpp:7: error: &#8216;cout&#8217; was not declared in this scope
temp.cpp:7: error: &#8216;endl&#8217; was not declared in this scope


Thanks

---

### Post by ChipOManiac on 2011-03-22
> **btf18 said:**
> 
And its not the code because i just did another tutorial this time on how to compile and copied and pasted more code and saved and it did the same thing: ben@ubuntu:~$ g++ temp.cpp
temp.cpp:1: error: expected constructor, destructor, or type conversion before ‘<’ token
temp.cpp: In function ‘int main()’:
temp.cpp:7: error: ‘cout’ was not declared in this scope
temp.cpp:7: error: ‘endl’ was not declared in this scope
Thanks

Have you installed the development packages for C++ those 'cout' things seem to be with not being able to reference.

---

### Post by btf18 on 2011-03-22
O I have to download the c++ language dont i? i have not at all done this xP Do you know how? Im using ubuntu

---

### Post by MadCow108 on 2011-03-23
> **btf18 said:**
> hey, thanks, but if i just type g++ and the filename it just prints the same error message :-/

And its not the code because i just did another tutorial this time on how to compile and copied and pasted more code and saved and it did the same thing: ben@ubuntu:~$ g++ temp.cpp
temp.cpp:1: error: expected constructor, destructor, or type conversion before ‘<’ token
temp.cpp: In function ‘int main()’:
temp.cpp:7: error: ‘cout’ was not declared in this scope
temp.cpp:7: error: ‘endl’ was not declared in this scope


Thanks

just because you pasted some code from the internet does not mean it is correct.
please post the code.

---

### Post by SevenMachines on 2011-03-23
Install the 'build-essential' package, you might want to post the code you're trying to build too, its much much more likely to be where the problem is.

---

### Post by ChipOManiac on 2011-03-25
> **SevenMachines said:**
> Install the 'build-essential' package

Yes that should do the trick it it's the libraries... I'd add libstdc++ as well to be sure...

> **SevenMachines said:**
> , you might want to post the code you're trying to build too, its much much more likely to be where the problem is.

I say the same, seeing the code will help.

---

### Post by JupiterV2 on 2011-03-25
1. The .o extension is for compiled objects.

2. The -o <name> switch tells g++ that you want its output to be <name>.
```
g++ file.cpp -o myprog
```
...would compile a program named myprog.

3. g++ should automatically link stdc++ into your program. You may have forgotten to declare the namespace with 'using namespace std;' or prefixing each cout/endl with std:: (the prefered method).

4. You should, at a minimum, enable basic warnings with -Wall:

```
g++ -Wall myfile.cpp -o myprog
```

5. Definitely make sure build-essential is installed.

---

### Post by btf18 on 2011-03-29
Thanks guys. I seem to have got it working. I assume i made some noob mistake like copying and pasting wrong xP The program only said this is some text. it was pretty anti-climactic. How does one create a program that will print something in a window that is not the shell? atleast that would be slightly more impressive

Thanks

---

### Post by btf18 on 2011-03-29
however that was the only program that would compile. This one wont, sorry i cant use a code box as i cant find the # button:

#include <stdio.h>
#include <iostream.h>

int main()
{

  float num1;
  float num2;
  int num3;
  float num4;

  cout << "Enter a number: " << endl;
  cin >> num1;

  cout << "Enter a second number: " << endl;
  cin >> num2;

  cout << "Choose an operation." << endl;
  cout << "Enter 1 to add, 2 to subtract, 3 to multiply, 4 to divide: " << endl;
  cin >> num3;


  if (num3 >4 || num3 <1)
  {
    cout << "Your operation choice isn't valid!  Please run the program again." << endl;
    cout << "Press Enter to end program." << endl;
    getchar();
    return 0;
  }
  else
  {
        if (num3 == 1)
        {
            num4 = num1 + num2;
            cout << "Result is: "<<  num4 << endl;
        }
        else if (num3 == 2)
        {
            num4 = num1 - num2;
            cout << "Result is: "<<  num4 << endl;
        }
        else if (num3 == 3)
        {
            num4 = num1 * num2;
            cout << "Result is: "<<  num4 << endl;
        }
        else if (num3 == 4)
        {
            num4 = num1 / num2;
            cout << "Result is: " <<  num4 << endl;
        }

  }

  cout << "Press Enter to end program." << endl;
  getchar();

  return 0;
}

---

### Post by MadCow108 on 2011-03-29
replace the first to lines with:
```
#include <cstdio>
#include <iostream>
using namespace std;

```
this includes the correct headers (c++ standard headers do not have an extension and C standard headers have a c in front) and sets the namespace for the file.

and change tutorial, yours is obviously seriously outdated.

---

### Post by btf18 on 2011-03-29
Thanks. That made it work. I have changed tutorial. Was the code i posted old? Namely the headers.

---

### Post by MadCow108 on 2011-03-29
yes very old, these headers where deprecated in the 2003 revision of the 1998 c++ standard

---

### Post by btf18 on 2011-03-29
> **JupiterV2 said:**
> 1. The .o extension is for compiled objects.
 
2. The -o <name> switch tells g++ that you want its output to be <name>.
```
g++ file.cpp -o myprog
```
...would compile a program named myprog.
 
3. g++ should automatically link stdc++ into your program. You may have forgotten to declare the namespace with 'using namespace std;' or prefixing each cout/endl with std:: (the prefered method).
 
4. You should, at a minimum, enable basic warnings with -Wall:
 
```
g++ -Wall myfile.cpp -o myprog
```
 
5. Definitely make sure build-essential is installed.
 
 
 
 
Thanks, about that -wall command, is that sort of a debugger or something telling me my mistakes kinda thing? Because i definitely need that, and i havent found out how to utilise vims debugger

---

### Post by MadCow108 on 2011-03-29
its no debugger (see gdb for that) but it will detect possible errors and problems during compilation.
Wall does, unlike its name, suggests not activate all warnings but only the most important ones.
for more warning flags consult the manual of gcc

You should always compile with at least -Wall and fix the warnings the compiler emits.

---

