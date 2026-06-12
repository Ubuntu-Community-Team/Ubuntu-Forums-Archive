---
title: "Image not loading in gtkmm when using a .desktop file."
date: 2014-06-29
forum: Programming Talk
---

### Post by govert1991 on 2014-06-29
Hello,

Recently I started learning gtkmm, and one of my programs has some strange behaviour when used in combination with a .desktop file. The program should take an image (which comes from an external file), and display a window with just that image inside it.
It does this fine when I launch the program from the command line, but when I use the .desktop file to launch it it just displays the broken image picture.
Does anyone know whether this has to do with my still poor gtkmm skills or do I have to add something to the .desktop file to tell it that the executable needs the image file? I've included my desktop file and the source code of my program below.

Thanks in advance!

Tutorial.desktop
```
[Desktop Entry]
Version=1.0
Name=Tutorial 3.5
Comment=Hope this works...
Exec=/home/govert/projects/gtkmmtutorials/tutorial3_5/Tutorial
Icon=/home/govert/projects/gtkmmtutorials/tutorial3_5/Info.png
Terminal=false
Type=Application
Category=Application

```

Main.cpp
```
#include "Window.h"
#include <gtkmm/application.h>


int main(int argc, char* argv[]){
    Glib::RefPtr<Gtk::Application> app = Gtk::Application::create(argc,argv,"org.gtkmm.example");


    Experiment experiment; 


    return app->run(experiment);
}

```

Window.h
```
#ifndef WINDOW_H
#define WINDOW_H


#include <gtkmm/window.h>
#include <gtkmm/image.h>


class Experiment : public Gtk::Window{
public:
    Experiment();
    virtual ~Experiment();
protected:
    Gtk::Image Picture;
};


#endif

```

Window.cpp
```
#include "Window.h"


Experiment::Experiment() : Picture("Info.png"){
    set_title("I hope this works");
    set_border_width(10);


    add(Picture);


    show_all_children();
}


Experiment::~Experiment(){
}

```

---

### Post by spjackson on 2014-06-30
When you specify Picture("Info.png"), you are referring to a file in your current working directory. So you need to get your app to run in the right directory for this to work. One way to do this is to add
```

Path=/home/govert/projects/gtkmmtutorials/tutorial3_5

```
to your .desktop file.

---

### Post by govert1991 on 2014-06-30
Thank you. In the end I managed to get it working by typing the full path in the source code, but your way is better since you don't have to hard-code the location that way.

---

### Post by ofnuts on 2014-06-30
A program shouldn't have a dependency on its work directory.

If the image and the executable are located in the same directory, you can retrieve the directory of the actual path/name of the executable (apply readlink() to /proc/self/exe) and create the complete path to the image from that. A program shouldn't have a dependency on its work directory.

---

