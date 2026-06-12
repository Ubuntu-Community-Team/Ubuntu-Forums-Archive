---
title: "Compiling Autotrace with libpng15"
date: 2012-11-19
forum: Packaging and Compiling Programs
---

### Post by dodle on 2012-11-19
Autotrace 0.31.1 does not support libpng 1.5. Rather than downgrading to 1.4 I decided to try and fix the problems. I got a bunch of "[color=blue]dereferencing pointer to incomplete type[/color]" errors that I was able to fix except for one. The original code is thus:

input-png.c:
[php]	info_ptr->row_pointers = (png_bytepp)png_malloc(png_ptr,
							info_ptr->height * sizeof(png_bytep));[/php]

```
../input-png.c: In function 'read_png':
../input-png.c:180:10: error: dereferencing pointer to incomplete type
```

So I changed up the code like this (which worked for the other dereferencing errors, but this one is a different situation):

[php]	png_get_rows(png_ptr, info_ptr) = (png_bytepp)png_malloc(png_ptr,
							png_get_image_height(png_ptr, info_ptr) * sizeof(png_bytep));[/php]

Now the error is thus:
```
../input-png.c: In function 'read_png':
../input-png.c:180:34: error: lvalue required as left operand of assignment
```

I'm guessing it is because "[color=blue]png_get_rows()[/color]" just returns the value without placing it into a variable. But I don't know to which variable I am supposed to assign the value. Originally it was a member of [color=blue]info_ptr[/color] I guess.

Here is the function in its entirety:
[php]static png_bytep *
read_png(png_structp png_ptr, png_infop info_ptr, at_input_opts_type * opts)
{
	int row;
	png_color_16p original_bg;
	png_color_16  my_bg;

	png_read_info(png_ptr, info_ptr);

	png_set_strip_16(png_ptr);
	png_set_packing(png_ptr);
	if ((png_get_bit_depth(png_ptr, info_ptr) < 8) ||
	    (png_get_color_type(png_ptr, info_ptr) == PNG_COLOR_TYPE_PALETTE) ||
	    (png_get_valid(png_ptr, info_ptr, PNG_INFO_tRNS)))
		png_set_expand(png_ptr);

	if (png_get_bKGD(png_ptr, info_ptr, &original_bg)) {
		/* Fill transparent region with ... */
		my_bg.index = 0;

		if (opts && opts->background_color) {
			my_bg.red   = 256 * opts->background_color->r;
			my_bg.green = 256 * opts->background_color->g;
			my_bg.blue  = 256 * opts->background_color->b;
			my_bg.gray  = 256* ((opts->background_color->r
					     + opts->background_color->g
					     + opts->background_color->b) / 3);
		} else
			  /* else, use white */
			  my_bg.red = my_bg.green = my_bg.blue = my_bg.gray = 0xFFFF;
		
		png_set_background(png_ptr, &my_bg,
				   PNG_BACKGROUND_GAMMA_FILE, 1, 1.0);
	} else
		png_set_strip_alpha(png_ptr);
	png_read_update_info(png_ptr, info_ptr);


	png_get_rows(png_ptr, info_ptr) = (png_bytepp)png_malloc(png_ptr,
							png_get_image_height(png_ptr, info_ptr) * sizeof(png_bytep));
#ifdef PNG_FREE_ME_SUPPORTED
	png_free_data(png_ptr, info_ptr, PNG_FREE_ROWS, -1);
#endif
	for (row = 0; row < (int)png_get_image_height(png_ptr, info_ptr); row++)
		png_get_rows(png_ptr, info_ptr)[row] = (png_bytep)png_malloc(png_ptr,
								    png_get_rowbytes(png_ptr, info_ptr));
	
	png_read_image(png_ptr, png_get_rows(png_ptr, info_ptr));
	png_get_valid(png_ptr, info_ptr, PNG_INFO_IDAT);
	png_read_end(png_ptr, info_ptr);
	return png_get_rows(png_ptr, info_ptr);
}[/php]

I have been through the [libpng reference](http://www.libpng.org/pub/png/libpng-manual.txt) (somewhat) and png headers and haven't been able to find an answer.

**----- Edit -----**

This is from the manual:
> After you have called png_read_png(), you can retrieve the image data
with

   row_pointers = png_get_rows(png_ptr, info_ptr);

where row_pointers is an array of pointers to the pixel data for each row:

   png_bytep row_pointers[height];

Here are all the changes that I have made to this function:

[php]@@ -9,8 +9,8 @@ read_png(png_structp png_ptr, png_infop
 
 	png_set_strip_16(png_ptr);
 	png_set_packing(png_ptr);
-	if ((png_ptr->bit_depth < 8) ||
-	    (png_ptr->color_type == PNG_COLOR_TYPE_PALETTE) ||
+	if ((png_get_bit_depth(png_ptr, info_ptr) < 8) ||
+	    (png_get_color_type(png_ptr, info_ptr) == PNG_COLOR_TYPE_PALETTE) ||
 	    (png_get_valid(png_ptr, info_ptr, PNG_INFO_tRNS)))
 		png_set_expand(png_ptr);
 
@@ -36,17 +36,17 @@ read_png(png_structp png_ptr, png_infop
 	png_read_update_info(png_ptr, info_ptr);
 
 
-	info_ptr->row_pointers = (png_bytepp)png_malloc(png_ptr,
-							info_ptr->height * sizeof(png_bytep));
+	png_get_rows(png_ptr, info_ptr) = (png_bytepp)png_malloc(png_ptr,
+							png_get_image_height(png_ptr, info_ptr) * sizeof(png_bytep));
 #ifdef PNG_FREE_ME_SUPPORTED
-	info_ptr->free_me |= PNG_FREE_ROWS;
+	png_free_data(png_ptr, info_ptr, PNG_FREE_ROWS, -1);
 #endif
-	for (row = 0; row < (int)info_ptr->height; row++)
-		info_ptr->row_pointers[row] = (png_bytep)png_malloc(png_ptr,
+	for (row = 0; row < (int)png_get_image_height(png_ptr, info_ptr); row++)
+		png_get_rows(png_ptr, info_ptr)[row] = (png_bytep)png_malloc(png_ptr,
 								    png_get_rowbytes(png_ptr, info_ptr));
 	
-	png_read_image(png_ptr, info_ptr->row_pointers);
-	info_ptr->valid |= PNG_INFO_IDAT;
+	png_read_image(png_ptr, png_get_rows(png_ptr, info_ptr));
+	png_get_valid(png_ptr, info_ptr, PNG_INFO_IDAT);
 	png_read_end(png_ptr, info_ptr);
 	return png_get_rows(png_ptr, info_ptr);
 }[/php]

And for reference, no, I do not understand what is going on in this function. It looks to me like, in the part that I am struggling with, that memory is being allocated.

---

