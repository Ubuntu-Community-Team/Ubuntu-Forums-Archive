---
title: "Help with libpng's png_write_image function"
date: 2006-11-24
forum: Programming Talk
---

### Post by duff on 2006-11-24
I'm trying to get familiar with libpng, so I'm trying to write a simple program that can create a valid copy of a png file... so I only need to copy whats necessary; IHDR, PLTE, IDAT, and IEND.

I'm attaching my test program, that takes two arguments: source file and destination; but it segfaults on the call to png_write_image ().  I've also tried using png_write_rows, but that gave me the same thing: ```
#0  0x00002b3f1a91facc in memcpy () from /lib/libc.so.6
#1  0x00002b3f1a797c18 in png_write_row () from /usr/lib/libpng12.so.0
#2  0x00002b3f1a797ea7 in png_write_image () from /usr/lib/libpng12.so.0
#3  0x0000000000401159 in write_png_file (filename=0x7fff90440c93 "foo.png", 
    width=128, height=96, bit_depth=8, color_type=2, interlace_method=0, 
    compression_method=0, filter_method=0, palette=0x0, num_palette=444087328, 
    row_pointers=0x507170) at png-test.c:98
#4  0x0000000000400ddf in main (argc=3, argv=0x7fff9043ee88) at png-test.c:27
```

The file is compliable with ```
# gcc -Wall -g png-test.c `pkg-config --cflags --libs libpng` -o png-test
```

Any ideas?  I've been staring at this for hours and comparing it with code I've found with google and can't seem to get past it :(  Am I reading the rows in incorrectly?

**EDIT**: Attaching didn't work, so here's the ol' copy'n'paste:

```
#include <stdlib.h>
#include <assert.h>
#include <png.h>

void read_png_file (char *, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp *row_pointers);

void write_png_file (char *, png_uint_32 width, png_uint_32 height, int bit_depth, int color_type, int interlace_method, int compression_method, int filter_method, png_colorp palette, int num_palette, png_bytepp row_pointers);

int main (int argc, char *argv[])
{
   png_uint_32 width;
   png_uint_32 height;
   int bit_depth;
   int color_type;
   int interlace_method;
   int compression_method;
   int filter_method;
   png_colorp palette;
   int num_palette;
   png_bytepp row_pointers;

   read_png_file (argv[1], &width, &height, &bit_depth, &color_type, &interlace_method, &compression_method, &filter_method, &palette, &num_palette, &row_pointers);

   printf ("size: %d x %d\n", (int) width, (int) height);

   write_png_file (argv[2], width, height, bit_depth, color_type, interlace_method, compression_method, filter_method, palette, num_palette, row_pointers);

   return 0;
}

void read_png_file (char *filename, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp *row_pointers)
{
   FILE         *fp;
   png_structp   png_ptr;
   png_infop     info_ptr;

   printf ("opening %s\n", filename);
   fp = fopen (filename, "r");
   assert (fp);

   png_ptr = png_create_read_struct (PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
   assert (png_ptr);

   info_ptr = png_create_info_struct (png_ptr);
   assert (info_ptr);

   png_init_io (png_ptr, fp);

   png_read_info (png_ptr, info_ptr);

   assert (1 == png_get_IHDR (png_ptr, info_ptr, width, height, bit_depth, color_type, interlace_method, compression_method, filter_method));

   png_get_PLTE (png_ptr, info_ptr, palette, num_palette);

   *row_pointers = (png_bytepp) malloc (*height * sizeof (png_bytep));
   assert (*row_pointers);
   png_read_image (png_ptr, *row_pointers);

   png_read_end (png_ptr, NULL);

   png_destroy_read_struct (&png_ptr, &info_ptr, NULL);

   fclose (fp);
}

void write_png_file (char *filename, png_uint_32 width, png_uint_32 height, int bit_depth, int color_type, int interlace_method, int compression_method, int filter_method, png_colorp palette, int num_palette, png_bytepp row_pointers)
{
   FILE         *fp;
   png_structp   png_ptr;
   png_infop     info_ptr;

   printf ("writing %s\n", filename);
   fp = fopen (filename, "w");
   assert (fp);

   png_ptr = png_create_write_struct (PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
   assert (png_ptr);

   info_ptr = png_create_info_struct (png_ptr);
   assert (info_ptr);

   if (setjmp (png_jmpbuf (png_ptr)))
   {
      fprintf (stderr, "erro?\n");
      return;
   }

   png_init_io (png_ptr, fp);

   png_set_IHDR (png_ptr, info_ptr, width, height, bit_depth, color_type, interlace_method, compression_method, filter_method);

   png_write_info (png_ptr, info_ptr);

   if (palette && num_palette > 0)
      png_set_PLTE (png_ptr, info_ptr, palette, num_palette);

   png_write_image (png_ptr, row_pointers);

   png_write_end (png_ptr, info_ptr);

   fclose (fp);
}
```

---

### Post by llonesmiz on 2006-11-25
> I'm trying to write a simple program that can create a valid copy of a png file... so I only need to copy whats necessary; IHDR, PLTE, IDAT, and IEND.
If that means that the output file isn't a perfect copy of the input file (it just has the same dimensions and palette) then I got the program working by changing:

```
--- png-test.c  2006-11-25 09:29:19.000000000 +0100
+++ png-test-modified.c 2006-11-25 09:30:32.000000000 +0100
@@ -2,7 +2,7 @@
 #include <assert.h>
 #include <png.h>
 
-void read_png_file (char *, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp *row_pointers);
+void read_png_file (char *, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp row_pointers);
 
 void write_png_file (char *, png_uint_32 width, png_uint_32 height, int bit_depth, int color_type, int interlace_method, int compression_method, int filter_method, png_colorp palette, int num_palette, png_bytepp row_pointers);
 
@@ -19,7 +19,7 @@
    int num_palette;
    png_bytepp row_pointers;
 
-   read_png_file (argv[1], &width, &height, &bit_depth, &color_type, &interlace_method, &compression_method, &filter_method, &palette, &num_palette, &row_pointers);
+   read_png_file (argv[1], &width, &height, &bit_depth, &color_type, &interlace_method, &compression_method, &filter_method, &palette, &num_palette, row_pointers);
 
    printf ("size: %d x %d\n", (int) width, (int) height);
 
@@ -28,7 +28,7 @@
    return 0;
 }
 
-void read_png_file (char *filename, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp *row_pointers)
+void read_png_file (char *filename, png_uint_32 *width, png_uint_32 *height, int *bit_depth, int *color_type, int *interlace_method, int *compression_method, int *filter_method, png_colorp *palette, int *num_palette, png_bytepp row_pointers)
 {
    FILE         *fp;
    png_structp   png_ptr;
@@ -52,9 +52,9 @@
 
    png_get_PLTE (png_ptr, info_ptr, palette, num_palette);
 
-   *row_pointers = (png_bytepp) malloc (*height * sizeof (png_bytep));
-   assert (*row_pointers);
-   png_read_image (png_ptr, *row_pointers);
+   row_pointers = (png_bytepp) malloc (*height * sizeof (png_bytep));
+   assert (row_pointers);
+   png_read_image (png_ptr, row_pointers);
 
    png_read_end (png_ptr, NULL);

```

bytepp is the same as byte** so you don't need to pass "row_pointers" with & in the read function.

If I misunderstood due to my bad English I'm sorry for the waste of time and space.

---

### Post by duff on 2006-11-25
Thanks for the suggestion, but that still didn't work for me.  It turns out I wasn't allocating room for the rows ... just pointers to the rows:  ```
   *row_pointers = (png_bytepp) malloc (*height * sizeof (png_bytep));
   assert (*row_pointers);
   for (h = 0; h < *height; h++) {
      (*row_pointers)[h] = (png_bytep) malloc (*width * sizeof (png_byte));
   }
   png_read_image (png_ptr, *row_pointers);

```

---

