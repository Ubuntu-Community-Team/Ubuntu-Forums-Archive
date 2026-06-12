---
title: "How to change screen resolution by a program using Ubuntu?"
date: 2010-01-28
forum: Programming Talk
---

### Post by resander on 2010-01-28
The Ubuntu Gnome GUI provides functions to change screen resolution (for example from 800x600 to 1024x768) via menus or task bars.

I would like to change the resolution from an application. Is this possible?

Current screen resolution can be obtained by:

GdkScreen * screen = gtk_window_get_screen(GTK_WINDOW(window));
int width = gdk_screen_get_width(screen);  // in pixels
int height = gdk_screen_get_height(screen);

but I have not found anything similar for setting the resolution.

Is there a 'set current screen resolution' command-line command that I can call from my app? or some other way?

---

### Post by John Bean on 2010-01-28
```
man xrandr
```

---

### Post by hessiess on 2010-01-28
Unless you have an extremely good reason for doing so, don't change the resolution. Modern LCD monitors are really only capable of displaying ONE resolution.

Non-native resolutions are supported through in-monitor scaling which creates all sorts of problems like aliasing, aspect stretching and display lag.

If you are writing some sort of resolution dependent 2D application/game, make it resolution independent by scaling to the native resolution in software/hardware(OpenGL).

---

### Post by resander on 2010-01-29
John Bean:
Many thanks for the tip!

 system ( "xrandr --output default --mode 1024x768" );

works fine.

The 'default' after --output is the default name of the device, I think. Stumbled upon it after some googling in the xrandr -q example in 

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) 

One of the first couple of lines reads:  'VGA connected...' where VGA is an output name. On my PC the xrandr line reads: 'default connected...'. There are no names like VGA in my xorg.conf file.

Hessiess:
Your point about quality and resolution is interesting. 

My app uses a GUI which I want to make resolution-dependent by allocating different amount of screen space to widgets depending on resolution. I don't want the size of the widgets to scale linearly with changes in resolution. For example, if the gui contains a list of product category names like Dairies, Vegetables & Fruit, Meats etc and a list of detailed descriptions of the products in current category then typically, I would not want the width of the category list to increase when I increase the resolution. Instead I want the extra size to be given to the product descriptions.

My idea was to let the user hop between different resolutions from inside the application just to compare the GUI layouts. However, with the system ( "xrandr ...) call above the screen goes completely black for about a second and then the new resolution pops up. I had hoped it the change-over would be a bit quicker and smoother. 

Vector graphics transforms of course would be quicker. The GTK widgets may well be drawn by vector-graphics software, but I don't know how to use transforms to zoom these. Learning from looking at the source code would take too long, so I have to use the widgets the way they are offered.

I found references to the xrandr library with header file #include <X11/extensions/Xrandr.h>. I would like to try it to see if it is quicker than the system() call. 
Does anyone know how to use this library to change the screen resolution?

---

### Post by resander on 2010-02-04
It is possible to change the screen resolution using XLib
extension XRandR directly, but the screen is still going black. 
It is not visibly faster than a system call to pass
parameters to the shell.

```

#include <X11/Xlib.h>
#include <X11/extensions/Xrandr.h>
.....
static bool changescreenres ( const char * displayname , 
                              int newwidth ,
                              int newheight )
   {
   Rotation rotation = 1 ;
   int reflection = 0;
   Display * dpy = XOpenDisplay ( displayname ) ;
   if ( dpy == NULL )
      {
      printf ( "Cannot open display %s\n", displayname ) ;
      return false ;
      }
   int screen = DefaultScreen ( dpy ) ;
   Window root = RootWindow ( dpy, screen ) ;

   XSelectInput (dpy, root, StructureNotifyMask);
   XRRSelectInput (dpy, root, RRScreenChangeNotifyMask);
   int eventbase ;
   int errorbase ;
   XRRQueryExtension ( dpy, &eventbase, &errorbase ) ;

   XRRScreenConfiguration * sc = XRRGetScreenInfo (dpy, root);
   if ( sc == NULL )
      {
      printf ( "Cannot get screen info\n" ) ;
      return false ;
      }
   int nsize ;
   XRRScreenSize * sizes = XRRConfigSizes(sc, &nsize);
   int sizeindex = 0 ;
   while ( sizeindex < nsize )
      {
      if (sizes[sizeindex].width == newwidth &&
          sizes[sizeindex].height == newheight)
        break;
      sizeindex++ ;
      }
   if ( sizeindex >= nsize )
      {
      printf ( "%dx%d resolution not available\n" , newwidth , newheight ) ;
      return false ;
      }

   Status status = XRRSetScreenConfig ( dpy, sc,
                                        DefaultRootWindow (dpy),
                                        (SizeID) sizeindex,
                                        (Rotation) (rotation | reflection),
                                        CurrentTime);
   XEvent event;
   bool rcvdrrnotify = false ;
   bool rcvdconfignotify = false ;
   if ( status == RRSetConfigSuccess)
      {
      while (1)  // event loop
         {
         XNextEvent(dpy, (XEvent *) &event);
         printf ("Event received, type = %d\n", event.type);
         XRRUpdateConfiguration ( &event ) ;
         switch (event.type - eventbase)
            {
            case RRScreenChangeNotify:
               rcvdrrnotify = true ;
               break ;
           default:
              if (event.type == ConfigureNotify)
                 {
                 printf("Rcvd ConfigureNotify Event!\n");
                 rcvdconfignotify = true ;
                 }
              else
                 {
                 printf("unknown event = %d!\n", event.type);
                 }
               break ;
            }
         if ( rcvdrrnotify && rcvdrrnotify )
            {
            break ;  // finished
            }
         }
      }
   return true ;
   }

```

The code above is based on an early version of code for the
commandline command xrand plus various documents about
Xlib (there are plenty).

---

### Post by hessiess on 2010-02-04
Writing resolution dependent applications in this day and age, where there are a huge number of different monitor resolutions deployed `in the wind' is an **extremely** bad idea. Also how would you handle aspect ratio differences (4:3/16:9 etc), the common monitor behaviour is just to stretch the image, yuck!

What you are describing is NOT resolution dependence, but resolution independence. If you want something to remain the same size on screen regardless of the resolution it has to be drawn independent of the pixel grid. monitors are not limited to 72DPI any more.

You should consider developing the whole interface using OpenGL, like Blender for example. This really is the only way to make something always take up the same amount of screen space regardless of resolution.

---

### Post by resander on 2010-02-04
The applicaton is 100% resoution-dependent by design because I want the screen to be used differently depending on the resolution. The motivating force is to let the user see as much data as possible at any resolution without wasting space. I do not start from one representation that is transformed mathematically for use by other resolutions. The resolutions are independent and handled one by one. Each case can be handled by writing special code, by using available resource editors or by specially tailored text descriptions that are parsed. I choose the latter because it is a lot less work. The amount of space to be allocated to widgets depends on the amount of data and the min-max dimensions of data destined for each widget. It also depends on taste, style and balance so design has to progress little by little by trial and error.     
 
The application itself does not draw anything, so drawing packages would be of no use. It just passes data to predefined GTK widgets (could be qt,wx xaw, mosaic too) which are rendered by the toolkit and lower level functions in xlib/xrender.
Small amounts of data fit into a smaller widgets and larger amounts into larger. When increasing the total amount of space available, there comes a point when there is no merit in allocating any more space to a widget holding small amounts of data as this would result in unused empty space in the widget.

Going back to the food example with categories and descriptions data, then for example categories  

'Dairies, Vegetables & Fruit, Meats' fit comfortably into a left-aligned listbox at 800x600 resolution like:

 Dairies
 Vegetables & Fruit
 Meats

but some food descriptions do not fit into another listbox to the right of the category list when listing the foods of current category. For example, for the Meats the description for mince might read: 'Lean Steak Mince 500G. Typically less than 12% fat. From lean cuts low in saturated fat'. Then only a part of the description fits for example 'Lean Steak Mince 500G Typically le' (the listbox shows only one line per descriptor). When increasing the resolution to 1024x768  there would be no point in keeping the proportions the same for the the two listboxes. The descriptions listbox should be allocated more horizontal space so it can show more, the category listbox already has enough. 

Allocating widget space depending on resolution in this way is easy to implement. For each resolution to be supported define (in text form) the proportions (in percentages) for the changeable widgets after space has been allocated to the non-changing widgets and add salt and pepper to taste. However, getting the percentages and overall balance right needs experimentation and visual feedback, so it is useful to be able to change screen resolution from inside the program.

---

