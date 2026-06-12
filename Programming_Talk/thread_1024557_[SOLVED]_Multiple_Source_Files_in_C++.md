---
title: "[SOLVED] Multiple Source Files in C++"
date: 2008-12-29
forum: Programming Talk
---

### Post by nebu on 2008-12-29
If I have multiple source files for a program in c++....

how do i use a class defined in one of the files in another??

do i have to include something in the header files??? function prototyping in the header files lets me use them in multiple source files..... how do i achieve this for classes??

---

### Post by dempl_dempl on 2008-12-29
Declaration  in MyClass.h  file  :

```


#ifndef __MY_CLASS_H__ ///Header file protection begin
#define __MY_CLASS_H__

 class MyClass
 { 
   public:
       MyClass();
       ~MyClass();  
        
       void someFunction(); //     
 };

#endif  ///Header protection end


```

In MyClass.cpp  :

```

#include "MyClass.h" //You need this :)


#include <iostream>  //I've put this here just for example
using namespace std;

MyClass::MyClass()
{
//Initialization stuff
}

void MyClass::someFunction()
{
 cout << "Hello, world" << endl;
}


MyClass::~MyClass()
{
 //Destructor stuff
}


```

---

### Post by Emill on 2008-12-29
Then you can include MyClass.h in another file and use MyClass in that file.

---

### Post by nebu on 2008-12-29
thnx.... that solved it

---

