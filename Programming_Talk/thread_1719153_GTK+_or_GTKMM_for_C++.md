---
title: "GTK+ or GTKMM for C++?"
date: 2011-04-01
forum: Programming Talk
---

### Post by u-noob-tu on 2011-04-01
Hey all,

i think im pretty close to designing my first graphical program, but im confused about what libraries to use to make it. i have the "Devhelp" documentation program, which is a little confusing, and im not sure if i should be including headers for GTK+ or GTKMM. i thought i read that GTKMM is for C++, but im not 100% sure thats right. plus, im having trouble with classes and the layering of the widgets of each window. i cant seem to find a clear guide on how things are supposed to be ordered. if anyone wants to take a look at my source code and give me some pointers, ill put it up for you to look at. it will be very appreciated.

thanks all. :)

```
#include <iostream>
#include <string>
#include <gtk/gtk.h>
#ifndef _WINDOW_H_
#define _WINDOW_H_
using namespace std;

class Gtk::Window
{
public:
    virtual Gtk::Window::~Window();

    virtual bool verify() const = 0;

    virtual void doit();

    const char *id() const;

    void doVerify();

protected:
    virtual double whatName() = 0;

};

#endif // _WINDOW_H_

int main()
{
    string name;
    string password;
    cout << "Please enter your name";
    cin >> name;
    cout << "Please enter your password";
    cin >> password;
    if ((name == "Ryan") && (password == "password"))
         {
             cout << "Welcome, Ryan. What do you want to do first?" << endl;
         }
         cout << "Press ENTER to continue" << endl;
         cin.get();
         return 0;
     }
```

---

### Post by JupiterV2 on 2011-04-01
If using C++, then I would recommend using gtkmm as it is the GTK+ language binding for C++.

BTW, it is quite unusual to include boilerplate code outside of a header:

```
#ifndef BOILERPLATE_H
#define BOILERPLATE_H 1
...
#endif /* BOILERPLATE_H */
```

This code is to prevent multiple declarations of functions and data types when including a header into multiple files. Are you sure this is what you want to do?

---

### Post by deathadder on 2011-04-01
Since you're using C++ it has to be GTKMM, have a look at the documentation here, they have a great tutorial that I found really helpful: [http://www.gtkmm.org/en/documentation.html](http://www.gtkmm.org/en/documentation.html)

I think you might want to get the idea of classes etc understood before you add another layer (GUI's) on top of that. It'll be easier if you have a good understanding of how classes, and OOP work in C++ before trying to use GTKMM as the way widgets are inherited will make more sense.

You may want to have a read about the STL and classes from here: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by u-noob-tu on 2011-04-01
Gtkmm it is then. I'm not sure how my program should look. I saw an example online and that was my best effort to make it work for me. It compiled fine, got no errors, but based on what you said it probably won't run.

---

### Post by mmix on 2011-04-01
try vala.
[http://live.gnome.org/Vala](http://live.gnome.org/Vala)

---

