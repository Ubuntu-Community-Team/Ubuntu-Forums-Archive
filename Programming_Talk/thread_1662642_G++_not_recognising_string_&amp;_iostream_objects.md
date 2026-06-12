---
title: "G++ not recognising string &amp; iostream objects"
date: 2011-01-08
forum: Programming Talk
---

### Post by TMagic*04 on 2011-01-08
Hi,

I'm going back to coding in C++ after a while on a new box, I installed g++ and multilib package, and trying to compile a simple program I keep getting errors with regard to my use of strings and objects from other libraries.

I'm trying this on ubuntu 10.10 with a 64bit machine (could this be a potential cause?)

The code is
```
#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <string.h>
#include <string>
#include <ctype.h>

void awaitUser(){

  char ch;
  char buff[3];
  int count = 3, 
  string name; 
  cout << "|| -- |ENTER 3 OR q to quit this program..." << endl;
  while(count!=-1){
    cin >> name;
    if(name == "q" || name == "3")
      exit(0);    
    }
}

int main(int argc, char *argv[]){
awaitUser();
}//end main()
```

and using this compile command:
```
g++ -o ./foo -Wall -pedantic main.cpp

```

I get the following output:
```
main.cpp: In function ‘void awaitUser()’:
main.cpp:13: error: ‘string’ was not declared in this scope
main.cpp:13: error: expected ‘;’ before ‘name’
main.cpp:14: error: ‘cout’ was not declared in this scope
main.cpp:14: error: ‘endl’ was not declared in this scope
main.cpp:19: error: ‘cin’ was not declared in this scope
main.cpp:19: error: ‘name’ was not declared in this scope
main.cpp:10: warning: unused variable ‘ch’
main.cpp:11: warning: unused variable ‘buff’
main.cpp:12: warning: unused variable ‘i’

```

Could anyone explain why string, and the iostream objects are listed as not declared and recommend a possible solution? I imagine that it's because it can't find the libraries although I may be wrong.

thanks for any help,

---

### Post by MadCow108 on 2011-01-08
you are missing the std namespace:
std::string, std::cout, std::endl, ...
or a using namespace std; in the beginning of the cpp file

[http://www.cplusplus.com/doc/tutorial/namespaces/](http://www.cplusplus.com/doc/tutorial/namespaces/)

also in c++ you prepend a c and remove the .h from **standard** c headers like string.h => cstring, stdlib.h => cstdlib, stdio.h => cstdio ...

---

### Post by TMagic*04 on 2011-01-08
Doh! I should've really seen that, seeing as I've done the same thing on countless problems before...

Thank you very much for pointing it out to me, and the information about pre-pending c to the library names, didn't know that but it's definitley useful

---

### Post by worksofcraft on 2011-01-08
> **TMagic*04 said:**
> Doh! I should've really seen that, seeing as I've done the same thing on countless problems before...

Thank you very much for pointing it out to me, and the information about pre-pending c to the library names, didn't know that but it's definitley useful

It may help if you also know that c++ header file versions are there to eliminate extensive use of macros that is in some standard c headers.

---

