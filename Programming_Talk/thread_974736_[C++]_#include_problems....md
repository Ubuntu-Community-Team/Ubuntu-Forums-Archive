---
title: "[C++] #include problems..."
date: 2008-11-07
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-11-07
I am developing an app with Gtkmm. As you know the main window is a class. Let's name it "Mainwindow.h". I have created a class of my own which will be re-used several times on runtime(through new and delete). Let's name it "my_class.h". I want to be able to call/notify the main window for some changes in my class. So I thought I'll declare a pointer to my "Mainwindow.h" in my class prototype in "my_class.h".
The resulting code is for:
Mainwindow.h
[php]#include "myclass.h"
blah blah blah[/php]
my_class.h
[php]#include "Mainwindow.h"
blah blah blah[/php]

When trying to compile the whole project the compiler says for my "my_class.h" that the pointer I have that points to main window is "not delcared" (actually it says that the type of the pointer is not declared).

Obviously this is realated to the fact that I include each header in the other header. So how do I solve it? How can I have a pointer to my parent class and compile?

Thank you in advance.

---

### Post by Delever on 2008-11-08
You can use single header where you redeclare each class
You can use abstract class as base either for main window or for your class (it would be like interface)
You can pass callback functions to a class.

---

### Post by dribeas on 2008-11-08
> **SledgeHammer_999 said:**
> So I thought I'll declare a pointer to my "Mainwindow.h" in my class prototype in "my_class.h".
The resulting code is for:
Mainwindow.h
[php]#include "myclass.h"
blah blah blah[/php]
my_class.h
[php]#include "Mainwindow.h"
blah blah blah[/php]

When trying to compile the whole project the compiler says for my "my_class.h" that the pointer I have that points to main window is "not delcared" (actually it says that the type of the pointer is not declared).

You have a cycle dependency. If myclass.h only needs MainWindow.h to declare a pointer you can remove the header inclussion from myclass.h and just forward declare the type:

```

// MainWindow.h
#include "myclass.h"
class MainWindow
{
private:
   MyClass x_; // Requires full declaration of MyClass
};

// myclass.h
class MainWindow; // Forward declaration
class MyClass
{
private:
   MainWindow* window_; // Only requires forward declaration
};

// myclass.cpp
#include "myclass.h" // in any order
#include "MainWindow.h"

// here both are fully declared and you can fully use MainWindow

```

In MainWindow.h and all other compilation units that include it, both MainWindow and MyClass are fully declared classes. In myclass.h MainWindow has only been forward declared. Any compilation unit that requires the use of MainWindow class must also include MainWindow.h (as in myclass.cpp)

See a [previous post]("http://ubuntuforums.org/showpost.php?p=6090657&postcount=17") on forward declarations. 

As @Delever pointed before consider whether this is design you want for your application. You are coupling both classes together, when you could provide an interface (pure abstract class) and decouple (changes to one of the classes, as long as the interface is not changed, will not require changes/compilation of the other class)

---

### Post by SledgeHammer_999 on 2008-11-08
Ok thank you.
I also solved it another way. I used a void pointer and didn't include "Mainwindow.h" in "my_class.h". I inlcuded it in "my_class.cpp" and just type_casted the void pointer into a MainWindow pointer :D

---

### Post by dribeas on 2008-11-08
> **SledgeHammer_999 said:**
> Ok thank you.
I also solved it another way. I used a void pointer and didn't include "Mainwindow.h" in "my_class.h". I inlcuded it in "my_class.cpp" and just type_casted the void pointer into a MainWindow pointer :D

That is dangerous. The compiler will not help you if by error in any later maintenance task you store a pointer to any other type.

---

### Post by SledgeHammer_999 on 2008-11-08
I understand what you're saying. But my void is in the constructor so it is "casted" in there and after that it "dies".(un-accesible from other member functions).

But I think I'll use the forward declaration, because in the future it will be easier for me to understand what I am doing :p (I forget quite often) hahahahha

---

