---
title: "g++ doesn't like char *"
date: 2008-06-17
forum: Programming Talk
---

### Post by techmarks on 2008-06-17
I did the class MyWindow which is just for the simple Fltk window,


```

class MyWindow : public Fl_Window
{
  public:
		//Constructor and destructor
    MyWindow(int width, int height, char *title);
    virtual ~MyWindow();
};

```


 the main program is like this;

```

#include <Fl/Fl.h>
#include "MyWindow.h"

int main(int argc, char** args)
{
	// Construct the window
  MyWindow myWindow(400, 400, "first window");
	// Show the window
  myWindow.show();
	// Run FLTK
  Fl::run();

  return 0;
}

```


And then I compiled it with this command;

```

$ g++ -I/usr/local/include
 -I/usr/local/include/freetype2
 -I/usr/local/include
 -O2 -fno-strict-aliasing -pipe
 -I/usr/local/include
 -o main main.cpp
 -o MyWindow MyWindow.cpp
 -L/usr/local/lib
 -L/usr/local/lib
 -L/usr/local/lib
 -lm /usr/local/lib/libfltk.a -lXft -lXext -lX11

```

 the program compiles but I get a warning;

```

main.cpp: In function 'int main(int, char**)':
main.cpp:21: warning: deprecated conversion from string constant to 'char*'
$ 

```


I'm passing the MyWindow constructor the string
literal "first window", for the functions prototype is
char *title.

It's just a warning but I can't make it warning go away
anybody know what that means? or why?

---

### Post by LaRoza on 2008-06-17
> **techmarks said:**
> 
It's just a warning but I can't make it warning go away
anybody know what that means? or why?

It is deprecated. A workable, but an older convention that is not recommended and may be gone in the future. You can get rid of it by using std::string.

---

### Post by techmarks on 2008-06-17
I tried using string but still the warning

seems no way to be rid of it

---

### Post by Jessehk on 2008-06-17
This snippet works fine for me. 

```

#include <iostream>
#include <string>

class Widget {
public:
    explicit Widget( int width, int height, const std::string &title );
    virtual ~Widget() {}
};

Widget::Widget( int width, int height, const std::string &title ) {
    std::cout << "Creating a window with a title of \""
              << title << "\""
              << std::endl;
}

int main() {
    Widget widget( 400, 400, "first window" );
}

```

---

### Post by techmarks on 2008-06-17
(from MyWindow.h)
```

class MyWindow : public Fl_Window
{
  public:
		//Constructor and destructor
    MyWindow(int width, int height, const std::string &title);
    virtual ~MyWindow();
};

```



```


#include "MyWindow.h"


MyWindow::MyWindow(int width, int height, const std::string &title) 
         : Fl_Window(width, height, title)

{}

MyWindow::~MyWindow()

{}

```


```

#include <Fl/Fl.h>
#include "MyWindow.h"



              
 int main(int argc, char** args)
 {

string s("my window");

	MyWindow myWindow(400, 400, "my window");
	myWindow.show();
	
	Fl::run();
	
	return 0;
}

```




now it doesn't compile that way
the error;

```


MyWindow.cpp:20: error: prototype for 'MyWindow::MyWindow(int, int, char*)' does not match any in class 'MyWindow'
MyWindow.h:21: error: candidates are: MyWindow::MyWindow(const MyWindow&)
MyWindow.h:24: error:                 MyWindow::MyWindow(int, int, const std::string&)
$ 




```

---

### Post by geirha on 2008-06-18
EDIT: err ... nvm, would have produced a completely different error.
EDIT2: Ok, I tried your code, but I got a different error. Very similar to yours, but about FL_Window, which didn't take string as third argument. I can't figure out how to reproduce your errors though.

mywindow.h
```

#ifndef MYWINDOW_H
#define MYWINDOW_H
#include <FL/Fl.H>
#include <FL/Fl_Window.H>
#include <iostream>

class MyWindow : public Fl_Window
{
    public:
        MyWindow(int width, int height, const std::string &title);
        virtual ~MyWindow();
};
#endif

```

```

#include "mywindow.h"

MyWindow::MyWindow(int width, int height, const std::string &title)
             : Fl_Window(width, height, title.c_str()) {}
MyWindow::~MyWindow() {}

               
int main(int argc, char** args)
{   
    std::string title("my window");

    MyWindow myWindow(400, 400, title);
    myWindow.show();
    Fl::run();

    return 0;
}

```

The above two files compiles and runs for me, giving me a grey window titled "my window".

---

