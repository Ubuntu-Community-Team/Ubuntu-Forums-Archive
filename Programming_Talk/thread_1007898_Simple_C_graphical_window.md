---
title: "Simple C graphical window"
date: 2008-12-10
forum: Programming Talk
---

### Post by brandon88tube on 2008-12-10
I'm new to C and I am trying to make a simple graphical window pop up that says "Hello World!", but I haven't found any tutorials to really help me on this. I think examples help. The only other program I have been able to make in C so far was this:
```
#include <stdio.h>

int main()
{
  printf("Hello World!\n");
  return 0;
}
```
This was with some help. Yeah I know that its sad and I might be moving a little fast to try and get a window to pop up, but I don't want my stuff limited to the terminal.

---

### Post by dwhitney67 on 2008-12-10
Try looking into using GTK+.  Here's a link:  [http://www.gtk.org/](http://www.gtk.org/)

---

### Post by brandon88tube on 2008-12-10
I already looked into that, but I wanted to know if there was a way of doing this that was somewhat cross-platform. Also, to tell you the truth, it confused me.

---

### Post by ZuLuuuuuu on 2008-12-10
Doing some GUI (Graphical User Interface) stuff requires usually great C knowledge. If the only C program you can write with your current C knowledge is "Hello World", I suggest you to improve your C knowledge first, since even a simple GUI program requires knowledge of variables, function calls, pointers and macros. Only then you can learn graphical toolkits like GTK. And in C you don't have much choice for graphical toolkits. GTK is the current best one (and it _is_ cross-platform).

---

### Post by brandon88tube on 2008-12-10
Oh, wasn't aware it was cross-platform... Hmm, I was only looking at making a simple program and it turns out to be a big major ordeal.

---

### Post by mdurham on 2008-12-11
maybe all he wants to do is run his 'hello world' program in a terminal?

---

### Post by mmix on 2008-12-11
```
 /*
   Simple Xlib application drawing a box in a window.
 */
 
 #include<X11/Xlib.h>
 #include<stdio.h>
 
 int main() {
   Display *d;
   int s;
   Window w;
   XEvent e;
 
                        /* open connection with the server */
   d=XOpenDisplay(NULL);
   if(d==NULL) {
     printf("Cannot open display\n");
     exit(1);
   }
   s=DefaultScreen(d);
 
                        /* create window */
   w=XCreateSimpleWindow(d, RootWindow(d, s), 10, 10, 100, 100, 1,
                         BlackPixel(d, s), WhitePixel(d, s));
 
                        /* select kind of events we are interested in */
   XSelectInput(d, w, ExposureMask | KeyPressMask);
 
                        /* map (show) the window */
   XMapWindow(d, w);
 
                        /* event loop */
   while(1) {
     XNextEvent(d, &e);
                        /* draw or redraw the window */
     if(e.type==Expose) {
       XFillRectangle(d, w, DefaultGC(d, s), 20, 20, 10, 10);
     }
                        /* exit on key press */
     if(e.type==KeyPress)
       break;
   }
 
                        /* destroy our window */
   XDestroyWindow(d, w);
 
                        /* close connection to server */
   XCloseDisplay(d);
 
   return 0;
 }
```

> cc sample.c -I/usr/include -L/usr/lib -lX11

./a.out

---

### Post by wmcbrine on 2008-12-11
When I see the phrase "simple C graphical window", my first thought is "oxymoron". But my second thought is "SDL". I was able to learn it and build a working game in just a few hours.

SDL won't get you the standard GUI look, though. There's no really simple path to that.

---

### Post by wd5gnr on 2008-12-11
I agree -- forget windowing for awhile. And cross platform windowing is even worse.

However, if you insist, wxWidgets is a pretty good tool kit. However, it is C++ -- but maybe you should be focused on that anyway. In particular, C++ will let you write (nearly) C code if that's what you want to do. Very few differences at the core. But a C++ LIBRARY can make your life a lot easier with very little effort on your part. Here's why:

I could in theory write the GNR library to create simple window applications. I could provide a class GNRWin that is a full blown application that does... NOTHING. So your program could be something like:

```
#include "GNRWin.h"
GNRWin mainwindow;

void main() { mainwindow.start(); }
```


So what? Well I could leave little "hooks" for you to customize this do nothing app. So maybe:


```
#include "GNRWin.h"
class MyWin : public GNRWin
  {
  public:
  void SetOutput(GNRContext &win);
  } mainwindow;

void main() { mainwindow.start(); }

void MyWin::SetOutput(GNRContext &win)
  {
  win.text(10,10,"Hello World!");
  }
```

This is all made up of course but it is how real things like Wx, MFC, OWL, etc. work. In the example, I left a "hook" named SetOutput. By default it does nothing. But you've just replaced my empty one with one that says Hello World. You are basically writing C code with a few new ideas (class override, references, but nothing really hard).

Now if you want to stick with command line C, you could always use shell scripts with GUI front ends to drive the command line. Check out Kommander, Dialog, Whiptail, and zenity. I'm sure there are others.

---

### Post by brandon88tube on 2008-12-11
Thanks for trying to help me out guys. Just out of curiosity I tried this code and tried to compile it. I ended getting a lot of errors the first being error: X11/Xlib.h: No such file or directory. Am I missing something?

> **mmix said:**
> ```
 /*
   Simple Xlib application drawing a box in a window.
 */
 
 #include<X11/Xlib.h>
 #include<stdio.h>
 
 int main() {
   Display *d;
   int s;
   Window w;
   XEvent e;
 
                        /* open connection with the server */
   d=XOpenDisplay(NULL);
   if(d==NULL) {
     printf("Cannot open display\n");
     exit(1);
   }
   s=DefaultScreen(d);
 
                        /* create window */
   w=XCreateSimpleWindow(d, RootWindow(d, s), 10, 10, 100, 100, 1,
                         BlackPixel(d, s), WhitePixel(d, s));
 
                        /* select kind of events we are interested in */
   XSelectInput(d, w, ExposureMask | KeyPressMask);
 
                        /* map (show) the window */
   XMapWindow(d, w);
 
                        /* event loop */
   while(1) {
     XNextEvent(d, &e);
                        /* draw or redraw the window */
     if(e.type==Expose) {
       XFillRectangle(d, w, DefaultGC(d, s), 20, 20, 10, 10);
     }
                        /* exit on key press */
     if(e.type==KeyPress)
       break;
   }
 
                        /* destroy our window */
   XDestroyWindow(d, w);
 
                        /* close connection to server */
   XCloseDisplay(d);
 
   return 0;
 }
```

---

### Post by snova on 2008-12-11
Probably the X headers. Dunno what the package you need is called...

There really is no such thing as a "simple" GUI toolkit for C. I am of the opinion that the situation improves a little with C++, but even then- GUI is nothing simple.

SDL is a graphics library (among other things), I think. I don't know whether it has anything GUI-related.

---

### Post by brandon88tube on 2008-12-11
I decided to try using GTK+ and they actually have a tutorial for making a window that says Hello World. [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD). The thing is I can't compile this program for the life of me. I tried what they suggested on this page [http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html) , but it won't work. Can anyone help me out with this?

---

### Post by dwhitney67 on 2008-12-11
You did not specify exactly what problem you are having... thus how can I help?

I copied the helloworld.c program as listed on the website, pasted it into a file that I created on my system, bearing the same name.

Then I compiled/linked the application without incident using this statement:
```

gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \
`pkg-config --libs gtk+-2.0`

```

If compiling is holding you up, then it is quite possible that you are missing the GTK+ development package(s) on your system.  Use synaptic (or apt-get) to install it.

---

### Post by brandon88tube on 2008-12-11
To make sure I am doing this correctly, is that one entire line of code or two separate lines?

---

### Post by dwhitney67 on 2008-12-11
The command as it appears on the website has a \ character in it, thus making it two lines.  I was hoping in my post that it would appear as one line, but it did not.

I have edited my previous post to include a backslash (\) character.  Now you should be able to copy/paste the statement to your terminal.

---

### Post by brandon88tube on 2008-12-11
I could have swore I had all the needed packages, but it failed with this;
```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \
> `pkg-config --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
helloworld.c:1:21: error: gtk/gtk.h: No such file or directory
helloworld.c:5: error: expected ‘)’ before ‘*’ token
helloworld.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘delete_event’
helloworld.c:30: error: expected ‘)’ before ‘*’ token
helloworld.c: In function ‘main’:
helloworld.c:40: error: ‘GtkWidget’ undeclared (first use in this function)
helloworld.c:40: error: (Each undeclared identifier is reported only once
helloworld.c:40: error: for each function it appears in.)
helloworld.c:40: error: ‘window’ undeclared (first use in this function)
helloworld.c:41: error: ‘button’ undeclared (first use in this function)
helloworld.c:45: warning: implicit declaration of function ‘gtk_init’
helloworld.c:48: warning: implicit declaration of function ‘gtk_window_new’
helloworld.c:48: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
helloworld.c:55: warning: implicit declaration of function ‘g_signal_connect’
helloworld.c:55: warning: implicit declaration of function ‘G_OBJECT’
helloworld.c:56: warning: implicit declaration of function ‘G_CALLBACK’
helloworld.c:56: error: ‘delete_event’ undeclared (first use in this function)
helloworld.c:56: error: ‘NULL’ undeclared (first use in this function)
helloworld.c:62: error: ‘destroy’ undeclared (first use in this function)
helloworld.c:65: warning: implicit declaration of function ‘gtk_container_set_border_width’
helloworld.c:65: warning: implicit declaration of function ‘GTK_CONTAINER’
helloworld.c:68: warning: implicit declaration of function ‘gtk_button_new_with_label’
helloworld.c:74: error: ‘hello’ undeclared (first use in this function)
helloworld.c:79: warning: implicit declaration of function ‘g_signal_connect_swapped’
helloworld.c:80: error: ‘gtk_widget_destroy’ undeclared (first use in this function)
helloworld.c:84: warning: implicit declaration of function ‘gtk_container_add’
helloworld.c:87: warning: implicit declaration of function ‘gtk_widget_show’
helloworld.c:95: warning: implicit declaration of function ‘gtk_main’
```

Also sorry for making you go through all of this trouble. I am probably just making dumb mistakes.

---

### Post by dwhitney67 on 2008-12-11
You merely need to install the gtk+-2.0 package(s).  I believe this is the correct package to install:
```

sudo apt-get install libgtk2.0-dev

```

---

### Post by brandon88tube on 2008-12-11
Thank you so much! That was all I needed to get the program to work...funny how I didn't have that one package though.

EDIT: I did notice that the button resized itself if you resized the window. Is this normal?

---

### Post by dwhitney67 on 2008-12-11
Yes, it is normal.  The same thing occurs when programming in Java.  To prevent this from happening, I believe one needs to place button(s) inside a separate container than the container used by the main window.  The separate container(s) are then added to the container used by the main window.  It is not uncommon to have one or more containers inside another container, and yet more containers inside these.

Btw, I do not know GTK+ at all, and it is been awhile since I have programmed in Java.

---

### Post by brandon88tube on 2008-12-12
Well thanks again. Unfortunately you might be seeing more of me as I will undoubtedly have some more problems down the road. Though I will try to resolve them without causing problems for others.

---

### Post by BloGTK on 2008-12-12
Out of curiosity, why C? If you're interested in producing GUI apps, you're better off starting with an easier language like Python than trying to learn C. Once you get the basics of UNIX programming, it's easier to apply those concepts to a language like C.

C is the language you would use if you wanted to be a UNIX guru, but it's a royal pain if all you want to do is create a GUI app.

Also, try installing Glade - it lets you build your apps GUI graphically rather than trying to code all the containers and widgets yourself.

---

### Post by brandon88tube on 2008-12-12
I chose C kind of randomly, but I wanted it to be fast and possibly cross-platform. Though python looks to be easier the __ confused me and c just came up so I said "what the heck".

---

