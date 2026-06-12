---
title: "maximize, fullscreen (GTKMM)"
date: 2010-03-05
forum: Programming Talk
---

### Post by gtkman on 2010-03-05
Dear all! 

I'm new to this forum, and sorry for my poor English.

I think I do not understand something in reference to resizing the widgets.

I'm trying to write an application which use fullscreen window. There is a child widget (Gtk::Fixed, Gtk::HBox etc.) in main window. I need to add some widgets to this child (Gtk:ScrolledWindow and my custom widget)

Everything works fine if it is in the constructor of the main window. (   MainWindow::MainWindow()   )

for example:

Gtk::Fixed mainfixed;
Gtk::Button button1;

[B]MainWindow::MainWindow()
{
maximize();
fullscreen();
add(mainfixed);

button1.set_size_request(...........
mainfixed.put(button1,........
}[/B]

But I have to place some widgets to the right side of window after it is maximized. I can get the size of the window by on_configure_event, but I cannot resize the child widget (Gtk::Fixed) of main window. Every widgets which I placed outside the area that allocated in constructor's widgets will be invisible.

for example (in constructor):

[B]button1.set_size_request(100,50);
mainfixed.put(button1,500,100);[/B]

allocated area: 600x150 pixel

If any widget exceed on coordinate 600;150 will invisible. What I do wrong?

Thank you!

---

### Post by PaulM1985 on 2010-03-05
Are you using show_all_children() at the end of the constructor?

Can you do a get size (not sure on the exact function name) to find out what size it thinks it is at the end of the constructor?

Paul

You should only have to call one of fullscreen() or maximize(), I don't think you have to do both.

---

### Post by gtkman on 2010-03-06
> **PaulM1985 said:**
> Are you using show_all_children() at the end of the constructor?

Dear Paul!

Every widgets created in contructor are automatically showed. There is no porblem with them. My problem is that I can not position widgets dependent upon maximized (or fullscreen) window size.

Gtk::Window -------> Gtk::Fixed -------> My Widgets

Gtk::Fixed assumes the size of the area that used in constructor. The border of this area is the coordinates of the right-bottom corner of the farthest widget. I can not add (or move!) any widget outside of this area after constructor run out. I have tried the set_resize_mode(Gtk::RESIZE_IMMADIATE) before maximize() and resize_children() after it but they produced no effect  Resizing Gtk::Fixed is futile too.

I found a (half) solutions today. I have connected two own functions to a signal_window_state and signal_expose_event. In function which connected to signal_window_state I can sense the maximized or fullscreen state. I moved all adding commands of child widgets into the function which connected to signal_expose_event. The constructor contains only fullscreen() and signal connecting commands now.

It is only a half solution, because signal_expose_event is emitted many time even after window is maximized, and on the first calling the window size is invalid.

---

### Post by SledgeHammer_999 on 2010-03-06
Hi gtkman,

I have a lot of experience with Gtkmm in the field you are having problems. (containers, widgets, repositioning). I would like to help you, but I cannot understand exactly what you are saying or what the problem is or what is the behaviour you seek. But I have a really simple solution. Please provide an exapmle program that shows the problem you're having. Add some comments to the code where the problems arises and mention what YOU would like to happen. I need a functional program to give an answer(because I will test it myself and try to figure out where it goes wrong).

PS: when posting code please use the [code] [/ code] tags. It makes it easier for other people to read the code.

---

### Post by gtkman on 2010-03-06
Dear SledgeHammer!

I started a brand new project, and it is working perfectly (now)! :)

I think I mixed up the order of the commands in previous version.

```


class MainWindow : public Gtk::Window
{
public:
    MainWindow();
    virtual ~MainWindow();
    Gtk::Fixed mainfixed;
    Gtk::ScrolledWindow scrolled;
    bool on_my_configure_event(GdkEventConfigure* event);
};

MainWindow::MainWindow()
{    
    fullscreen();
    add(mainfixed);    
    signal_configure_event().connect(sigc::mem_fun(*this, &MainWindow::on_my_configure_event),false);
}

MainWindow::~MainWindow()
{
    
}

bool MainWindow::on_my_configure_event(GdkEventConfigure* event)
{
    scrolled.set_size_request(300,event->height-20);
    mainfixed.put(scrolled,event->width-310,10);
    scrolled.show();
    return false;
}


```

Thank you for your helpful attitude!

---

### Post by SledgeHammer_999 on 2010-03-07
I am glad you found the answer by yourself. I'll be around if another problem arises. Happy coding.

---

### Post by gtkman on 2010-03-24
Dear all!

I have a problem with fullscreen mode again.

Is it possible to raise a window over the "fullscreen state" main window?

The...
```

mysecondwindow.get_window()->raise();

```
... simply does nothing. The second window remains behind the main window.

The...
```

unfullscreen();
mysecondwindow.get_window()->raise();
fullscreen();

```
...is working, but it is an ugly solution and I need to click somewhere on main window to make it fullscreen again. The "grab_focus" does not help.

Thank You!

---

### Post by SledgeHammer_999 on 2010-03-24
How about [Gtk::Window::present()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html#a7d848c59fc1a42f4a296461515c0476e)?

---

### Post by gtkman on 2010-03-24
> **SledgeHammer_999 said:**
> How about [Gtk::Window::present()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html#a7d848c59fc1a42f4a296461515c0476e)?

It does the same thing like raise().

I think, there is some difference from this point of view between the two computers I use. (ubuntu 8.10 and ubuntu 9.10)

On first: raise/present does not raise the window to front if the main window is in fullscreen state. (as I have written before)

On second: raise/present raises the window to front, but the ubuntu panels appear while second window is displayed. If I close this window, the panels disappear, and main window is in fullscreen state again. Maybe, it is absolutely logical that panels are visible during a not fullscreen window is displayed.

---

### Post by SledgeHammer_999 on 2010-03-24
Oh yeah I don't know how I forgot that. Some backstory:
I am making a video player and I wanted for the controls to appear, while on fullscreen, above the video. It was easy to fullscreen the window on which the video was being drawn onto. The difficult part was to display the controls(play/pause/stop buttons) above the video. I was baffled, but I took a quick look on Totem's source. I found the answer by looking at the relevant glade file.

To make it short: In the constructor of the [Gtk::Window](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html#aa3273081166e86df1850738a17ecdb09) use as Gtk::WindowType the [Gtk::WINDOW_POPUP](http://library.gnome.org/devel/gtkmm/unstable/group__gtkmmEnums.html#ga8c724168aabf37953fbb194b35ad250f).

This will make the window appear above the fullscreen window, but I don't know if you have decorations(the min/max/close buttons etc).

---

### Post by gtkman on 2010-03-25
> **SledgeHammer_999 said:**
> Gtk::Window use as Gtk::WindowType the [Gtk::WINDOW_POPUP](http://library.gnome.org/devel/gtkmm/unstable/group__gtkmmEnums.html#ga8c724168aabf37953fbb194b35ad250f).

popup.h
```

#ifndef _MYPOPUP_H
#define	_MYPOPUP_H

class MyPopup : public Gtk::Window
{
public:
    MyPopup();
    virtual ~MyPopup();
};

#endif

```

popup.cpp:
```

#include "mypopup.h"

MyPopup::MyPopup()
{
    
}

MyPopup::~MyPopup()
{
    
}

```

main.cpp:
```

class MainWindow : public Gtk::Window
{
public:
    
    MyPopup popup;
    Gtk::Button button;
    Gtk::Fixed fixed;

    MainWindow();
    virtual ~MainWindow();
    void on_button_clicked();

};

void MainWindow::on_button_clicked()
{
    popup.present();
}

MainWindow::MainWindow()
{
    fullscreen();
    button.set_size_request(100,100);
    add(fixed);
    fixed.put(button,10,10);
    button.signal_clicked().connect(sigc::mem_fun(*this, &MainWindow::on_button_clicked));
}

MainWindow::~MainWindow()
{

}

```

------------------------------------------

I have tried to insert...
```

MyPopup::MyPopup()
{
    Window(Gtk::WINDOW_POPUP);
}

```
..but I have received an error message: 
"invalid use of qualified-name Gtk::WINDOW_POPUP"

I do not understand what kind of parameter what "Window" function is waiting for.

---

### Post by PaulM1985 on 2010-03-25
Just a guess...

Try using:
Window(WINDOW_POPUP);

instead of
Window(Gtk::WINDOW_POPUP);

Paul

---

### Post by SledgeHammer_999 on 2010-03-25
I had the same problem too(I am an amatuer also in C++ :P)

Anyways, take a look here [http://www.cplusplus.com/doc/tutorial/inheritance/](http://www.cplusplus.com/doc/tutorial/inheritance/) a few lines under the header that says: **What is inherited from the base class?**

In your case you should(I haven't tested it, I have no access to the compiler ATM):
```
#ifndef _MYPOPUP_H
#define	_MYPOPUP_H

class MyPopup : public Gtk::Window
{
public:
    MyPopup(Gtk::WindowType type);
    virtual ~MyPopup();
};

#endif
```

```

#include "mypopup.h"

MyPopup::MyPopup(Gtk::WindowType type) : Gtk::Window(type)
{
    
}

MyPopup::~MyPopup()
{
    
}

```

---

### Post by gtkman on 2010-03-25
Another amateur question: :)

How to declare a MyPopup class object in main.cpp in this case?

MyPopup popup(Gtk::WINDOW_POPUP) gives:

error: &#8216;Gtk::WINDOW_POPUP&#8217; is not a type (ok, I am stupid, it works as a declaration of a function, not an object)

---

### Post by SledgeHammer_999 on 2010-03-25
So does that mean that you fixed it?

---

### Post by gtkman on 2010-03-25
> **SledgeHammer_999 said:**
> So does that mean that you fixed it?

Unfortunately not.

I do not understand, where I have to set the type to Gtk::WINDOW_POPUP. In the main.cpp? And how to declare the object. Sorry, I am totally beginner in C++.

---

### Post by SledgeHammer_999 on 2010-03-25
The biggest problem with the code example you provided is that you had forgotten to #inlcude stuff. I added some other things here and there to make it work and display "nicely"

popup.h
[php]
#ifndef _MYPOPUP_H
#define	_MYPOPUP_H

#include <gtkmm/window.h>
#include <gtkmm/button.h>

class MyPopup : public Gtk::Window
{
public:
    MyPopup(Gtk::WindowType type);
    virtual ~MyPopup();
    Gtk::Button button;
};

#endif[/php]

popup.cpp
[php]
[#include "popup.h"

MyPopup::MyPopup(Gtk::WindowType type) : Gtk::Window(type), button("Another sample")
{
  add(button);
  show_all();    
}

MyPopup::~MyPopup()
{
    
}[/php]

main.cpp
[php]
#include "popup.h"

#include <gtkmm/main.h>
#include <gtkmm/button.h>
#include <gtkmm/fixed.h>
#include <gdkmm/color.h>

class MainWindow : public Gtk::Window
{
public:
    
    MyPopup popup;
    Gtk::Button button;
    Gtk::Fixed fixed;

    MainWindow();
    virtual ~MainWindow();
    void on_button_clicked();

};

void MainWindow::on_button_clicked()
{
    popup.show();
    popup.move(100, 100);    
}

MainWindow::MainWindow(): popup(Gtk::WINDOW_POPUP), button("Sample label")
{
    fullscreen();
    button.set_size_request(100,100);
    add(fixed);
    fixed.put(button,10,10);
    button.signal_clicked().connect(sigc::mem_fun(*this, &MainWindow::on_button_clicked));
    popup.hide();
    show_all();
}

MainWindow::~MainWindow()
{

}

int main(int argc, char *argv[])
{
    Gtk::Main main_loop(argc, argv);
    MainWindow window;
    main_loop.run(window);
    return 0;
}[/php]

If I did something you cannot understand please let me know and I'll explain.

---

### Post by gtkman on 2010-03-25
It is working!

This was the key:

```

MainWindow::MainWindow(): popup(Gtk::WINDOW_POPUP) .....

```

Thank You very much SledgeHammer_999!

---

### Post by SledgeHammer_999 on 2010-03-25
No Problem. I suggest reading a little bit about initialization lists. The first hit from google-->[http://www.cprogramming.com/tutorial/initialization-lists-c++.html](http://www.cprogramming.com/tutorial/initialization-lists-c++.html)


EDIT: oh yeah now I noticed. Stupid mistake by me. I wrote Gtk::Window(type) instead of popup(type). Sorry...
EDIT2: nevermind I was wrong again.

---

