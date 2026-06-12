---
title: "Changing the cursor color"
date: 2009-09-01
forum: Programming Talk
---

### Post by Marco A on 2009-09-01
.

---

### Post by Marco A on 2009-09-01
.

---

### Post by Arndt on 2009-09-02
> **Marco A said:**
> I'm posting a complete short and simple program example using only Xlib.

The following code compiles.

It will open a window and keep it open 5 seconds. I'm trying to get the window to have a white and blue/violet cursor.

The color names in the program are defaults from the sample color database, but I even tried specifying the colors as pixel colors.

I still see the same white cursor I had, on my system and it doesn't work.
 
name it;

example1.c

to compile use;

gcc  -lX11 -o example1 example1.c


Thanks for any help.:-&

```



// example1.c
//
#include <X11/Xlib.h>
#include <X11/cursorfont.h>

//to compile use
//gcc  -lX11 -o example1 example1.c


main()
{


  // Open the display.
  Display *d = XOpenDisplay(0);


  if ( d )
    {
      // Create the window
      Window w = XCreateWindow(d, DefaultRootWindow(d), 0, 0, 200,
			       100, 0, CopyFromParent, CopyFromParent,
			       CopyFromParent, 0, 0);


//create a cursor with the standard cursor font
Cursor cursor = XCreateFontCursor(d, XC_arrow);
XDefineCursor(d,w,cursor);

XColor snow_def, bviolet_def;

Colormap colormap = DefaultColormap(d,DefaultScreen (d));

//get the colors RGB for a white and blue/violet cursor
XParseColor(d,colormap,"snow",&snow_def);
XParseColor(d,colormap,"BlueViolet",&bviolet_def);

//change the cursor color
XRecolorCursor(d,cursor,&snow_def,&bviolet_def);


      // Show the window
      XMapWindow(d, w);
      XFlush(d);

     
//Sleep 5 seconds before closing.
sleep(5);

    }

}




```

I tried it and didn't learn much more, except that for some cursors (e.g., XC_star), your colours do appear, while for others (e.g., XC_cross), they don't.

---

### Post by WitchCraft on 2009-09-02
Very funny ;-)

---

### Post by Marco A on 2009-09-02
.

---

### Post by jalyst on 2009-09-05
is there no straight forward way to change cursor colour from yellow to something else?

I finding it very hard to locate it, particularly via NX client on OSX, & when using the terminal. 

If it was black it would be much easier...

cheers

---

### Post by jalyst on 2009-09-05
forget it..

its mainly just an issue with the terminal, the yellow colour of the cursor's not too bad for most other things.

so I adjusted the background and text colours of the terminal to black & green respectively....

---

