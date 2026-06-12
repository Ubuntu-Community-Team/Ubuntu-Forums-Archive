---
title: "freading a bitmap (c)"
date: 2010-12-21
forum: Programming Talk
---

### Post by sdlynx on 2010-12-21
So I have been working with importing bitmaps into a c/++ program and storing the data as "width," "height," and "color data."  After working with the BMP files now for a while, I realized something peculiar.

At first, I was testing with bitmaps around 10x10 and noticed that after the 54 byte header, the bitmaps followed the pattern of 3 bytes per pixel per row.  However, at the end of each row, 2 blank bytes were thrown in.  I thought this odd but incorporated it into my code and it imported the files correctly.  

Then I tried a larger file (256x256), and noticed that my code completely failed to parse the image in a way that almost offset some of the pixels.  After some testing I found that there weren't 2 blank bytes after each row in the file.  So I revised my code to the original state, but then the 10x10s didn't import correctly.  After different filesize testing, I came to the explanation that BMPs under 16x16 have this 2 byte padding between rows.

Anyone have a similar experience?

Edit: On second look, it doesn't have to do with the bitmap's size exactly, it seems like it depends on whether the file is a 2^n x 2^n or some other resolution...

Edit2: Turns out there must be padding to make the number of the bytes in each row of a bitmap a multiple of 4.  Now I know.

---

### Post by sdlynx on 2010-12-21
This was a double post, oops.

---

### Post by worksofcraft on 2010-12-22
> **sdlynx said:**
> So I have been working with importing bitmaps into a c/++ program and storing the data as "width," "height," and "color data."  After working with the BMP files now for a while, I realized something peculiar.

At first, I was testing with bitmaps around 10x10 and noticed that after the 54 byte header, the bitmaps followed the pattern of 3 bytes per pixel per row.  However, at the end of each row, 2 blank bytes were thrown in.  I thought this odd but incorporated it into my code and it imported the files correctly.  

Then I tried a larger file (256x256), and noticed that my code completely failed to parse the image in a way that almost offset some of the pixels.  After some testing I found that there weren't 2 blank bytes after each row in the file.  So I revised my code to the original state, but then the 10x10s didn't import correctly.  After different filesize testing, I came to the explanation that BMPs under 16x16 have this 2 byte padding between rows.

Anyone have a similar experience?

Edit: On second look, it doesn't have to do with the bitmap's size exactly, it seems like it depends on whether the file is a 2^n x 2^n or some other resolution...

Edit2: Turns out there must be padding to make the number of the bytes in each row of a bitmap a multiple of 4.  Now I know.

Yes, this is exactly right.
It depends on your processor architecture: A 32 bit machine adresses words of 4 bytes at a time which is evidently 4 times faster than fetching them one byte at a time... so to make things easier at the end of each line they just pad it out to the next 4 byte boundary. That way it is easier to find the start of each line instead of having to try and unpack bytes from the previous line... You might have to check what happens on a 64 bit machine :shock:

---

