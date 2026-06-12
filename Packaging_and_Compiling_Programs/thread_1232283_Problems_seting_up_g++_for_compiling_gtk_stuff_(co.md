---
title: "Problems seting up g++ for compiling gtk stuff (complete newbie to ubuntu and c++)"
date: 2009-08-05
forum: Packaging and Compiling Programs
---

### Post by Pinecone_ on 2009-08-05
Hi,

I'm new to ubuntu and C++, I still have to use Windows at school though, so I thought I'd try developing cross platform stuff with c++ and gtk, but got stopped in my tracks at the first steps. I found a tutorial somewhere (cant remember where now) which had this example code:

```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}
```I saved the above as Test.cpp and ran this:

```
$ g++ Test.cpp -o Test
```which gave me this:

```
Test.cpp:1:21: error: gtk/gtk.h: No such file or directory
Test.cpp: In function &#8216;int main(int, char**)&#8217;:
Test.cpp:6: error: &#8216;GtkWidget&#8217; was not declared in this scope
Test.cpp:6: error: &#8216;window&#8217; was not declared in this scope
Test.cpp:8: error: &#8216;gtk_init&#8217; was not declared in this scope
Test.cpp:10: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; was not declared in this scope
Test.cpp:10: error: &#8216;gtk_window_new&#8217; was not declared in this scope
Test.cpp:11: error: &#8216;gtk_widget_show&#8217; was not declared in this scope
Test.cpp:13: error: &#8216;gtk_main&#8217; was not declared in this scope
```
So I'm guessing I haven't set up gtk to work right with g++ or something.

I know g++ works, as i compiled this earlier (from another tutorial)

```
#include <iostream>

using namespace std;

int main() {
    cout << "Hello World!\n";
    return 0;
}
```
So my question is, what do i need to do to get g++ to find the header files and such for compiling gtk things? Also, what would I need to keep in mind in order to compile things for windows as well? And are there any good tutorials that explain cross platform development with gtk, which explain steps compiling on windows and ubuntu (or any other linux which the steps would be the same or similar) for someone who has never used c++ before?

It's alot to ask I think, but thanks in advance for any help.

---

### Post by MadCow108 on 2009-08-05
first you need the gtk devellopment package which includes the needed headers:
*sudo apt-get install libgtk2.0-dev*

then you need to pass the right flags, include paths and librarys to g++ to compile.
the easiest way to do that is to use pkg-config. this will print all needed flags.
So to compile type:
*g++ `pkg-config gtk+-2.0 --libs --cflags` Test.cpp*
you can see all packages which pkg-config knows about by typing *pkg-config --list-all*

there also are c++ bindings for gtk in the gtkmm package which I find easier to use. the packages are libgtkmm-2.4-1c2a and libgtkmm-2.4-dev and pkg-config package name is gtkmm-2.4

---

### Post by Pinecone_ on 2009-08-05
Thanks, that got the first bit of code i posted to compile. I also looked up gtkmm and it looks much easier.

I am now trying to compile this:

```
#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    Gtk::Main::run(window);
    return 0;
}
```

with ```
$ g++ `pkg-config gtkmm-2.4 --cflags --libs` Test.cpp -o ../Test
```

and get ```
Test.cpp:1:25: error: gtkmm.h: No such file or directory
Test.cpp: In function ‘int main(int, char**)’:
Test.cpp:4: error: ‘Gtk’ has not been declared
Test.cpp:4: error: expected `;' before ‘kit’
Test.cpp:5: error: ‘Gtk’ has not been declared
Test.cpp:5: error: expected `;' before ‘window’
Test.cpp:6: error: ‘Gtk’ has not been declared
Test.cpp:6: error: ‘window’ was not declared in this scope
```

I'm guessing it's the same problem I had before with gtk, but I don't know what packages I need to install, I couldn't find anything that worked by searching.

A lot of things said to install libgtkmm2.0-dev
but using apt-get to install that, I got ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtkmm2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtkmm2.0-dev has no installation candidate
``` and don't know what to do from there.

Thanks again

---

### Post by Leslie Viljoen on 2009-08-06
Try libgtkmm-2.4-dev   (you even mention 2.4 in your command line!)

Want a quick list of the options? Do:

sudo apt-get install libgtkmm<TAB><TAB>

---

