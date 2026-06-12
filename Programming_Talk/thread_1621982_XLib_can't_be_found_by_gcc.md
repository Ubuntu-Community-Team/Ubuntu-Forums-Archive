---
title: "XLib can't be found by gcc"
date: 2010-11-14
forum: Programming Talk
---

### Post by austinprete on 2010-11-14
Hello,

I was recently trying to write a C application that used XLib following an example.  The app looked like this:
```
 /*
   Simple Xlib application drawing a box in a window.
   gcc input.c -o output -lX11
 */
 
 #include <X11/Xlib.h>
 #include <stdio.h>
 #include <stdlib.h>
 #include <string.h>
 
 int main(void) {
   Display *d;
   Window w;
   XEvent e;
   char *msg = "Hello, World!";
   int s;
 
                        /* open connection with the server */
   d = XOpenDisplay(NULL);
   if (d == NULL) {
     fprintf(stderr, "Cannot open display\n");
     exit(1);
   }
 
   s = DefaultScreen(d);
 
                        /* create window */
   w = XCreateSimpleWindow(d, RootWindow(d, s), 10, 10, 200, 200, 1,
                           BlackPixel(d, s), WhitePixel(d, s));
 
                        /* select kind of events we are interested in */
   XSelectInput(d, w, ExposureMask | KeyPressMask);
 
                        /* map (show) the window */
   XMapWindow(d, w);
 
                        /* event loop */
   while (1) {
     XNextEvent(d, &e);
                        /* draw or redraw the window */
     if (e.type == Expose) {
       XFillRectangle(d, w, DefaultGC(d, s), 20, 20, 10, 10);
       XDrawString(d, w, DefaultGC(d, s), 50, 50, msg, strlen(msg));
     }
                        /* exit on key press */
     if (e.type == KeyPress)
       break;
   }
 
                        /* close connection to server */
   XCloseDisplay(d);
 
   return 0;
 }

```gcc returned an error while trying to compile saying that X11/Xlib.h could not be found.  I found similar posts with the question on other forums, but none were Ubuntu specific.  It'd be great if you could either help me find an answer or link to somewhere it has previously been discussed.

Thanks

---

### Post by worksofcraft on 2010-11-15
Your program compiles and runs just fine on my computer... attached is the window it displays.

I suspect you have not installed X11 developer files. There should be a folder called /usr/include/X11, but I can't remember what you need to do to install them.

---

### Post by austinprete on 2010-11-15
Ah, that's probably it.  Was thinking Xlib came installed on Ubuntu to begin with.  I'll see if I can find a solution to install the dev files, I'll let you know if I find anything.

---

### Post by Zugzwang on 2010-11-15
Dear OP (original poster),

You have ran into the problem that some files are missing on your system. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.

---

### Post by Vox754 on 2010-11-15
> **austinprete said:**
> Ah, that's probably it.  Was thinking Xlib came installed on Ubuntu to begin with.  I'll see if I can find a solution to install the dev files, I'll let you know if I find anything.

Xlib comes installed on Ubuntu just like most libraries. Well, actually, runtime libraries, also called dynamically-linked libraries (.dll) in Windows, and shared objets in Linux (.so), are the ones included. But to compile and link programs that use Xlib, you need to install the proper development files, mostly C or C++ headers (.h).

So, whenever you are trying to compile anything, don't just assume it will work. First, search for the specific -dev packages which contain the headers.

---

