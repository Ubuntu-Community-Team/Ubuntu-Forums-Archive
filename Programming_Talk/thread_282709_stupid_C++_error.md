---
title: "stupid C++ error"
date: 2006-10-23
forum: Programming Talk
---

### Post by ilias on 2006-10-23
please do not laugh,
In dapper drake i got the following program:

#include <iostream>


int main()
{
	float f;
	char str[80];
	double d;

	cout << "Enter two floating point numbers: ";
	cin >> f >> d;

	cout << "Enter a string: ";
	cin >> str;

cout << f <<" " <<d <<" "<< str;

	return 0;
}

and get the following error:
ilias@ilias-laptop:~/DEVELOPMENT/C++/1st$ gcc -o 1stprogram 1stprogram.c++
1stprogram.c++:19:2: warning: no newline at end of file
1stprogram.c++: In function ‘int main()’:
1stprogram.c++:10: error: ‘cout’ was not declared in this scope
1stprogram.c++:11: error: ‘cin’ was not declared in this scope

when I include the line:
using namespace std;
i get the following error

/tmp/cc50uNP9.o: In function `main':1stprogram.c++:(.text+0x27): undefined reference to `std::cout':1stprogram.c++:(.text+0x2c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
:1stprogram.c++:(.text+0x3a): undefined reference to `std::cin'

-----------
--------
/tmp/cc50uNP9.o: In function `__tcf_0':1stprogram.c++:(.text+0xea): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc50uNP9.o: In function `__static_initialization_and_destruction_0(int, int)':1stprogram.c++:(.text+0x113): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc50uNP9.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


heeeelp!!

---

### Post by ilias on 2006-10-23
sorry for the extra images...i just discovered the Wrap [code] function...
Anyway any help would be greatly appreciated.

---

### Post by Ben Sprinkle on 2006-10-23
```
double d;

```
Rofl.
You compile with the ` parameters and the correct gtk package?

---

### Post by duff on 2006-10-23
C++ code requires the C++ compiler g++, gcc is for C code.

---

### Post by ilias on 2006-10-23
ok now i got it....
thanks duff it's g++ and not gcc
I thought that gcc was for all supported types of code
thanks again
code test:
```
//testing tha wrap code function
 thanks for the example synectics
```

---

### Post by Ben Sprinkle on 2006-10-23
Yeah, 4.0 is the version in repo's I think. I use it all the time. :)

---

### Post by thumper on 2006-10-23
You need to use std::cin and std::cout.

---

### Post by po0f on 2006-10-23
ilias,

If you're doing C++ development, why not use std::string instead of char arrays?  Pardon me if you haven't gotten that far in your tutorial yet.

---

### Post by ilias on 2006-10-24
It was a simple code fragment taken from a C++ book, to familiarise myself with the linux c++ programming environment...
I am learning qt developemnt because i've got a complex PhotoVoltaic (PV) module-effeciency mathematic model to investigate the annual power production of several PV modules. A significant number of module parameters are provided in  a rather large database and this factors are entered to the mathematical model to make the forecast of power production...
I would like to create a simplified version of the project in
[HTML]http://www.mauisolarsoftware.com/[/HTML]
for my personal use.
For informative purposes this is the model:
[http://www.sandia.gov/pv/docs/PDF/King%20SAND.pdf](http://www.sandia.gov/pv/docs/PDF/King%20SAND.pdf)
and the database can be found here:
[HTML]http://www.sandia.gov/pv/docs/Database.htm[/HTML]
it is an exe file that can be run with wine and extracts the database in question

---

### Post by indigoshift on 2006-10-25
> **thumper said:**
> You need to use std::cin and std::cout.

Or, insert the following line somewhere between your includes and main():

```
using namespace std;
```

And use cout and cin as you're using them already.

I had the same problem a few days ago, and the helpful folks here pointed this out.  It works fine now!

---

### Post by Luiz_Gustavo on 2007-10-29
Even using "using namespace std;" and compiling with g++, cin, cerr are not recognized.
I'm using Netbeans.
Any ideas?

thanks in advance!

---

### Post by Luiz_Gustavo on 2007-10-30
Hi,

now it's ok!
I needed to include "using namespace std;", include "#include <iostream>" without ".h" and use "std::cin". Strange, but now it works.

---

