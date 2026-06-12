---
title: "gtkmm Question: Opening Multiple Instances of a GtkWindow from a GtkBuilder"
date: 2010-06-13
forum: Programming Talk
---

### Post by linguae on 2010-06-13
Hello. I am currently working on a project written in C++ that uses the gtkmm wrapper of GTK+. The user interface is designed in a file created by Glade that uses the new GtkBuilder file format. One problem that I have been trying to figure out is how to open multiple copies of a window that was initialized by a GtkBuilder object. Calling the show() method on a GtkWindow does not display an additional instance of the window. Do I need to create a deep copy of the GtkWindow (and its container objects) that I want to display more than once, or is there an alternate approach? And if I have to create a deep copy of the window and its objects, how do I do that with gtkmm? Is it just a simple copy using the = operator, or is it more complicated than that? 

Below is my source code: 
[PHP]
#include <gtkmm.h> 
#include <iostream> 

void openChildWindow(); 

Gtk::Window *mainWindow; 
Gtk::Button *mainButton; 
Gtk::Window *childWindow; 

void openChildWindow() 
{ 
   std::cout << "Button clicked" << std::endl; 
   childWindow->show(); // NOTE: This is wrong 
} 

int main(int argc, char **argv) 
{ 
   Gtk::Main kit(&argc, &argv); 

   Glib::RefPtr<Gtk::Builder> builder = 
    Gtk::Builder::create_from_file("multiwindow.glade"); 

   builder->get_widget("mainWindow", mainWindow); 
   builder->get_widget("mainButton", mainButton); 
   builder->get_widget("childWindow", childWindow); 

   mainButton->signal_clicked().connect(sigc::ptr_fun(&openChildWindow)); 

   kit.run(*mainWindow); 
} 
[/PHP]


And below is my .glade file: 
[PHP]
<?xml version="1.0"?> 
<interface> 
  <!-- interface-requires gtk+ 2.8 --> 
  <!-- interface-naming-policy project-wide --> 
  <object class="GtkWindow" id="mainWindow"> 
    <property name="title" translatable="yes">Main Window</property> 
    <child> 
      <object class="GtkVBox" id="vbox1"> 
        <property name="visible">True</property> 
        <property name="orientation">vertical</property> 
        <child> 
          <object class="GtkLabel" id="label1"> 
            <property name="visible">True</property> 
            <property name="label" translatable="yes">Main Window</property> 
          </object> 
          <packing> 
            <property name="position">0</property> 
          </packing> 
        </child> 
        <child> 
          <object class="GtkButton" id="mainButton"> 
            <property name="label" translatable="yes">Open Child Window</property> 
            <property name="visible">True</property> 
            <property name="can_focus">True</property> 
            <property name="receives_default">True</property> 
            <property name="yalign">0.60000002384185791</property> 
          </object> 
          <packing> 
            <property name="position">1</property> 
          </packing> 
        </child> 
      </object> 
    </child> 
  </object> 
  <object class="GtkWindow" id="childWindow"> 
    <property name="title" translatable="yes">Child Window</property> 
    <child> 
      <object class="GtkLabel" id="label1"> 
        <property name="visible">True</property> 
        <property name="xalign">0.38999998569488525</property> 
        <property name="label" translatable="yes">Child Window</property> 
      </object> 
    </child> 
  </object> 
</interface> 
[/PHP]

---

### Post by SledgeHammer_999 on 2010-06-13
Let's say you want 3 windows of "childwindow", then you do something like this:
[php]
Gtk::Window *childWindow;
Gtk::Window *childWindow1;
Gtk::Window *childWindow2;


int main(int argc, char **argv) 
{ 
  .....
  builder->get_widget("childWindow", childWindow);  
  builder->get_widget("childWindow", childWindow1);  
  builder->get_widget("childWindow", childWindow2);
  ...
}[/php]
  
If you want an unspecified number of "childwindows" then you should an std::vector to store the Gtk::Window pointers.

Each Gtk::Window pointer points to an instantce of a particular Gtk::Window. If you want more "windows" then that means you want more instances of that widget/class/Gtk::Window so you have to use additional pointers to point to that instance/data.

---

### Post by linguae on 2010-06-13
Hello, again.  I tried your solution by implementing an array of pointers to Gtk::Window objects, and calling builder->get_widget() on an unreserved pointer to a Gtk::Window.  The problem, however, is that builder->get_widget() assigns the pointer of the internal childWindow to the pointer that I give the function, resulting in the same problem as the last piece of code.

Here is my modified code:

[PHP]
#include <gtkmm.h>
#include <iostream>

void openChildWindow();

Gtk::Window *mainWindow;
Gtk::Button *mainButton;
Glib::RefPtr<Gtk::Builder> builder;

Gtk::Window **children;
int counter = 0;

void openChildWindow()
{
   std::cout << "Button clicked" << std::endl;

   if (counter >= 10)
      return;

   builder->get_widget("childWindow", children[counter]);

   std::cout << "Index is " << counter << " and pointer of button is " << 
    children[counter] << std::endl;

   children[counter++]->show();
}

int main(int argc, char **argv)
{
   Gtk::Main kit(&argc, &argv);

   children = new Gtk::Window *[10];

   builder = Gtk::Builder::create_from_file("multiwindow.glade");

   builder->get_widget("mainWindow", mainWindow);
   builder->get_widget("mainButton", mainButton);

   mainButton->signal_clicked().connect(sigc::ptr_fun(&openChildWindow));

   kit.run(*mainWindow);
   delete[] children;
}
[/PHP]

I also tried dereferencing the pointer to the child window to obtain a copy of the object, and then assigning it to a Gtk::Window object, but the compiler complained about that (this is in a separate run with different code that used *; apparently the = operator is private on a Gtk::Window object):

```

/usr/include/gtkmm-2.4/gtkmm/window.h: In function ‘void openChildWindow()’:
/usr/include/gtkmm-2.4/gtkmm/window.h:173: error: ‘Gtk::Window& Gtk::Window::operator=(const Gtk::Window&)’ is private
multiwindow.cpp:21: error: within this context

```

Is there a way I can force the Gtk::Builder object to generate another copy of "childWindow"?

---

### Post by SledgeHammer_999 on 2010-06-15
Hmm you are right.

Maybe the purpose of a Gtk::Builder is to have just one instance of the widgets in the glade file.

If that is the case I suggest this. Move the childWindow widget to its own glade file. Then make as many Gtk::Builder instances as you want and feed each instance with the same childWindow glade file. Something like this:

[php]
....
Glib::RefPtr<Gtk::Builder> builder, builder2;

builder = Gtk::Builder::create_from_file("multiwindow.glade"); 
builder2 = Gtk::Builder::create_from_file("multiwindow.glade");

Gtk::Window *childWindow, *childWindow2;

builder->get_widget("childWindow", childWindow)
builder2->get_widget("childWindow", childWindow2)
...
[/php]

I know this is messy. Maybe you should ask the gtkmm mailing list.
Disclaimer: I haven't actually used glade. I always construct my UI through code.

---

