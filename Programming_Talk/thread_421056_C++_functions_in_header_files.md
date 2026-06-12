---
title: "C++ functions in header files"
date: 2007-04-24
forum: Programming Talk
---

### Post by ironfistchamp on 2007-04-24
Hey all,


I am trying to teach myself C++ (yet again) and I am having problems with calling functions inside of my own headers. Basically if I create header X with a function defined in it I can call it successfully from the main program. However, if I create header Y, include header X and try to use the function from X it does not work. 

Example

miscfunc.h

```

#ifndef _MISCFUNC_H // if not defined
#define _MISCFUNC_H // define MyHeader


#include <stdio.h>
#include <termios.h>
#include <unistd.h>

using namespace std;

int mygetch( ) {
  struct termios oldt,
                 newt;
  int            ch;
  tcgetattr( STDIN_FILENO, &oldt );
  newt = oldt;
  newt.c_lflag &= ~( ICANON | ECHO );
  tcsetattr( STDIN_FILENO, TCSANOW, &newt );
  ch = getchar();
  tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
  return ch;
};

#endif

```

testhead.h

```

#ifndef _TESTHEAD_H
#define _TESTHEAD_H

#include <iostream>
#include <cstdlib>
#include <string>
#include "miscfunc.h"


using namespace std;

void testFunc();


void testFunc(){
        string x;
        x = mygetch();
        cout << "\n\n\n\n" << x;
        cin.get();
};

#endif

```

myapp.cpp

```

#include <iostream>
#include <string>
#include "testhead.h"

using namespace std;

int main()      {
                testFunc();
};

```

This is a pretty bad example but I am doing this in a lesson and need to be quick. Don't really want to get caught on a forum :) 

Anyway, if anyone could show me where I am going wrong that would be excellent.

Thanks

Ironfistchamp

---

### Post by aquavitae on 2007-04-24
I can't see the problem, could you post your compiler errors?  I assume it fails during compilation? Something that might help though - its generally a good idea not to put initialisations in headers, only declarations, so try moving the functions to cpp files, and just put the daclaration in the header.  I can't see how this would make much difference but you never know!

---

### Post by ironfistchamp on 2007-04-24
Thanks for the reply. The main cpp file compiles fine. 

You said about putting them in source code files. How would I actually use those functions though? Is there something I have to do to link them. If maybe you could show me using my example.

Thanks

Ironfistchamp

---

### Post by harun on 2007-04-24
In your header files you want to have function definitions but do not do the implementation (code statements) there unless it is very short (i.e. { return l_SomeMemberVar }. Do those in your main program file or seperate .cpp files.

---

### Post by ironfistchamp on 2007-04-24
Thank you for the reply but how do I include those separate source files?

Thanks

Ironfistchamp

---

### Post by harun on 2007-04-24
myapp.cpp
```

#include <iostream>
#include <string>
#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <cstdlib>
#include "testhead.h"

using namespace std;

int main()      {
                testFunc();
};

void testFunc(){
        string x;
        x = mygetch();
        cout << "\n\n\n\n" << x;
        cin.get();
};

int mygetch( ) {
  struct termios oldt,
                 newt;
  int            ch;
  tcgetattr( STDIN_FILENO, &oldt );
  newt = oldt;
  newt.c_lflag &= ~( ICANON | ECHO );
  tcsetattr( STDIN_FILENO, TCSANOW, &newt );
  ch = getchar();
  tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
  return ch;
};

```
testhead.h
```

#ifndef _TESTHEAD_H
#define _TESTHEAD_H

void testFunc();
int mygetch();

#endif

```

Not an optimal solution but as good as I can do while not on my Ubuntu box :-).

---

### Post by ironfistchamp on 2007-04-24
Ah that is starting to make sense. Would it not just be as simple to not use the header file at all?

I am a bit of a Python programmer and am used to just being able to put a lot of related functions in one module and other related ones in another then just pulling it all together. 

I think this is going to take me some time to understand how and why it is different :p

Thanks

Ironfistchamp

---

### Post by harun on 2007-04-24
> **ironfistchamp said:**
> Ah that is starting to make sense. Would it not just be as simple to not use the header file at all?

For this example definately, no need to even have a header file. Just wanted to show you the example so you can see in the future if you were to start adding more functions how they could be defined in the header file.

---

### Post by WW on 2007-04-24
It looks like the function mygetch() is something you might want to use in more than one program, so it is natural to put that function in a separate file.  Here is another way to organize your code:

**mygetch.cpp**
```

//
// mygetch.cpp
//

#include <cstdio>
#include <termios.h>
#include <unistd.h>

int mygetch( )
{
    struct termios oldt,
                   newt;
    int ch;
    tcgetattr( STDIN_FILENO, &oldt );
    newt = oldt;
    newt.c_lflag &= ~( ICANON | ECHO );
    tcsetattr( STDIN_FILENO, TCSANOW, &newt );
    ch = getchar();
    tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
    return ch;
}

```
**mygetch.h**
```

//
// mygetch.h
//

#ifndef MYGETCH_H
#define MYGETCH_H

int mygetch();

#endif

```
**myapp.cpp**
```

//
// myapp.cpp
//

#include <iostream>
#include <string>
#include "mygetch.h"

using namespace std;

void testFunc()
{
    string x;
    x = mygetch();
    cout << "\n\n\n\n" << x;
    cin.get();
}

int main()
{
    testFunc();
}

```
Here is a sequence of command to compile and run the code:
```

$ ls
myapp.cpp  mygetch.cpp  mygetch.h
$ g++ -c mygetch.cpp     # Compile mygetch.cpp into mygetch.o
$ ls
myapp.cpp  mygetch.cpp  mygetch.h  mygetch.o
$ g++ -c myapp.cpp       # Compile myapp.cpp into myapp.o
$ ls
myapp.cpp  myapp.o  mygetch.cpp  mygetch.h  mygetch.o
$ g++ myapp.o mygetch.o -o myapp   # Link myapp.o and mygetch.o, create myapp 
$ ls
myapp  myapp.cpp  myapp.o  mygetch.cpp  mygetch.h  mygetch.o
$ ./myapp                # Run the program




w
$

```

---

### Post by ironfistchamp on 2007-04-24
Perfect now I get what is going on. I shall have to learn more about this .cpp to .o to executable.

Time for some googling. 

Thanks again

Ironfistchamp

---

### Post by aquavitae on 2007-05-02
If you really want the functions in a separate cpp file, use extern in the header:

mygetch.h:
*extern* int mygetch();

---

### Post by siiib on 2007-05-02
unless its a one liner you really shouldn't be putting the implementation in the header file.. just the functions signature.. or 'prototype' as it is known.. the implementation goes in a seperate .cpp file that you can link with the header.. its just a convention whose value isn't immediately obvious when you're starting out, but it makes things simpler when you have a lot of code floating around

hth

---

### Post by baltimark on 2007-05-02
I like what WW wrote earlier, but if I make a header file, I like to put all of my includes in there. 

A very simple example
**test.h**
```

#ifndef TEST_H
#define TEST_H

#include <math.h>   //the header file includes the libraries and other header files you write

double testReturn();

#endif

```

[B]
test.cpp[/B]
```

#include "test.h"  //the only include is the .cpp code's header file

double testReturn()
{
  return sin(5.);  //the sine function takes a double, returns a double.  Notice I didn't include "math.h" in here. 
}

```


**main.cpp**
```

#include <iostream>

#include "test.h"

using namespace std;

int main()
{
  cout <<"Value is: " <<  testReturn() << endl;
  exit(0);
}

```

You can compile this just using 

```

> g++ main.cpp test.cpp 

```

if you want, but WW's example makes explicit what you're trying to do.

More typically for C++, your header files will contain classes. 

**myClass.h**
```

#ifndef MYCLASS_H
#define MYCLASS_H

#include "SomeOtherClass.h"

class myClass {
private:
  void foo();
}

```

**myClass.cpp**
```

#include "myClass.h"

void myClass::foo() 
{
  //do stuff
}

```

And, in the file with  main(), you'll want to include myClass.h, obviously. This seems to be the kind of stuff that books never really break down nicely.

---

