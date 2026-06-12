---
title: "How to correctly compile FLTK with g++?"
date: 2011-05-24
forum: Programming Talk
---

### Post by SterlingM on 2011-05-24
I am trying to compile an fltk file with g++. The solution in this thread does not work for me - 
[http://ubuntuforums.org/showthread.php?t=176994](http://ubuntuforums.org/showthread.php?t=176994)
The problem I am having is that the file will compile seemingly okay, but when I run it, there are no widgets.
The solution here -
[http://www3.telus.net/public/robark/](http://www3.telus.net/public/robark/)
does not work because I do not have the X11R6 libraries. I tried converting those to just the X11 folders, but that would not even compile.
Some other thing I have tried -

```

g++ -o go guiwindow.cpp -L/home/sterling/Downloads/fltk-1.3.x-r8695/FL -lfltk -lXext -lX11 -lm

g++ $(fltk-config --compile) -o go guiwindow.cpp -L/home/sterling/Downloads/fltk-1.3.x-r8695/FL -lfltk -lXext -lX11 -lm

g++ -L/home/sterling/Dtownloads/fltk-1.3.x-r8695/FL -lfltk -lXext -lX11 -lm -o go guiwindow.cpp

```

These are just the first ones I have in the terminal history. I have tried many more combinations. This is the code for what I am doing - 

```

void GUIWindow::cb_stop(Fl_Widget* o, void* v) {
    Fl_Button* b = (Fl_Button*)o;
    b->label("Good Job");
    b->resize(50,75,100,50);
    b->redraw();
}


GUIWindow::GUIWindow(int w, int h, const char* title) : Fl_Window(w, h, title) {

    begin();
        stop = new Fl_Button(50, 75, 70, 30, "Stop");
        stop->callback(cb_stop, this);
        drive = new Fl_Button(150, 75, 70, 30, "Test");
    end();
    resizable(this);
    show();
}

GUIWindow::~GUIWindow() {}


int main() {
    GUIWindow w(300,200,"Testing");
    return Fl::run();
}

```

fltk-config --compile guiwindow.cpp works for just one file, but I need to use this one file with other files in a project. Thats what I am trying to use g++. What does the fltk-config --compile do differently that my g++ scripts aren't? If anyone could help me, I would extremely grateful.

---

### Post by MadCow108 on 2011-05-24
please always post the error message

this should compile (provided you fix the compilation errors your above code has):
```
g++ test.cxx `fltk-config --cxxflags --ldflags`
```
or static variant
```
g++  test.cxx `fltk-config --cxxflags --libs` -lXft -lXinerama
```

---

### Post by SterlingM on 2011-05-24
Thank you for the reply. I didn't notice it before, but when I do fltk-config --compile, it outputs a g++ script. I guess I just overlooked it as "stuff" earlier. I just copied the g++ script it outputted and it began to work. The script was -
g++ -I/usr/local/include -I/usr/local/include/FL/images -I/usr/include/freetype2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_THREAD_SAFE -D_REENTRANT -o GUIWindow GUIWindow.cpp /usr/local/lib/libfltk.a -lXext -lXft -lfontconfig -lXinerama -lpthread -ldl -lm -lX11

---

### Post by keghn on 2012-12-12
Hello.
 Could not get Madcow line to work.
 But what I have been using for years are:

g++ `fltk-config --cxxflags` test.cxx `fltk-config --ldflags` -o test

                or use:

g++ `fltk-config --cxxflags` test.cpp `fltk-config --ldflags` -o test

 To run:

./test

 Those line have been working great on Ubuntu 8.10 to 12.04 and Mint mate 13, and 
Mint 14 mate.
 This is for fluid and fltk 1.3.
Fltk 2.0 is near dead.

---

