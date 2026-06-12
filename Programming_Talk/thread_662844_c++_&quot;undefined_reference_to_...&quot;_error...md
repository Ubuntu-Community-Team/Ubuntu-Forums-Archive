---
title: "c++ &quot;undefined reference to ...&quot; error..please help"
date: 2008-01-09
forum: Programming Talk
---

### Post by hereitcomes on 2008-01-09
having followed suggestions in other threads around the same problem, I'm going to have to post my own example and hope someone can help
I'm just starting to learn C++ from a Java background
I have 3 files, main.cpp, TestClass.cpp, TestClass.h

It was working until I decided to create my own method "gimme()" in the TestClass class, then I started getting the undefined reference from the call in main
Thanks for any advice
Edit: Here is the error from eclipse: 
```


**** Build of configuration Debug for project HelloManage ****

make -k all 
Building file: ../TestClass.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"TestClass.d" -MT"TestClass.d" -o"TestClass.o" "../TestClass.cpp"
Finished building: ../TestClass.cpp
 
Building target: HelloManage
Invoking: GCC C++ Linker
g++  -o"HelloManage"  ./TestClass.o ./main.o   
./main.o: In function `main':
/home/scott/workspace/HelloManage/Debug/../main.cpp:9: undefined reference to `TestClass::gimme()'
collect2: ld returned 1 exit status
make: *** [HelloManage] Error 1
make: Target `all' not remade because of errors.
Build complete for project HelloManage

```

**main.cpp**
```

#include <iostream>
#include <string>
#include "TestClass.h"
using namespace std;

int main()
{
	TestClass s;
	s.gimme();
	string yourName;

	cout << "Enter your name: ";
	cin  >> yourName;
	cout << "Hello " + yourName << endl;

	return 0;
}

```

**TestClass.h**
```

#ifndef TESTCLASS_H_
#define TESTCLASS_H_

class TestClass
{
public:
	TestClass();
	virtual ~TestClass();
	void gimme();
};

#endif /*TESTCLASS_H_*/

```



**TestClass.cpp**
```

#include "TestClass.h"
#include <iostream>

TestClass::TestClass()
{
	std::cout << "Created TestClass\n";
}

TestClass::~TestClass()
{
}

void gimme()
{
	std::cout << "Called gimme\n";
}

```

---

### Post by luisromangz on 2008-01-09
Well, as the error says, you haven't defined TestClass::gimme() but you defined it in the header file. What you defined was gimme, without naming the class it belongs.

You should declare that method this way:

void TestClass::gimme() {

...

}

---

### Post by hereitcomes on 2008-01-09
ahh I see thank you very much!
is there a reason why the .cpp file for a class needs to have the class name prefixed on all method headers? It seems a bit redundant, but that's just my java background where the convention is to have a class called TestClass.java where anything to do with the TestClass class is defined.

Thanks very much again that worked

---

### Post by [h2o] on 2008-01-09
> **hereitcomes said:**
> ahh I see thank you very much!
is there a reason why the .cpp file for a class needs to have the class name prefixed on all method headers? It seems a bit redundant, but that's just my java background where the convention is to have a class called TestClass.java where anything to do with the TestClass class is defined.

Thanks very much again that worked

Actually it is the same. If I remember correctly Java does not differ between declaration and implementation. You declare the function and implement it in the same file. And since the function is declared **inside** the class statement, there is no need prefix it with anything since there is no question to which class the function is a member. In C++ you can hace function that are not members of a class therefore you need to specify if they are members of a class or not.
You can implement the function inside the class declaration with C++ as well, but it is not the standard way (at least not for larger functions). I tend to use it for very short functions like
int get_age() { return this.age; }
Although I know I probably shouldn't ;)

---

### Post by hereitcomes on 2008-01-09
wow nice tip :) I see it all coming together slowly . .
I'm learning C++ for my uni dissertation, I just need to write a plugin for mythtv using sockets mostly, and boy is it tougher than java!
is C++ worth going heavily into?

---

