---
title: "Grab 10x10 to 100x100 pixel section of screen ?"
date: 2008-07-26
forum: Programming Talk
---

### Post by joebert on 2008-07-26
Please forgive me if I don't know what I'm talking about.

I'm basicly looking to duplicate the zoom/magnify functionality of [_this_](http://www.colorschemer.com/colorpix_info.php).
Where a variable sized section of the screen is magnified & clicking returns the RGB value of the pixel.

I've got a few years of experience with JS & PHP, I've managed to build Hello World with GTK & for a console, I'm getting the hang of Glade, but retrieving a section of the screen has really got me scratching my head.

I'm having a tough time determining what I'm looking for, let alone where to look.

Any pointers about retrieving that section & anything else I should know would be appreciated. :)

BTW, I'm on Ubuntu Hardy & don't have any immediate plans to make it work anywhere else at the moment if that makes a difference.

---

### Post by mbsullivan on 2008-07-26
> I've got a few years of experience with JS & PHP

... but this isn't a browser app, right? It's a stand alone application. And you're using C/C++ for this application, if I'm not mistaken?

There's probably a sexier way to do it, but the first thing I thought of was hacking [scrot]("http://freshmeat.net/projects/scrot/") to do it. Basically it'll come down to using imlib2 to grab a portion of the screen, and then putting that info into your GUI.

Mike

---

### Post by joebert on 2008-07-26
> **mbsullivan said:**
> ... but this isn't a browser app, right? It's a stand alone application. And you're using C/C++ for this application, if I'm not mistaken?

There's probably a sexier way to do it, but the first thing I thought of was hacking [scrot]("http://freshmeat.net/projects/scrot/") to do it. Basically it'll come down to using imlib2 to grab a portion of the screen, and then putting that info into your GUI.

Mike

Yes, standalone written in C (I think, I'm new to C/C++). I was aiming to give some sort of idea where I am skillset-wise with the mention of JS/PHP.

I'll take a better look at scrot/imlib2 in the morning, thanks for the suggestion. :)

---

### Post by mbsullivan on 2008-07-26
> I'll take a better look at scrot/imlib2 in the morning, thanks for the suggestion. 

If you take a look at the scrot source code, you'll probably want to focus on:

main.c - Program application
imlib.c - Initialization code
scrot.h - Necessary includes

All the rest are just for parsing options from the command line and setting up the build system.

Mike

---

### Post by joebert on 2008-08-03
Here's the header I ended up using.

```
#define GTK_DISABLE_DEPRECATED
#include <gtk/gtk.h>
```

Which makes available the Gdk functions.

At the moment this test function gives me the color of a pixel on the screen,
```
void sample_color ()
{
	int 			x, y;
	gchar			*_x, *_y;
	guint32			color;
	GdkModifierType	state;
	GdkImage		*section;

	gdk_window_get_pointer(gdk_get_default_root_window (), &x, &y, &state);
	
	if((x != last_x) || (y != last_y))
	{
		last_x = x;
		last_y = y;
	
		//gtk_image_clear (GtkImage *image);
		//gtk_image_set_from_image (GtkImage *image, GdkImage *gdk_image, GdkBitmap *mask);
		
		section = gdk_drawable_get_image (
			(GdkDrawable *)gdk_get_default_root_window (),
			(gint)x, (gint)y, 20, 15);
		
		color = gdk_image_get_pixel(section, 0, 0);

		gtk_entry_set_text((GtkEntry*)rgb,
			g_strdup_printf ("rgb(%i, %i, %i)", (color >> 16), (color >> 8 & 255), (color & 255))
		);
		gtk_entry_set_text((GtkEntry*)hex,
			g_strdup_printf ("#%.2X%.2X%.2X", (color >> 16), (color >> 8 & 255), (color & 255))
		);
	}
}
```

I plan on being able to utilize the GdkImage returned from *gdk_drawable_get_image* as the second argument to *gtk_image_set_from_image*, I just haven't investigated the third GdkBitmap argument yet.

Since I get valid colors from that test function, I think it's safe to assume "section" is a valid section of the screen.

---

### Post by joebert on 2008-08-24
After getting into the project more and needing to get rid of flickering, I ended up doing it differently.

What it boils down to, is I'm fetching an 11x11 pixel section of the root windows drawable around the mouse pointer, then looping through those pixels and drawing a 20x20 pixel rectangle to a buffer for each one, before finally applying the buffer to the image widget.

Here's the relevant code of what I'm doing.

```
root_window		= gdk_get_default_root_window ();
buffer			= gdk_pixmap_new (root_window, 220, 220, -1);
magnified		= GTK_IMAGE (gtk_builder_get_object (builder, "magnified"));

ctx				= gdk_cairo_create(buffer);

if((x != last_x) || (y != last_y))
{
	gdk_window_get_geometry (root_window, NULL, NULL, &width, &height, NULL);

	left	= max(0, x - 5);
	right	= min(width, x + 6);
	top		= max(0, y - 5);
	bottom	= min(height, y + 6);
	width	= right - left;
	height	= bottom - top;

	section = gdk_drawable_get_image (root_window, left, top, width, height);

	cairo_rectangle (ctx, 0, 0, 220, 220);
	cairo_set_source_rgb (ctx, 0.75, 0.75, 0.75);
	cairo_fill (ctx);

	for(i = 0, xx = 11 - width; i < width; i++, xx++)
	{
		for(j = 0, yy = 11 - height; j < height; j++, yy++)
		{
			color	= gdk_image_get_pixel(section, i, j);
			red		= color >> 16;
			green	= color >> 8 & 255;
			blue	= color & 255;

			cairo_rectangle			(ctx, (20 * xx), (20 * yy), 20, 20);
			cairo_set_source_rgb	(ctx, (double)red/255, (double)green/255, (double)blue/255);
			cairo_fill				(ctx);
		}
	}
	g_object_unref (section);


	/* Apply the buffered magnifier to the display widget */
	gtk_image_set_from_pixmap (magnified, buffer, NULL);
}
```

---

