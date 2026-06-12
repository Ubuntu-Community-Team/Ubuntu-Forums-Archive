---
title: "How to get the length of a string in pixels using GTK?"
date: 2009-08-24
forum: Programming Talk
---

### Post by resander on 2009-08-24
Given the font name and size in pts of a font, how can I get 
the length of a string in pixels, or better:


```

int getpixellength ( char fontname[] , int sizeinpts , char * stringtomeasure )
   {
   // what goes in here?
   return pixellength;
   }

```

---

### Post by WitchCraft on 2009-08-24
Pixel is a relative unit.
It is relative to your screen resolution.

You can only convert it to a length in mm if you have the screen resolution.

pts is points.
1 inch = 72 points = 2.54 cm = 25.4 mm

(1 point = 127&#8260;360 mm = 352.7 µm).

and 1 pica = 12 points


Now, to convert mm's to pixels or vice versa, the information you've provided is insufficient. 
Because the metric dimension of a pixel depends on the screen and its resolution. 

For example, if you have a 17 inch monitor [17 inches being the length of the diagonal]
With your screen being a rectangle, and the diagonal is crossing at a non-45 old-degrees angle = not pi/4

Then you can calculate the length of the horizonal and vertical axis by using trigonometry.
assuming you have a 1024 * 768 resolution in pixels.
That means 1024 pixels long and 768 height.
Since the screen is most-likely a rectangle, we use Pythagoras, we get a² + b² = c²

so (1024²+ 768²)pixel² = (17*2.54cm)^2
1638400 * pixel^2 = 1864.5124 cm²
<==> 1280 pixel= 43.18 cm = 431.8 mm
        1 pixel = 0.033734375 mm
==> 1 mm = 29.6433534 pixel


**but only at a resolution of 1024 x 768 and a 17 inch screen.**


Now, you can get the screen resolution by using the Xlib:

```

#include <X11/Xlib.h>
// Compile: g++ myfile.c -o my -lX11

    Display* display;

    /* open the connection to the display "simey:0". */
    display = XOpenDisplay(0);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (-1);
    }
    int screen_height = DisplayHeight(display, DefaultScreen(display));
    int screen_width  = DisplayWidth(display, DefaultScreen(display));
    XCloseDisplay( display );

```

The better question now is how can you get the size of the diagonal programmatically, because IMHO that's not possible...

---

### Post by kknd on 2009-08-25
You can use pango, the text layout library used by GTK, to get these type of information!

[http://library.gnome.org/devel/pango/stable/](http://library.gnome.org/devel/pango/stable/)

---

### Post by Reiger on 2009-08-25
> **WitchCraft said:**
> Pixel is a relative unit.
It is relative to your screen resolution.

You can only convert it to a length in mm if you have the screen resolution.

pts is points.
1 inch = 72 points = 2.54 cm = 25.4 mm

(1 point = 127&#8260;360 mm = 352.7 µm).

and 1 pica = 12 points


Now, to convert mm's to pixels or vice versa, the information you've provided is insufficient. 
Because the metric dimension of a pixel depends on the screen and its resolution. 

For example, if you have a 17 inch monitor [17 inches being the length of the diagonal]
With your screen being a rectangle, and the diagonal is crossing at a non-45 old-degrees angle = not pi/4

Then you can calculate the length of the horizonal and vertical axis by using trigonometry.
assuming you have a 1024 * 768 resolution in pixels.
That means 1024 pixels long and 768 height.
Since the screen is most-likely a rectangle, we use Pythagoras, we get a² + b² = c²

so (1024²+ 768²)pixel² = (17*2.54cm)^2
1638400 * pixel^2 = 1864.5124 cm²
<==> 1280 pixel= 43.18 cm = 431.8 mm
        1 pixel = 0.033734375 mm
==> 1 mm = 29.6433534 pixel


**but only at a resolution of 1024 x 768 and a 17 inch screen.**


Now, you can get the screen resolution by using the Xlib:

```

#include <X11/Xlib.h>
// Compile: g++ myfile.c -o my -lX11

    Display* display;

    /* open the connection to the display "simey:0". */
    display = XOpenDisplay(0);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (-1);
    }
    int screen_height = DisplayHeight(display, DefaultScreen(display));
    int screen_width  = DisplayWidth(display, DefaultScreen(display));
    XCloseDisplay( display );

```

The better question now is how can you get the size of the diagonal programmatically, because IMHO that's not possible...

I don't think this is how it works in practice. The glyphs & the global properties of the font used for rendering the string are what determines the dimensions of the bounding box of that string on screen: glyphs are converted to bitmaps then drawn on screen.

Simply put: to a font engine a 1900x1200 screen @ 24 inch is exactly the same as a 1900x1200 screen @ 27 inch. I think this is also why there is a notion of adjusting/forcing DPI: to make up for the fact that the underlying engine itself has no information about screen sizes either.

---

### Post by resander on 2009-08-25
KKND:

Many thanks. You made me look in the right direction, so here is a Pango solution that returns width and height of a string in pixel units.

```

extern GttWidget * curdlg;  // of current dialog

void gettextwdht ( char * family , int ptsize , int weight , bool normalstyle ,
                   char * stringtomeasure ,
                   int * wdret , int * htret )
   { 
   PangoFontDescription * fd = pango_font_description_new ( );

   pango_font_description_set_family (fd, family );
   pango_font_description_set_style (fd, normalstyle ? PANGO_STYLE_NORMAL :
                                                       PANGO_STYLE_ITALIC );
   pango_font_description_set_variant (fd, PANGO_VARIANT_NORMAL);
   pango_font_description_set_weight (fd, (PangoWeight)weight );
   pango_font_description_set_stretch (fd, PANGO_STRETCH_NORMAL);
   pango_font_description_set_size (fd, ptsize * PANGO_SCALE);

   PangoContext * context = gtk_widget_get_pango_context ( curdlg ) ;
 
   PangoLayout * layout = pango_layout_new ( context );
   pango_layout_set_text ( layout, stringtomeasure, -1 );
   pango_layout_set_font_description ( layout, fd );
   pango_layout_get_pixel_size (layout, wdret , htret );
   g_object_unref ( layout );
   }

```

The last five statements kindly given by a member of the GTK mailing list.
The routine 'borrows' the GtkWidget of current dialog that is active at the
time of call in order to get a context.

I need this function to compare strings in order to align them. There is no need to have a length in absolute units. Counting relative pixels is fine.

---

### Post by WitchCraft on 2009-08-25
> **Reiger said:**
> I don't think this is how it works in practice. The glyphs & the global properties of the font used for rendering the string are what determines the dimensions of the bounding box of that string on screen: glyphs are converted to bitmaps then drawn on screen.

Simply put: to a font engine a 1900x1200 screen @ 24 inch is exactly the same as a 1900x1200 screen @ 27 inch. I think this is also why there is a notion of adjusting/forcing DPI: to make up for the fact that the underlying engine itself has no information about screen sizes either.

Just think: At some time, you must give the hardware concrete information of absolute size. Unless this is done, nothing can get displayed on the screen.

Now DPI, like pixel, - and unlike points - is a relative measurement.
And of course you want to have a relative measurement, because that way "it" automagically scales it to the "right" size for the screen size and resolution.

And pango gets the size by asking the bitmap size, screen size and resolution from either the operating system or via some Xorg API's, and then calculate the absolute bitmap size back to relavite DPIs or pixels.

This is how quake3 does it:
```

// ================
// CG_AdjustFrom640
// Adjusted for resolution and screen aspect ratio
// ================
void CG_AdjustFrom640( float *x, float *y, float *w, float *h ) {
#if 0
	// adjust for wide screens
	if ( cgs.glconfig.vidWidth * 480 > cgs.glconfig.vidHeight * 640 ) {
		*x += 0.5 * ( cgs.glconfig.vidWidth - ( cgs.glconfig.vidHeight * 640 / 480 ) );
	}
#endif
	// scale for screen sizes
	*x *= cgs.screenXScale;
	*y *= cgs.screenYScale;
	*w *= cgs.screenXScale;
	*h *= cgs.screenYScale;
}

```
Got it? Adjust measurements from 640 x 480 to screen size of any size (via GL config that is in cgs, so using the system resolution, and screen size).

Now to the original problem:
Using Pango is obviously a nice way, since Pango just does all the math for you.
But just remember that relative size adjustment does not necessarily mean that it's fault free and neither that it aesthetically looks the same at any common resolution - or that the window containing something written with a font of relative size is large enough in size for the text to fit in at a low resolution (e.g. the gnome login preferences window at 640 x 480, where you can't select values, because they are off-screen, and the window is neither scrollable nor resizable nor movable...).

---

