---
title: "[SOLVED] doc &amp;amp; oo to image converter program?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by anewguy on 2008-10-02
Does anyone know if there is a Linux/Ubuntu program that will convert .doc and OpenOffice.org documents to an image (png, jpg, etc.)?

I need something like this so I can take the monthly sales flier (images and text) and post it to our web site.

Thanks in advance! 

Dave :)

---

### Post by M4rotku on 2008-10-02
I would imagine there is some way you can do it with gimp.

Open the file with gimp and trying saving it with a different file type.

you could also try printing the file to a PDF.

---

### Post by M4rotku on 2008-10-02
Never mind, gimp does not work.

However, if you print it as a PDF, gimp will be able to convert a PDF to an image such as a jpg.

I just tested it, works fine.

---

### Post by anewguy on 2008-10-02
I was only able to get that to work for a single page - the sales flyer is multiple pages.

Thanks for the help!  If you can find a way to do it for multiple pages all at once to a single image file it would be great!

Dave :)

---

### Post by anewguy on 2008-10-03
I'll tell you what I did - it isn't pretty, it takes a while, but it is free.

I saved each page from openoffice as a pdf file.

Then I used Inkscape to read in each pdf and export each as a .png file.

Edited the html to have an <img> statement for each of the .pngs.

Not what I want to do, but it worked for now.  I'd like to save the entire multi-page document in openoffice as a single pdf and make it a single image so the html can just include a single <img> file.  That way I don't have to change the html each time the on sale item lists change - just copy the image file up to the server.

Dave :)

---

