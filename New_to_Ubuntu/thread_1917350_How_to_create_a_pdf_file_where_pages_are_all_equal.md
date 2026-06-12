---
title: "How to create a pdf file where pages are all equal size"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by mcbob628 on 2012-01-29
Hi,

I am trying to create a pdf file from about 20 jpg files. The jpg pics are comics. So once I convert the 20 jpg in the pdf, it will be a single pdf file. I use the following command:
convert *.jpg output.pdf
it create the output file in pdf format.

But the problem is that some pages are smaller than others. i.e. you have to zoom in and out every few pages. it gets annoying. The first page is perfect size, I am able to read the text, pictures are clear, etc. but page 7 is smaller (as well as some other pages). page 7 is seen with smaller borders than other pages in the pdf file even though it is basically the same size in pixels (dimensions).

After looking closely at the jpg files associated with the pdf pages that are smaller, I discovered that the jpg files associated with smaller pages were smaller in size i.e. 500 kB. Most of the others are above 1 megabyte, but some are around 500 kb.

So I guess to sum up, How do I create a pdf file out of multiple jpg files (with different file size: kb, mb, etc.), where the pdf pages all have the same dimensions.

Thank You, 
Thank You Very Much
For your contributions

---

### Post by dixonstalbert on 2012-01-29
Hello

Sorry I don't have an exact answer, but this might get you going while you wait for a better one:


convert uses imagemagick.

I found this webpage:

[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)

that has examples of resizing multiple images

Hope this helps

---

### Post by mcbob628 on 2012-03-11
Before closing thread I figure I should mention a solution I came upon from some other site, here goes:

NOTE:: This will only work if all the pages are equal size in dimensions, (not necessarily equal in byte-size)

You can open all images as layers in GIMP. After this you can save the entire file as an MNG Animation (make sure to save it as an animation, do not flatten image). Save the file as "filename.mng".

Use the convert command to convert "filename.mng" into "file2.pdf"

use command: 
convert filename.mng file2.pdf

TA DAA~

NOTE:: This will only work if all the pages are equal size in dimensions, (not necessarily equal in byte-size)

---

