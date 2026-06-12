---
title: "programming X needs help"
date: 2012-04-01
forum: Programming Talk
---

### Post by conradin on 2012-04-01
Hi All I'm trying to program X, and wrote what seemed like a simple bit of code. It compiles without error, and seems to run, but a X-window never appears! Can some one look at this code snippet and tell me where I'm going wrong? What do i need to get an X-window to appear? Do in need to run this from?

Im compiling with: gcc -o xfile -Wall xfile.c -lX11 
which gives me: 
```

$ ./xfile
Display 0x9f88008 lnScreen 0 
Depth 24 


```

```

#include <stdio.h>
#include <stdlib.h>     /* declares malloc() */
#include <unistd.h>
#include <X11/Xlib.h>

int main( int argc, char * argv[]){

int s,depth;
Display* d;

d = XOpenDisplay(NULL);
if(d==NULL){
	printf("Cannot open display \n");
	return 1;}
	

printf("Display %p ln", d);

s=DefaultScreen(d);
printf("Screen %d \n", s);
depth=DefaultDepth(d,s);
printf("Depth %d \n ", depth);
XCloseDisplay(d);

sleep(10);
return 0;
}

```

---

### Post by pbrane on 2012-04-01
XopenDisplay does not create a window. You have to do that with other functions depending on the toolkit you are using.

Have a look at this link: [http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html]("http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html")

---

### Post by alexfish on 2012-04-01
hello-x Example .. Hope it helps

compile

[LIST]
[*] gcc -L/usr/X11R6/lib -lX11 hello-x.c -o hello-x
[/LIST]
 ```
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
 
   d = XOpenDisplay(NULL);
   if (d == NULL) {
      [fprintf]("http://www.opengroup.org/onlinepubs/009695399/functions/fprintf.html")(stderr, "Cannot open display\n");
      [exit]("http://www.opengroup.org/onlinepubs/009695399/functions/exit.html")(1);
   }
 
   s = DefaultScreen(d);
   w = XCreateSimpleWindow(d, RootWindow(d, s), 10, 10, 100, 100, 1,
                           BlackPixel(d, s), WhitePixel(d, s));
   XSelectInput(d, w, ExposureMask | KeyPressMask);
   XMapWindow(d, w);
 
   while (1) {
      XNextEvent(d, &e);
      if (e.type == Expose) {
         XFillRectangle(d, w, DefaultGC(d, s), 20, 20, 10, 10);
         XDrawString(d, w, DefaultGC(d, s), 10, 50, msg, [strlen]("http://www.opengroup.org/onlinepubs/009695399/functions/strlen.html")(msg));
      }
      if (e.type == KeyPress)
         break;
   }
 
   XCloseDisplay(d);
   return 0;
}
```the source code

[http://rosettacode.org/wiki/Window_creation/X11](http://rosettacode.org/wiki/Window_creation/X11)

ADDED : for those looking to see instant results could Try TCC compiler : this is the difference

DESCRIPTION
       TCC options are a very much like gcc options. The main difference is
       that TCC can also execute directly the resulting program and give it
       runtime arguments.

regards

alexfish

---

### Post by anewguy on 2012-04-02
And if what you want to do is write a GUI'd app, there are other tools as well.  You can look at GTK, and I know others will suggest things they are familiar with as well.  Such things as GTK can be used in Linux and Windows - I've done that before.  the display manager, such as X, becomes a layer "behind the scenes" at that point.

Dave ;)

---

