---
title: "Making GTK windows transparent"
date: 2007-08-08
forum: Programming Talk
---

### Post by Sp4cedOut on 2007-08-08
I want to make part of my GTK windows transparent, so I can see the desktop behind it, and I was wondering how I would do that.  I'm using Compiz-Fusion, but I'd like it to support various compositing window managers if possible.

Thanks in advance.

---

### Post by moma on 2007-08-08
I hope this helps.

I do not use GTK or any other toolkits but I know that the Xlib (the basic X window library) let you create [COLOR="Purple"]**transparent**[/COLOR] and [COLOR="Purple"]**shaped**[/COLOR] windows quite easily.

XShapeCombineMask(..) function is essential part of making a window transparent or shaped.

Take a look at the attached code. I copied it originally from 
[http://lists.freedesktop.org/pipermail/xorg/2005-October/010877.html](http://lists.freedesktop.org/pipermail/xorg/2005-October/010877.html)

Compile it:
$ [COLOR="SeaGreen"]gcc -Wall -g -lX11 -lXext xshape1.c -o xshape1[/COLOR]
Run it:
$ [COLOR="SeaGreen"]./xshape1[/COLOR]

libXext library is part of the Ubuntu's "libxext-dev" package.

And of course,  google for "[COLOR="blue"]GTK and XShapeCombineMask[/COLOR]".

Attachment: xshape1.c.txt

---

### Post by moma on 2007-08-09
Ehm, 
you can of course set the transparency / opacity by setting the _NET_WM_WINDOW_OPACITY atom on the Window Manager.

See the enclosed (new) sample code xtest1.c.
Uncomment the lines below " [COLOR="Plum"]// Window transparency/opacity test[/COLOR]".
Set the transparency variable  to a value between 0.0 - 1.0.  Eg.
double transparency = 0.600;   

Compile it.
$  [COLOR="SeaGreen"]gcc -lX11 -lXext xtest1.c -o xtest1[/COLOR]

Comment out the lines below "[COLOR="Plum"]// Window at the background test[/COLOR]" so the window stays at the top of the desktop.

_NET_WM_WINDOW_OPACITY works only if you have activated compositing or run a [compositing window manager...]("http://en.wikipedia.org/wiki/Compositing_window_manager") such as Beryl or Compiz-fusion -- as you mensioned.

---

### Post by Sp4cedOut on 2007-08-09
Thanks a lot for your help, that code is a godsend.

I was wondering if you also might know how to make a window sticky (appear on all workspaces).  I know GTK has gtk_window_stick() but I want to know how to do it in Xlib.  Many google searches turned up little.

---

### Post by moma on 2007-08-09
Try this code snippet:

// Put window on all desktops or on a spesific desktop number.

```
#define DESKTOP_ALL (0xffffffff)

   // unsigned int desktop =  1;  /* normally 0 - 3 */
   unsigned int desktop =  DESKTOP_ALL;

   Atom atom_net_vm_desktop = XInternAtom(g_display, "_NET_WM_DESKTOP", False);
   XChangeProperty(g_display, win, atom_net_vm_desktop, XA_CARDINAL, 32, PropModeReplace, (unsigned char *) &desktop, 1L);
```


This code snippet will tell you the total number of virtual desktops, normally 1 to 4.

```
   Atom actual_type;
   int actual_format;
   unsigned long num_items, bytes_left;
   unsigned char *ret_data_ptr;

   Atom atom_net_number_desktops = XInternAtom(g_display, "_NET_NUMBER_OF_DESKTOPS", False);
    
  Window root_win = RootWindow(g_display, g_screen);

  if(XGetWindowProperty(g_display, root_win, atom_net_number_desktops, 0, 1/*= one 32 bits item */ ,False, 
                      XA_CARDINAL, &actual_type, &actual_format, &num_items, &bytes_left, &ret_data_ptr) == Success)
  {
     unsigned int num;
     num = *((int*)ret_data_ptr);
     printf("The number of desktops is: %d\n",num); 

     XFree(ret_data_ptr);
  }

```

As you see, the XGetWindowProperty(...) and XChangeProperty(...) take quite a few parameters, So it's normally feasible to create a general functions that returns or sets a 32 bits (or any other size)  atom values.  Due to lack of advanced XLib examples I have started to read the code of various Window Managers. See: [http://xwinman.org/](http://xwinman.org/)

Openbox, Aewm and Larswm window managers are rather "simple and easy" to understand.
Just download the code and learn...

Good luck with your o projecto.

---

### Post by Sp4cedOut on 2007-08-10
Thanks so much.

I was thinking of looking through the code for GTK+.

---

### Post by sevenstar on 2008-10-15
Hi,

I have window and image on it. I just want to view the image not window.
In short i want to make window transparent. Can any on help...
Thanks in advance.

---

