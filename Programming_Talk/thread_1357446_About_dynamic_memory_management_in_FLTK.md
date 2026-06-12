---
title: "About dynamic memory management in FLTK"
date: 2009-12-17
forum: Programming Talk
---

### Post by barisurum on 2009-12-17
Hello people;

I recently started learning gui programming in FLTK. I have a question about DMM in this example (main program):
```

// FLTK text program. (text output field).
// 0.1.4

#include <Fl/Fl.H>
#include <Fl/Fl_Window.H>
#include "textoutput.h"
#include "box.h"



int main( int argc, char ** argv )
{
    //OBJ
        Fl_Window * textWindow_OBJ_PTR = new Fl_Window( 800, 600 );
        Box * textBox_OBJ_PTR = new Box( 10, 10, 300, 50, "FLTK TEXT" );
        TextOutput * textOutput_OBJ_PTR = new TextOutput( 10, 80, 350, 30, "An example text output! You can't edit this :)" );

    textWindow_OBJ_PTR ->end();
    textWindow_OBJ_PTR ->show();


    return Fl::run();

    delete textBox_OBJ_PTR; textBox_OBJ_PTR = 0;
    delete textOutput_OBJ_PTR; textOutput_OBJ_PTR = 0;
    delete textWindow_OBJ_PTR; textWindow_OBJ_PTR = 0;
}
```

First I dynamically allocate a window directly from the main program as you can see.

Then I dynamically allocate a title box and a text field object which are defined and implemented in their respective header and cpp files (textoutput.h, textoutput.cpp, box.h, box.cpp). In those files I again dynamically allocate respective Fl_Box and Fl_Output objects.

And then I delete all the objects from memory in main program.

Question 1: Is this approach a sane and correct one?

Question 2: Does FLTK automatically deallocate the memory of the window (and objects tied to this hierarchy) when return FL::run() returns?

---

### Post by dwhitney67 on 2009-12-17
This is the last statement that will be executed in the main() function:
```

return Fl::run();

```
Any code appearing after this statement will not be executed.

Perhaps it would be better to write the code as:
```

int main(int argc, char** argv)
{
    ...

    int rtn= Fl::run();

    delete textBox_OBJ_PTR;    textBox_OBJ_PTR = 0;
    delete textOutput_OBJ_PTR; textOutput_OBJ_PTR = 0;
    delete textWindow_OBJ_PTR; textWindow_OBJ_PTR = 0;

    return rtn;
}

```

IMO, the 'delete' statements are not really necessary since the program is exiting; this memory will be collected by the system for use by other applications.  It's only when the application is in continuous operation that you need to worry about memory leaks.

---

### Post by barisurum on 2009-12-17
Thanks dwhitney.

---

