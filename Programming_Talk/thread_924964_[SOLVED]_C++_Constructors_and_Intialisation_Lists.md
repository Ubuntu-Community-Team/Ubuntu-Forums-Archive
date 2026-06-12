---
title: "[SOLVED] C++ Constructors and Intialisation Lists"
date: 2008-09-20
forum: Programming Talk
---

### Post by cybrid on 2008-09-20
Hi there, I'm not totally sure if I can post a thread like this here, but I don't see where I could, so here it goes.

I'm learning C++ and Gtk programming along, and I'm facing a understanding problem. I don't see why the next code is wrong.

```

#include <gtkmm/window.h>
#include <gtkmm/button.h>
#include <iostream>
#include <string>

using namespace std;

class MyWindow : public Gtk::Window {

        public:
                MyWindow();
                virtual ~MyWindow();

        private:
                string windowTitle;
                Gtk::Button* m_button;
};

MyWindow::MyWindow(){
        windowTitle = "My First Gtk App";
        m_button = new Gtk::Button("Hello");
}
MyWindow::~MyWindow(){
        delete m_button;
}  
```

---

### Post by jespdj on 2008-09-20
This belongs in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum.

---

### Post by cybrid on 2008-09-20
Strange....I don't see it in the front page :(

Also, please delete this thread, I've created it again where it belongs.

---

### Post by cybrid on 2008-09-20
Hi there, I'm not totally sure if I can post a thread like this here, but I don't see where I could, so here it goes.

I'm learning C++ and Gtk programming along, and I'm facing a understanding problem. I don't see why the next code is wrong.

```

#include <gtkmm/window.h>
#include <gtkmm/button.h>
#include <iostream>
#include <string>

using namespace std;

class MyWindow : public Gtk::Window {

        public:
                MyWindow();
                virtual ~MyWindow();

        private:
                string windowTitle;
                Gtk::Button* m_button;
};

MyWindow::MyWindow(){
        windowTitle = "My First Gtk App";
        m_button = new Gtk::Button("Hello");
}
MyWindow::~MyWindow(){
        delete m_button;
}  
```

---

### Post by cb951303 on 2008-09-20
where is your main function?

PS: always post the error msg along with source ...

---

### Post by cybrid on 2008-09-20
I don't think "main" to be necessary but if you wan it, here it is:

```
#include "MyClass.cpp"
#include <gtkmm/main.h>

int main (int argc, char* argv[]){

        Gtk::Main kit(argc, argv);

        MyWindow myWindow;

        Gtk::Main::run(myWindow);

        return 0;
}
```

And the error I'm getting:

```
xabi@cairhien:~$ g++ main.cpp MyClass.cpp -o simple `pkg-config gtkmm-2.4 --cflags --libs`
/tmp/ccFLOEHw.o: In function `virtual thunk to MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x17c): multiple definition of `virtual thunk to MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x17c): first defined here
/tmp/ccFLOEHw.o: In function `non-virtual thunk to MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x18c): multiple definition of `non-virtual thunk to MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x18c): first defined here
/tmp/ccFLOEHw.o: In function `MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x194): multiple definition of `MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x194): first defined here
/tmp/ccFLOEHw.o: In function `virtual thunk to MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x3a8): multiple definition of `virtual thunk to MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x3a8): first defined here
/tmp/ccFLOEHw.o: In function `non-virtual thunk to MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x3b8): multiple definition of `non-virtual thunk to MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x3b8): first defined here
/tmp/ccFLOEHw.o: In function `MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x3c0): multiple definition of `MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x3c0): first defined here
/tmp/ccFLOEHw.o: In function `MyWindow::~MyWindow()':
MyClass.cpp:(.text+0x5d4): multiple definition of `MyWindow::~MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x5d4): first defined here
/tmp/ccFLOEHw.o: In function `MyWindow::MyWindow()':
MyClass.cpp:(.text+0x7f2): multiple definition of `MyWindow::MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0x7f2): first defined here
/tmp/ccFLOEHw.o: In function `MyWindow::MyWindow()':
MyClass.cpp:(.text+0x9a2): multiple definition of `MyWindow::MyWindow()'
/tmp/ccLgBZ23.o:main.cpp:(.text+0xa52): first defined here
collect2: ld devolvió el estado de salida 1
```

---

### Post by cb951303 on 2008-09-20
first of all it should be "myclass.hpp" but that's not the problem. Since I compile and run your code without a problem it has something to do with your compilation string. here is what I used:
```

g++ main.cpp -o main `pkg-config gtkmm-2.4 --cflags --libs` 
```

---

### Post by cybrid on 2008-09-20
I'm sorry about my ignorance, but.. shouldn't the build string be:

```
g++ main.cpp MyClass.cpp -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

---

### Post by cb951303 on 2008-09-20
> **cybrid said:**
> I'm sorry about my ignorance, but.. shouldn't the build string be:

```
g++ main.cpp MyClass.cpp -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

no, MyClass should be in a header file. You can't include a source file. So this should work.
```

g++ main.cpp -o main `pkg-config gtkmm-2.4 --cflags --libs`

```

:popcorn:

---

### Post by cb951303 on 2008-09-20
I think you want to do this

MyClass.hpp
```

#include <gtkmm/window.h>
#include <gtkmm/button.h>
#include <iostream>
#include <string>

using namespace std;

class MyWindow : public Gtk::Window {

        public:
                MyWindow();
                virtual ~MyWindow();

        private:
                string windowTitle;
                Gtk::Button* m_button;
};

```

MyClass.cpp
```

#include "MyClass.hpp"

MyWindow::MyWindow(){
        windowTitle = "My First Gtk App";
        m_button = new Gtk::Button("Hello");
}
MyWindow::~MyWindow(){
        delete m_button;
}

```

main.cpp
```

#include "MyClass.hpp"
#include <gtkmm/main.h>

int main (int argc, char* argv[]){

        Gtk::Main kit(argc, argv);

        MyWindow myWindow;

        Gtk::Main::run(myWindow);

        return 0;
}
```

```
g++ main.cpp MyClass.cpp -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

---

### Post by cybrid on 2008-09-20
Oh, I see now, only headers and main function must be included in the compilation command, so if a class declaration and implementation is done in the same file, it must not be included in the compilation command since it's considered to be a header, am I right?.

---

### Post by K.Mandla on 2008-09-20
Moved to Programming Talk; merged similar threads.

---

### Post by scourge on 2008-09-20
> **cybrid said:**
> Oh, I see now, only headers and main function must be included in the compilation command, so if a class declaration and implementation is done in the same file, it must not be included in the compilation command since it's considered to be a header, am I right?.

Something like that but not exactly. You can #include a source file, although it's considered bad practice. In your example you've included MyClass.cpp in main.cpp, which is the equivalent of inserting the contents of MyClass.cpp at the beginning of main.cpp. So when you run "g++ main.cpp MyClass.cpp -o simple `pkg-config gtkmm-2.4 --cflags --libs`", you're actually trying to compile MyClass.cpp twice.

You'll get this problem with header files as well, if you include them in more than one place. To eliminate the problem you can use an #include guard: [http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard). It's a good idea to use them in every header file. So your MyClass.hpp (or MyClass.h) would look like this:
```

#ifndef MYCLASS_H
#define MYCLASS_H

#include <gtkmm/window.h>
#include <gtkmm/button.h>
#include <string>

class MyWindow : public Gtk::Window {

        public:
                MyWindow();
                virtual ~MyWindow();

        private:
                string windowTitle;
                Gtk::Button* m_button;
};

#endif // MYCLASS_H

```

I removed the <iostream> header from there, since it's not needed. And having something like "using namespace std;" in a header file is a really bad idea. Whether or not it should be done in source files is debatable.

---

### Post by cybrid on 2008-09-20
Thank you both for the help, now it's totaly clear. I already thought that it had something to do with me not understanding correctly initialisation lists or overwriting the default constructor hehehe.

---

