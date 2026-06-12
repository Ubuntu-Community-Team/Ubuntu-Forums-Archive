---
title: "still having trouble with xlib"
date: 2007-08-13
forum: Programming Talk
---

### Post by Sp4cedOut on 2007-08-13
I've been working on getting a window to appear on all desktops (I'm using Compiz-Fusion).  moma was nice enough to post this code:

```
#define DESKTOP_ALL (0xffffffff)

   // unsigned int desktop =  1;  /* normally 0 - 3 */
   unsigned int desktop =  DESKTOP_ALL;

   Atom atom_net_vm_desktop = XInternAtom(g_display, "_NET_WM_DESKTOP", False);
   XChangeProperty(g_display, win, atom_net_vm_desktop, XA_CARDINAL, 32, PropModeReplace, (unsigned char *) &desktop, 1L);
```

and this:

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

I was dismayed when my application still appeared only one one desktop.  When I used the second code reference to check the number of virtual desktops, it said there was only one, not 4 like on the cube.

When experimenting with GTK+ gtk_window_stick() worked perfectly so I looked at the source code for that, it changes both _NET_WM_DESKTOP and _NET_WM_STATE, I believe it adds _NET_WM_STATE_STICKY.  I tried doing the same in my own program, but alas, to no avail.  I also tried increasing the number of desktops to four but that didn't help either.

Here's the code I added:

```

/* request desktop 0xffffffff */
    vm_desktop = XInternAtom(dpy, "_NEW_WM_DESKTOP", False);
    XChangeProperty(dpy, RootWindow(dpy, vInfo->screen), vm_desktop, XA_CARDINAL, 32, PropModeReplace,
    	(unsigned char *) &desktops, 1);
    
    /* make the window appear in all viewports */
    Atom atom_sticky = XInternAtom(dpy, "_NET_WM_STATE_STICKY", False);
    vm_desktop = XInternAtom(dpy, "_NET_WM_STATE", False);
    Atom none = XInternAtom(dpy, NULL, False);
    unsigned long data[3] = { 1,  atom_sticky,  none };
    
    XChangeProperty(dpy, RootWindow(dpy, vInfo->screen), vm_desktop, XA_ATOM, 32,
    			PropModeReplace, (unsigned char *) &data, 3);
    
    /* print the number of virtual desktops */	
    Atom actual_type;
	   int actual_format;
	   unsigned long num_items, bytes_left;
	   unsigned char *ret_data_ptr;

	   Atom atom_net_number_desktops = XInternAtom(dpy, "_NET_NUMBER_OF_DESKTOPS", False);
	    
	  //Window root_win = RootWindow(dpy, xWin);

	  if(XGetWindowProperty(dpy, RootWindow(dpy, vInfo->screen), atom_net_number_desktops, 0L, 1L  ,False, 
	                      XA_CARDINAL, &actual_type, &actual_format, &num_items, &bytes_left, &ret_data_ptr) == Success)
	  {
	     unsigned int num;
	     num = *((int*)ret_data_ptr);
	     printf("The number of desktops is: %d\n",num); 

	     XFree(ret_data_ptr);
	  }

```

and the entire code to my program (mostly from opengl.org).  If anyone could tell me what I'm doing wrong that would by great.

---

