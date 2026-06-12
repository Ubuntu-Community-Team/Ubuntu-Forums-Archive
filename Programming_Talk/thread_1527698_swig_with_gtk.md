---
title: "swig with gtk"
date: 2010-07-09
forum: Programming Talk
---

### Post by miak on 2010-07-09
Hi,

I know this may sound a little bit stupid since there is pygtk, but i was wondering if anyone has tried or has any idea how to use swig with gtk??

The reason I'm trying to use gtk with swig instead of pygtk, is that GUI written in c is much faster then GUI written in pygtk(I'm working on updating images).

Thanks,
miak

---

### Post by kknd on 2010-07-09
I've done that, for 'fun'. I've created a GTK wrapper and then used swig to generate bindings for other languages. You will have some challenges when dealing with g_signal_connect and etc, but besides that it's like any other library.

---

### Post by miak on 2010-07-10
Can you by any chance give me the code you wrote?

I seem to have some troubles including gtk libraries into the build command

---

### Post by miak on 2010-07-12
Hi,

I still didn't figure out the way to compile gtk code into a python module.

I'm using swig and distutils
I have a hello.c witch is standard helloworld written in c, which can be found [here]("http://library.gnome.org/devel/gtk-tutorial/stable/c39.html")
hello.i is here :
```
%module hello

%inline %{
extern void hello( GtkWidget *widget, gpointer data);
extern gboolean delete_event( GtkWidget *widget, GdkEvent  *event, gpointer   data );
extern void destroy( GtkWidget *widget, gpointer   data );
extern int main (int argc, char *argv[] );

%}
```Here is what i do
```
swig -python hello.i
```, which works ok and produces hello_wrap.c and hello.py
after that i do 
```
python setup.py build_ext
```, and here when i get my problems.
Here is the error message printed to the terminal
```
running build_ext
building '_helloWorld' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I-pthread -I-D_REENTRANT -I-I/usr/include/gtk-2.0 -I-I/usr/lib/gtk-2.0/include -I-I/usr/include/atk-1.0 -I-I/usr/include/cairo -I-I/usr/include/pango-1.0 -I-I/usr/include/gio-unix-2.0/ -I-I/usr/include/glib-2.0 -I-I/usr/lib/glib-2.0/include -I-I/usr/include/pixman-1 -I-I/usr/include/freetype2 -I-I/usr/include/directfb -I-I/usr/include/libpng12 -I-pthread -I-lgtk-x11-2.0 -I-lgdk-x11-2.0 -I-latk-1.0 -I-lgio-2.0 -I-lpangoft2-1.0 -I-lgdk_pixbuf-2.0 -I-lm -I-lpangocairo-1.0 -I-lcairo -I-lpango-1.0 -I-lfreetype -I-lfontconfig -I-lgobject-2.0 -I-lgmodule-2.0 -I-lgthread-2.0 -I-lrt -I-lglib-2.0 -I/usr/include/python2.6 -c hello_wrap.c -o build/temp.linux-x86_64-2.6/hello_wrap.o
hello_wrap.c:2700: error: expected ‘)’ before ‘*’ token
hello_wrap.c:2701: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘delete_event’
hello_wrap.c:2702: error: expected ‘)’ before ‘*’ token
hello_wrap.c: In function ‘_wrap_hello’:
hello_wrap.c:2866: error: ‘GtkWidget’ undeclared (first use in this function)
hello_wrap.c:2866: error: (Each undeclared identifier is reported only once
hello_wrap.c:2866: error: for each function it appears in.)
hello_wrap.c:2866: error: ‘arg1’ undeclared (first use in this function)
hello_wrap.c:2866: error: expected expression before ‘)’ token
hello_wrap.c:2867: error: ‘gpointer’ undeclared (first use in this function)
hello_wrap.c:2867: error: expected ‘;’ before ‘arg2’
hello_wrap.c:2880: error: expected expression before ‘)’ token
hello_wrap.c:2889: error: ‘arg2’ undeclared (first use in this function)
hello_wrap.c:2889: error: expected expression before ‘)’ token
hello_wrap.c:2892: warning: implicit declaration of function ‘hello’
hello_wrap.c: In function ‘_wrap_delete_event’:
hello_wrap.c:2902: error: ‘GtkWidget’ undeclared (first use in this function)
hello_wrap.c:2902: error: ‘arg1’ undeclared (first use in this function)
hello_wrap.c:2902: error: expected expression before ‘)’ token
hello_wrap.c:2903: error: ‘GdkEvent’ undeclared (first use in this function)
hello_wrap.c:2903: error: ‘arg2’ undeclared (first use in this function)
hello_wrap.c:2903: error: expected expression before ‘)’ token
hello_wrap.c:2904: error: ‘gpointer’ undeclared (first use in this function)
hello_wrap.c:2904: error: expected ‘;’ before ‘arg3’
hello_wrap.c:2914: error: ‘gboolean’ undeclared (first use in this function)
hello_wrap.c:2914: error: expected ‘;’ before ‘result’
hello_wrap.c:2921: error: expected expression before ‘)’ token
hello_wrap.c:2926: error: expected expression before ‘)’ token
hello_wrap.c:2935: error: ‘arg3’ undeclared (first use in this function)
hello_wrap.c:2935: error: expected expression before ‘)’ token
hello_wrap.c:2938: error: ‘result’ undeclared (first use in this function)
hello_wrap.c:2938: warning: implicit declaration of function ‘delete_event’
hello_wrap.c:2939: error: expected expression before ‘)’ token
hello_wrap.c:2939: error: too few arguments to function ‘SWIG_Python_NewPointerObj’
hello_wrap.c: In function ‘_wrap_destroy’:
hello_wrap.c:2948: error: ‘GtkWidget’ undeclared (first use in this function)
hello_wrap.c:2948: error: ‘arg1’ undeclared (first use in this function)
hello_wrap.c:2948: error: expected expression before ‘)’ token
hello_wrap.c:2949: error: ‘gpointer’ undeclared (first use in this function)
hello_wrap.c:2949: error: expected ‘;’ before ‘arg2’
hello_wrap.c:2962: error: expected expression before ‘)’ token
hello_wrap.c:2971: error: ‘arg2’ undeclared (first use in this function)
hello_wrap.c:2971: error: expected expression before ‘)’ token
hello_wrap.c:2974: warning: implicit declaration of function ‘destroy’
error: command 'gcc' failed with exit status 1

```Lots of extra libraries are libraries produced by ```
`pkg-config --cflags --libs gtk+-2.0`
```Here is my setup.py:
```
#!/usr/bin/env python


"""
setup.py for gtk helloworld (hello.c)
"""

from distutils.core import Extension, setup


hello_module = Extension('_helloWorld',
                         include_dirs = [  '-pthread', 
                                        '-D_REENTRANT', 
                                        '-I/usr/include/gtk-2.0', 
                                        '-I/usr/lib/gtk-2.0/include', 
                                        '-I/usr/include/atk-1.0', 
                                        '-I/usr/include/cairo', 
                                        '-I/usr/include/pango-1.0', 
                                        '-I/usr/include/gio-unix-2.0/', 
                                        '-I/usr/include/glib-2.0', 
                                        '-I/usr/lib/glib-2.0/include', 
                                        '-I/usr/include/pixman-1', 
                                        '-I/usr/include/freetype2', 
                                        '-I/usr/include/directfb', 
                                        '-I/usr/include/libpng12', 
                                        '-pthread', 
                                        '-lgtk-x11-2.0', 
                                        '-lgdk-x11-2.0', 
                                        '-latk-1.0', 
                                        '-lgio-2.0', 
                                        '-lpangoft2-1.0', 
                                        '-lgdk_pixbuf-2.0', 
                                        '-lm', 
                                        '-lpangocairo-1.0', 
                                        '-lcairo', 
                                        '-lpango-1.0', 
                                        '-lfreetype', 
                                        '-lfontconfig', 
                                        '-lgobject-2.0', 
                                        '-lgmodule-2.0', 
                                        '-lgthread-2.0', 
                                        '-lrt', 
                                        '-lglib-2.0', 
                                        ], 
                         sources=['hello_wrap.c', 'hello.c'],)

setup (name = 'helloWorld',
       version = '0.1',
       author      = "arsen",
       description = "desc",
       ext_modules = [hello_module],
       py_modules = ["helloWorld"],
       )
```ANYONE PLEASE, any help will be so much appreciated.
Best,
miak

---

