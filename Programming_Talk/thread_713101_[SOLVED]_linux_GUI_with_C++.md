---
title: "[SOLVED] linux GUI with C++"
date: 2008-03-02
forum: Programming Talk
---

### Post by StOoZ on 2008-03-02
if I understood it correctly, its being done using gtkmm right?
if so, seems like when I use netbeans ,and I try to include : <gtkmm.h> the compiler complains that its not available (well obviously...was just cheking).
now I know where to donwload these libaries from, but I dont know how to make to compiler (netbeans) to recognize where they are , so I could use the include command.

im yet to download it.
thanks.

---

### Post by jpeddicord on 2008-03-02
If you install the package libgtkmm-2.4-dev, the libraries will automatically be installed right into your compiler's path. At that point all you need is a simple #include <gtkmm.h>. Hope that answers your question!

---

### Post by StOoZ on 2008-03-02
thanks.

---

### Post by Sockerdrickan on 2008-03-02
Actually try to use #include <cgtkmm> probably wont work though

---

### Post by StOoZ on 2008-03-05
Im having alot of troubles with it, I have this simple code:
> #include <gtkmm-2.4/gtkmm.h>
using namespace std;

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}

the path of the include is ok (using netbeans).
now I get this a huge error when trying to compile, this is only a part of it,but all of it looks the same:
> g++    -c -g -o build/Debug/GNU-Linux-x86/newfile.o newfile.cc
In file included from newfile.cc:1:
/usr/include/gtkmm-2.4/gtkmm.h:29:20: error: glibmm.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:30:19: error: gdkmm.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:32:26: error: gtkmm/object.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:33:31: error: gtkmm/aboutdialog.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:34:28: error: gtkmm/accelkey.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:35:30: error: gtkmm/accelgroup.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:36:30: error: gtkmm/adjustment.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:37:29: error: gtkmm/alignment.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:38:25: error: gtkmm/arrow.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:39:31: error: gtkmm/aspectframe.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:40:29: error: gtkmm/assistant.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:41:24: error: gtkmm/base.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:42:23: error: gtkmm/bin.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:43:23: error: gtkmm/box.h: No such file or directory
....
.....
> /usr/include/gtkmm-2.4/gtkmm.h:182:28: error: gtkmm/viewport.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:183:26: error: gtkmm/widget.h: No such file or directory
/usr/include/gtkmm-2.4/gtkmm.h:184:26: error: gtkmm/window.h: No such file or directory
newfile.cc:13:2: warning: no newline at end of file
newfile.cc: In function ‘int main(int, char**)’:
newfile.cc:6: error: ‘Gtk’ has not been declared
newfile.cc:6: error: expected `;' before ‘kit’
newfile.cc:8: error: ‘Gtk’ has not been declared
newfile.cc:8: error: expected `;' before ‘window’
newfile.cc:10: error: ‘Gtk’ has not been declared
newfile.cc:10: error: ‘window’ was not declared in this scope
make[1]: *** [build/Debug/GNU-Linux-x86/newfile.o] Error 1
make[1]: Leaving directory `/home/nathan/NetBeansProjects/Application_1'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.



any idea how to solve this??

---

### Post by WW on 2008-03-05
I'm not on an Ubuntu computer where I can test this now, but you shouldn't have to use **gtkmm-2.4** in the #include statement, i.e. you should just have
```

#include <gtkmm.h>

```
Then, if necessary, add the option **-I/usr/include/gtkmm-2.4** to the g++ command that compiles the program.

---

### Post by StOoZ on 2008-03-05
> **WW said:**
> I'm not on an Ubuntu computer where I can test this now, but you shouldn't have to use **gtkmm-2.4** in the #include statement, i.e. you should just have
```

#include <gtkmm.h>

```
Then, if necessary, add the option **-I/usr/include/gtkmm-2.4** to the g++ command that compiles the program.

the "#include <gtkmm.h>" statement doesnt work , it doesnt even find the 'gtkmm.h'
I've installed the gtkmm files using the synaptic... so i have them installed

---

### Post by WW on 2008-03-05
Then you have to tell the compiler where to find gtkmm.h.  If you are using g++ in the command line, you would just add the option -I/usr/include/gtkmm-2.4 to the command.

However, you said you are using Netbeans.  I've never used Netbeans, but I'm sure there must be a way to add compiler options.  Any Netbeans gurus out there?

---

### Post by StOoZ on 2008-03-05
someone? :(

---

### Post by WW on 2008-03-05
You could try asking here: [http://www.nabble.com/Netbeans---Users-f2605.html](http://www.nabble.com/Netbeans---Users-f2605.html)

For what it's worth, [here](nabble.com/adding-include-directories-%28cnd%29-to11784193.html#a11784193) is a question from that forum that seems relevant.

---

### Post by StOoZ on 2008-03-06
I tried  , no help there , thanks anyway.
well I've a way, too add to the project command line (project properties in netbeans) these values:
> -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0  -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0


and then it works.
BUT(!): its really annoying, and im sure there is a better way, why cant I just add the "include <gtkmm.h> " and everything will work fine, like with
 iostream etc... :(

anyone?

---

### Post by sznurek on 2008-03-06
```

g++ -o main main.cpp `pkg-config --cflags gtkmm-2.4` `pkg-config --libs gtkmm-2.4`

```
??

---

### Post by StOoZ on 2008-03-06
I mean that I dont want to use these commands,I want netbeans to automatically find it...
isnt that the reason (one of...) that we use IDE's?
I got tired from adding such lines to the netbean's console each time I want to build/compile a program with libraries that are not included with C++...

---

### Post by LaRoza on 2008-03-06
> **StOoZ said:**
> I mean that I dont want to use these commands,I want netbeans to automatically find it...
isnt that the reason (one of...) that we use IDE's?
I got tired from adding such lines to the netbean's console each time I want to build/compile a program with libraries that are not included with C++...

It is probably possible to make your IDE use them, however, it would require knowledge of that specific application. I suggest looking into the documentation of your IDE to see how.

---

### Post by xlinuks on 2008-04-12
> **StOoZ said:**
> I mean that I dont want to use these commands,I want netbeans to automatically find it...
isnt that the reason (one of...) that we use IDE's?
I got tired from adding such lines to the netbean's console each time I want to build/compile a program with libraries that are not included with C++...
A bit late but might help other people:
You have to set the properties of the project. Right-click your project name, choose properties, then set the include directories for your compiler and (perhaps) linker. Here's a short video I recorded (1.2MB)
[http://xlinuks.googlepages.com/netbeans.ogg](http://xlinuks.googlepages.com/netbeans.ogg)

---

### Post by StOoZ on 2008-04-12
thats is very useful, thanks a alot! :guitar:

---

### Post by Fabioamd87 on 2010-11-10
not found :(

---

### Post by worksofcraft on 2010-11-10
QT is an alternative to Gtk.
It comes with a very nice looking IDE and on the command line all you have to type is make -project and then make.
Try this tutorial Hello World program to help you choose ;)
[http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html)

---

### Post by Fabioamd87 on 2010-11-10
I will try.

---

