---
title: "c++ pointers and classes"
date: 2009-12-22
forum: Programming Talk
---

### Post by CatsRninja on 2009-12-22
I`m more used to java and python, but i got to learn c++ so i could try a compile language.
I`m trying to make an apllication with a gui, using qt4,and i came up with the following problem.
This is a simplification:
I got my main that calls this class, named say Gui, and calls this during the initialization:
```

     //set pointer to this:
     void *p = this;
     this->window = new MainWindow(p);

```
Main window has the folowing init(part of it) and method:
```

MainWindow::MainWindow(void *c){
        //set controler
        this->controler = &c;
(...)
//method:
std::string MainWindow::getPreferences(std::string what){
        this->controler->getPreferences();
        return "result";
}


```
I use a void pointer because i need to include "mainwin.h" in the gui class and  if i included gui.h it would say that the include went to far.

so in short,
i have a class that passes a pointer to itself to another class(mainwindow) that is in it, that other class(mainWindow) uses that pointer to have a pointer in it pointing to the class that created it.
then it uses that pointer to call up the method.

the error i get is: 
../mainwindow.cpp|70|error: ‘void*’ is not a pointer-to-object type|

mayby im using it wrong?

Hope you undertood it, have a nice day.
CRN

---

### Post by dwhitney67 on 2009-12-22
> **CatsRninja said:**
> ...
I use a void pointer because i need to include "mainwin.h" in the gui class and  if i included gui.h it would say that the include went to far.

I do not quite understand everything you have presented, but the information provided above is a good indicator that you are cutting corners and are not doing something quite right.

> 
so in short,
i have a class that passes a pointer to itself to another class(mainwindow) that is in it, that other class(mainWindow) uses that pointer to have a pointer in it pointing to the class that created it.
then it uses that pointer to call up the method.

It seems that one object is performing a "registration" with another object.  This should be fairly trivial.  Can you show more of your code (ie. constructors or relevant accessors)?  Or just show a similar example where you have whittled the problem-space into something smaller?

> 
the error i get is: 
../mainwindow.cpp|70|error: &#8216;void*&#8217; is not a pointer-to-object type|

In plain English, this error is indicating that you cannot de-reference a void pointer to call a method.  Perhaps you should cast it to the appropriate object type first.  What's bizarre is that you should not have had to store a void* in the first place.

---

### Post by dwhitney67 on 2009-12-22
Upon further reading your OP, here's a trivial example:

Window.h:
```

#ifndef WINDOW_H
#define WINDOW_H

#include <string>

class Controller;

class Window
{
public:
   Window(Controller* c);

   std::string getPreferences(const std::string& doWeNeedThisParam);

   ...

private:
   Controller* myController;
};

#endif

```
Window.cpp:
```

#include "Window.h"
#include "Controller.h"

Window::Window(Controller* c)
   : myController(c)
{
}

std::string getPreferences(const std::string& doWeNeedThisParam)
{
   myController->getPreferences();
   return "result";
}

...

```
Controller.h:
```

#ifndef CONTROLLER_H
#define CONTROLLER_H

class Window;

class Controller
{
public:
   Controller();

   ...

private:
   Window* myWindow;
};

#endif

```
Controller.cpp:
```

#include "Controller.h"
#include "Window.h"

Controller::Controller()
{
   myWindow = new Window(this);
}

```

---

### Post by CatsRninja on 2009-12-22
The solution you presented works completly.

My problem was that i coulnd add #include "controler.h" on the window class cause it went on a wierd cicle, the controler would include the window, and the window would include the controler.

adding the class window;
and making the includes in the cpp files, solved my problem.
I called the method with success.


Thanks, i was trying to make this work for hours.
Have nice hollidays.
CRN

---

### Post by dwhitney67 on 2009-12-22
> **CatsRninja said:**
> ...

adding the class window;
...
This is known as a "forward declaration".  When you have the time, read about it so that you understand it more.

---

### Post by CatsRninja on 2009-12-22
yeah, i guess i rushed to programing.

by the way, i read about memory allocating, and i think i am messing it up.

when do i realy need to use the new to allocate memory to a class?
when i dont know how big it can get right?
(i know i have to manualy delete the allocated space when im finished with them.)

Because i cant really be sure of it, im almost using allways new, less for some classes that have const info.


...i have been told many times:"what are you using new here for? this is not java"

---

### Post by dwhitney67 on 2009-12-22
> **CatsRninja said:**
> yeah, i guess i rushed to programing.

by the way, i read about memory allocating, and i think i am messing it up.

when do i realy need to use the new to allocate memory to a class?
when i dont know how big it can get right?
(i know i have to manualy delete the allocated space when im finished with them.)

Because i cant really be sure of it, im almost using allways new, less for some classes that have const info.


...i have been told many times:"what are you using new here for? this is not java"

If you anticipate that the object's footprint will be large, then by all means allocate the object on the heap.  Some classes seem very complicated, but that does not indicate it will take up a large footprint; examine the sizes of the member data.  An easier way is to write a small app the prints out the result of calling sizeof() on the class.

Every application is different, so determining when to allocate and when to use the stack varies.

If you allocate a Window object (as I demonstrated earlier), the proper thing to do is to deallocate it when the object (Controller) is destroyed.  However IMO, if you do not, it is not a "memory leak".  A leak occurs when you allocate many objects over time, and never free any of them after their lifetimes have completed.  The Window object will last the lifetime of the application; thus when the app finishes, the OS will collect the allocated memory and dole it out to other apps.

Analogy... think of a leaky faucet.  That's something that requires your attention... fix the problem, and the leak stops.  If the faucet is working a-ok, yet only one drop of water falls out after you have finished using the faucet, I would not worry at all.

---

### Post by CptPicard on 2009-12-22
If things like headers, memory management etc are problematic, OP might want to consider checking out C. It reduces a compiled language into a fairly minimal imperative form... C++ has a lot of detail to be mastered before properly correct code can be written.

---

