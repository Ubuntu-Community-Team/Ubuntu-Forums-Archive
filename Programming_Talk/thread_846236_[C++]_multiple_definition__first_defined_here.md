---
title: "[C++] multiple definition / first defined here"
date: 2008-07-01
forum: Programming Talk
---

### Post by A_B on 2008-07-01
Hi

I wrote a program in C++ made up of different source files, when I try to compile it, I get the following error many times:

I:\DOCUME~1\Alex\LOCALS~1\Temp/ccN9dCYr.o:globals.cpp:(.bss+0x4b8): multiple def
inition of `loadbtn'
I:\DOCUME~1\Alex\LOCALS~1\Temp/cc1HRoFk.o:main.cpp:(.bss+0x4b8): first defined here

where "loadbtn is (or should be) an instance of a "Button" class

The structure of the files is like this:

```

[main.cpp]
#include "constants.h"
#include "globals.h"
#include "functions.h"
#include "classes.h"


[constants.h]


[globals.h]
#include "classes.h"


[globals.cpp]
#include "globals.h"
#include "classes.h"


[classes.h]


[button.cpp]
#include "classes.h"
#include "functions.h"
#include "globals.h"


[stringinput.cpp]
#include "classes.h"
#include "functions.h"
#include "globals.h"


[functions.h]


[functions.cpp]
#include "functions.h"
#include "globals.h"
#include "classes.h"
#include "constants.h"


[clipterraintiles.cpp]
#include "globals.h"

```

now, when i try to compile the code, I get the error for every instance of the Button class. Then instances are intialized in [globals.h] and then declared in [globals.cpp]. Although there is no difference between the initialization of the instance and it's declaration. for example:

in [globals.h]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers

in [globals.cpp]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers


So, when I try to compile, the compiler sees multiple declarations, 1 time for every .cpp where [globals.h] was included.
The error displays "first defined here" only for the last .cpp ,where [globals.h] was included, in the list of .cpp's in my compile command.

so a different arrangement of compile command might as well give this error:

I:\DOCUME~1\Alex\LOCALS~1\Temp/ccN9dCYr.o:CLIPTERRAINTILES.cpp:
(.bss+0x4b8): multiple definition of `loadbtn'
I:\DOCUME~1\Alex\LOCALS~1\Temp/cc1HRoFk.o:main.cpp:(.bss+0x4b8): first defined here

(can anyone also tell me how to turn of the smilies here :p)



I hope you have a good idea of what the problem is by now, any help would be very appreciated.

Thanks
Alex

(You may have noticed by the error messages that I am in fact working on Windows now, I have checked that everything in my program is completely cross-platform, so the same thing should happen when trying to compile on a linux os. The reason I ask here is because I used ubuntu for a long time and the forums are a great place to get help, as opposed to the windows forums)

---

### Post by Tony Flury on 2008-07-01
You are including globals.h in a lot of different places, but possibly including it recursively.

you want to think about using include guards : 

```

#ifndef H_GLOBALS
#define H_GLOABLS
.......
<content of globals.h>
.......
#endif

```

Trying doing that with each different .h file - so that you don't get multiple defines. Make sure the macro you define has different names for each .h (H_FUNCTIONS, H_CLASSES, H_CONSTANTS etc).

---

### Post by Zugzwang on 2008-07-01
> **A_B said:**
> 
now, when i try to compile the code, I get the error for every instance of the Button class. Then instances are intialized in [globals.h] and then declared in [globals.cpp]. Although there is no difference between the initialization of the instance and it's declaration. for example:

in [globals.h]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers

in [globals.cpp]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers


These *are* your multiple definitions. Try replacing the definition in globals.h (header files should only contain *declarations* (exception: templates and inlined functions) with:
```

extern Button loadbtn;

```

---

### Post by A_B on 2008-07-01
@Tony Flury
my program already includes guards, they seem not to help for my problem though. I should have included that in my post.

@Zugzwang
I have included extern before every declaration in [global.h], extern does not work with instances or functions though, and the compiler gives an error when it sees the following:

extern Button loadbtn;



Thanks for the amazingly fast replies

Alex

---

### Post by Zugzwang on 2008-07-01
> **A_B said:**
> 
@Zugzwang
I have included extern before every declaration in [global.h], extern does not work with instances or functions though, and the compiler gives an error when it sees the following:

extern Button loadbtn;

I guess we are not talking about the same thing. It *does* work with instances. Example:
[PHP]
#include <iostream>

// This would be in you "globals.h"
class Testing {
private:
  int hello;
public:
  Testing(int _hello) : hello(_hello) {}
  void msg() {
    std::cout << "Testing 1-2-3\nThe magic number is: " << hello << std::endl;
  }
};

extern Testing test;

// This would be in your "globals.cpp"
Testing test(77);

int main() {
        test.msg();
        return 0;
}
[/PHP]

It does not work with functions since there is no need to specify "extern" here.

---

### Post by Tony Flury on 2008-07-01
> **A_B said:**
> Hi

in [globals.h]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers

in [globals.cpp]
Button loadbtn (x, y ,w ,h, type); //parameters are all integers


if your code in globals.cpp is really as above - then you are declaring loadbtn twice - rather than declaring once (in your header file) and then defining once (in your cpp file).

I think sometimes the error messages are misleading, be careful of the difference between declaration and defintion.

I am not sure if this is actually the problem.

---

### Post by WW on 2008-07-01
Zugzwang's suggestion in post #3 should work.
> **A_B said:**
> 
@Zugzwang
I have included extern before every declaration in [global.h], extern does not work with instances or functions though, and the compiler gives an error when it sees the following:

extern Button loadbtn;

Then you have an additional mistake somewhere in your declarations. What is the error?

---

### Post by A_B on 2008-07-01
@Zugzwang
ok, I moved all class declarations from [classes.h] to [global.h] and changed declarations and definitions of instances as shown in your post.

It works like a charm :p

Now the compiler continues to give some similar errors, this time related to a struct which should also be declared in [global.h]

struct tiles
{
     int type;
};

I guess this is the way to define a struct as opposed to only declaring it? If so, how would I declare the struct in [global.h]?


Thanks
Alex

---

### Post by dwhitney67 on 2008-07-01
You should not have to treat global.h as the kitchen sink, where you throw everything in there.

In some of the previous posts in this thread, some folks have been attempting to help with limited knowledge since you have not supplied any code for anyone to examine.

A typical header file should contain the multiple-inclusion guards, and preferably only one class or struct definition.  Here is an example of some header files, two implementation files, and the main module containing the main function.

Globals.h:    // btw, I would never recommend having globals
[PHP]#ifndef GLOBALS_H
#define GLOBALS_H

#include "Header_A.h"
#include "Header_B.h"


#ifdef MAIN
#define EXTERN           // the Main module defines objects
#else
#define EXTERN extern    // others modules see objects as externs
#endif


EXTERN Header_A headA(5);
EXTERN Header_B headB(2,3);

#endif[/PHP]
Header_A.h:
[PHP]#ifndef HEADER_A_H
#define HEADER_A_H

#include "Header_B.h"

class Header_A
{
  public:
    Header_A(int value = 0);

    int getValue() const;

    const Header_B & getHeadB() const;

  private:
    int      m_value;
    Header_B m_headB;
};

#endif[/PHP]
Header_B.h:
[PHP]#ifndef HEADER_B_H
#define HEADER_B_H

struct Header_B
{
  Header_B(unsigned int w = 0, unsigned int l = 0);

  unsigned int m_width;
  unsigned int m_length;
};

#endif[/PHP]
Header_A.cpp:
[PHP]#include "Header_A.h"


Header_A::Header_A(int value)
  : m_value(value),
    m_headB(value, value*2)
{
}

int
Header_A::getValue() const
{
  return m_value;
}

const Header_B &
Header_A::getHeadB() const
{
  return m_headB;
}[/PHP]
Header_B.cpp:
[PHP]#include "Header_B.h"

Header_B::Header_B(unsigned int w, unsigned int l)
  : m_width(w),
    m_length(l)
{
}[/PHP]
Main.cpp:
[PHP]#define MAIN
#include "Globals.h"
#include <iostream>

int main()
{
  std::cout << "headA.m_value          = " << headA.getValue()          << std::endl;
  std::cout << "headA.m_headB.m_width  = " << headA.getHeadB().m_width  << std::endl;
  std::cout << "headA.m_headB.m_length = " << headA.getHeadB().m_length << std::endl;

  std::cout << "headB.m_width          = " << headB.m_width << std::endl;
  std::cout << "headB.m_length         = " << headB.m_length << std::endl;

  return 0;
}[/PHP]

---

### Post by A_B on 2008-07-01
I finally got the program to compile, thanks to your help :p

But the program still doesn't work :( , The program uses SLD. The problem is that no surfaces are blitted on the screen, also, the program crashes when i try to click on the place where a button should be (which isn't visually there, as the button's image won't blit). I'm tracking down the errors now, as I don't think anyone event wants so see my source (it's big ,unorganized and unclear) this thread is finished to me.

Thanks for the help, I'll post my source code and program once it's finished :p

Alex

---

