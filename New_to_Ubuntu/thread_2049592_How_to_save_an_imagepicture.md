---
title: "How to save an image/picture"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by czgirb on 2012-08-28
How can I save a picture, which shown in **PDF's file** to **JPG** ?
(I tried to select  a picture > right-click > copy image ... and then what should I  do?)
*** In windows, I copied the picture and paste it in **Paint** and it's done.
[B]
PS:[/B]
I tried to paste it in **GIMP** ... but it pasted another picture, which I don't know where the picture comes from

Please guide me  ....
**Thank you**

---

### Post by Futant on 2012-08-28
Try [https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/](https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/)

---

### Post by meilin on 2012-08-28
There are quiet a few ways to convert pdf to jpg.

Online ways using web browser to visit:

[http://convert.neevia.com/pdfconvert/]("http://convert.neevia.com/pdfconvert/")
or
[http://www.zamzar.com/]("http://www.zamzar.com/")
or 
[http://www.youconvertit.com/ConvertFiles.aspx]("http://www.youconvertit.com/ConvertFiles.aspx")

They are free, and easy to use! 

If you would like a Linux tool, search and install **PDF utilities** in Ubuntu Software Center. This is a command line tool, using following command as example:

_pdfimages -j filename.pdf filename.jpg_


With this command, images in DCT format are saved as JPEG files. All  non-DCT images are saved in PBM/PPM format as usual.

---

### Post by czgirb on 2012-08-28
> **Futant said:**
> Try [https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/](https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/)

> **meilin said:**
> There are quiet a few ways to convert pdf to jpg.
Online ways using web browser to visit:
[http://convert.neevia.com/pdfconvert/](http://convert.neevia.com/pdfconvert/)
or
[http://www.zamzar.com/](http://www.zamzar.com/)
or 
[http://www.youconvertit.com/ConvertFiles.aspx](http://www.youconvertit.com/ConvertFiles.aspx)
They are free, and easy to use! 
If you would like a Linux tool, search and install **PDF utilities** in Ubuntu Software Center. This is a command line tool, using following command as example:
_pdfimages -j filename.pdf filename.jpg_
With this command, images in DCT format are saved as JPEG files. All  non-DCT images are saved in PBM/PPM format as usual.

No! No! No! Maybe what I said is not clear enough ... SORRY!
Once again ... I really SORRY for that.
All I wanna do is just to **COPY** an image/picture, which I saw from **PDF**'s file.
I do not wish to **EXTRACT** or **CONVERT** a **PDF** file into **JPG**.

**PS:**
So, I can **DELETE THE PDF** and keep **ONE IMAGE/PICTURE** only.

---

### Post by bootedguy on 2012-08-28
Use the Poppler utils which are included with Ubuntu. These are command line, and you can Google for the syntax. You can do all sorts of weird and wonderful things with PDFs.

---

### Post by jerome1232 on 2012-08-28
> **Futant said:**
> Try [https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/](https://ubuntugenius.wordpress.com/2012/02/04/how-to-extract-images-from-pdf-documents-in-ubuntulinux/)

This is what you want, it tells you how to extract the image from the pdf file. It's the same thing as "saving the image from the pdf file"

---

### Post by czgirb on 2012-08-29
[SIZE=4]**SORRY ...**[/SIZE]
All of you is not wrong.
It's my knowledge to the word **EXTRACT** is not enough.
**[SIZE=4]SORRY !!!!!!![/SIZE]**

If I just wants to copy just **ONE** image/picture, is it necessary to do that ?

---

### Post by NikTh on 2012-08-29
> **czgirb said:**
> How can I save a picture, which shown in **PDF's file** to **JPG** ?
(I tried to select  a picture > right-click > copy image ... and then what should I  do?)
*** In windows, I copied the picture and paste it in **Paint** and it's done.
[B]
PS:[/B]
I tried to paste it in **GIMP** ... but it pasted another picture, which I don't know where the picture comes from

Please guide me  ....
**Thank you**

Hi, 
something you've done wrong. It is simple procedure. Right click on image and save as.. now pay attention. You must give a name and at bottom right you will see the formats. From default has "by extension" click this to open the drop-down menu and change it to JPEG and do not forget at the end of the name  to add the extension .jpg 
If the name is mypicture , then you must save the picture as mypicture.jpg 
Thats it. 
The difference with windows here , is that Ubuntu not hide the extensions of the files.  
Thank you.

---

### Post by czgirb on 2012-12-01
Thank you.
In my computer, I unable to do that with Adobe Reader, but I able to do that with Okular.
Thank you

---

