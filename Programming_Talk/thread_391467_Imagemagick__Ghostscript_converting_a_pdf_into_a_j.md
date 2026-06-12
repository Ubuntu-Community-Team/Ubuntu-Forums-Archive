---
title: "Imagemagick / Ghostscript: converting a pdf into a jpg"
date: 2007-03-23
forum: Programming Talk
---

### Post by Jonne on 2007-03-23
Hi,
I'm trying to write a shellscript that converts pdf-s into jpg's, but the jpg's i get as a result are pixelated. Is there a way to make sure I get jpg's with a decent quality? The source pdf's are A3-sized, and the jpg's I get are about 1035x1474, while I need them to be almost double that size to make sure the text is readable.

this is the command I use:
```
convert 1.pdf -profile EuroscaleUncoated.icc -profile /usr/share/color/icc/sRGB.icm 1.jpg
```

these are the versions I'm using:
Imagemagick 6.2.4
Ghostscript 8.15.4
the OS is Ubuntu Feisty

Is there a way to improve quality with a switch or something?

---

### Post by WW on 2007-04-05
When converting to jpg, you can use the **-quality** option.  The "best" quality would be **-quality 100**.

---

### Post by Jonne on 2007-04-06
-Quality changes the quality of the jpg compression, after rasterizing. The problem is that I want jpegs of a bigger resolution, and ghostscript/imagemagick won't allow me (even with -density and other options i tried)

---

### Post by lazka on 2007-04-06
try "-density 200x200"

edit: ok i didnt read you last post.. density is working fine here, tough.

---

### Post by Jonne on 2007-04-06
Thanks for trying anyway ;) This thread has had no comments for weeks, and I still haven't found an adequate solution.  Anyway, i've tried again, and it still desn't work. I think there's something wrong with how imagemagick interfaces with Ghostscript.

If I import the pdf in the gimp (I believe the gimp also uses gs internally for pdf conversion), I can set the resolution to whatever I want, and it works. The colours are all wrong, though, because I can't use a colour profile to convert the colours as they should.

I want to do it through the command line, because it will be part of a script that converts a bunch of pdf's into jpg's automatically.

i want to replace an existing program that runs only on Windows, and uses Photoshop for the conversion, because I don't want to: 
1, depend on Photoshop & Windows
2, have photoshop take all the resources and screen estate while it's running


edit: I tried with Krita, and Krita gets both the colours right, and the resolution. Is there a way I could use Krita for this, without having it spawn its gui?

---

### Post by duff on 2007-04-06
> **Jonne said:**
> Thanks for trying anyway ;) This thread has had no comments for weeks, and I still haven't found an adequate solution.  Anyway, i've tried again, and it still desn't work. I think there's something wrong with how imagemagick interfaces with Ghostscript.

Have you tried their mailing list?
[http://www.imagemagick.org/mailman/listinfo/magick-users](http://www.imagemagick.org/mailman/listinfo/magick-users)

---

### Post by WW on 2007-04-06
You can change the size of the output file with the **-geometry** option, e.g. **-geometry 1600x1600** will ensure that the largest dimension is 1600 pixels (it will preserve the aspect ratio).  I don't know if this will get you what you want, but it's worth a try.  I tried it with a PDF file that contains just some text and equations, and it looked OK, but not great.

EDIT...
If I combine -geometry, -density, and -quality, it looks better.  For example,
```

$ convert -geometry 1600x1600 -density 200x200 -quality 100 file.pdf file.jpg

```
Then file.jpg looks pretty good to me.

---

### Post by Jonne on 2007-04-06
I think I found it, thanks to WW. Apparently it depends on the syntax you use. If you add the switches before giving the filename of the pdf, it will not ignore -density and such. If you give the filename first (like in the example I posted), Imagemagick will first rasterize the pdf, and only apply the switches afterward, thus giving degraded quality. to recap:
bad:
convert file.pdf -density 200x200 file.jpg

good:
convert -density 200x200 file.pdf file.jpg

thanks guys :)

---

### Post by itaylor on 2008-03-06
Wow, I just wasted 45 minutes trying to convert a PDF to JPG using every imagemagick option I could find. The default resolution looked horrible. I finally found this post and the problem is solved. Thanks! I'm sure the information is there on the imagemagick website somewhere, but it sure isn't obvious.

---

### Post by ridgeland on 2008-03-14
Thanks WW
I used your command line.
Worked fine for me.  I converted a one page pdf to a jpg.
I googled "Ubuntu pdf to jpg" and found this quick solution.

When I opened this jpg in the GIMP I saw that the GIMP can import pdf and then save as a jpg.  Both ways worked.  CLI or GUI.

---

### Post by danbar on 2008-04-11
Yes the operation was successful for me too.  I used the gimp.  But now that I tried changing more than one page document I saw that only the first page was changed into a jpg file.  Is there a solution for longer documents ?

---

### Post by Jonne on 2008-04-11
you could use pdftk to split them first.

---

### Post by danbar on 2008-04-11
Jonne,
Thanks for your time and patience.  You wrote : you could use pdftk to split them first.  Could you explain more how to go about it ?

---

### Post by Jonne on 2008-04-11
basically you install pdftk (using synaptic or apt-get), then you use 
```
pdftk mydoc.pdf burst
```
to split the pdf into multiple pages. After that you can run convert on the resulting single-page pdf's.

Read pdftk's manual for more info on its flags and stuff.

---

### Post by danbar on 2008-04-11
This is what the terminal gave me.....Error: Failed to open PDF file: 
   provapdfjpg.pdf
Done.  Input errors, so no output created.

---

### Post by Jonne on 2008-04-11
i guess there's something wrong with your pdf, then :s . I've never seen pdftk fail (but that's not saying much, I rarely use it). Can evince or xpdf open it properly?

---

### Post by danbar on 2008-04-11
Yes i opened it with Evince and it's ok !

---

### Post by danbar on 2008-04-11
By the way how can I open Pdftk ?

---

### Post by ridgeland on 2008-04-11
Hi danbar,
I can get the same error if I do

pdftk nofile.pdf burst

What did you use?  Full valid pathname?
You probably just need the full path name like
pdftk /home/me/myfile.pdf outfile

Also use
pdftk --help
to learn more
or 
man pdftk

---

### Post by k8b on 2008-08-10
There is a muck simpler way to split multipage pdfs into a jpg:

convert  -quality 100 -density 600x600 multipage.pdf single%d.jpg

[LIST]
[*]The -density option defines the quality the pdf is rendered before the convert > here 600dpi. For high quality prints you can increase that number. 
[*]The %d just before the jpg suffix is for automatic numbering of the output pages 0,1,2...
[*]The  -quality option defines the compression quality of the output jpg (0 min ... 100 max)
[*]The .jpg suffix defines the output format. You could use .png/.jpg/.pdf
[/LIST]

On linux I recommended to use png files, because of patent issues of jpg's. If pdf output is used, the pdf will saved as an image.

Note: If you need to crop the pages add "-crop 1000x750+1450+150" between "convert" and "-quality"

---

### Post by modemlamer on 2010-11-08
> **Jonne said:**
> I think I found it, thanks to WW. Apparently it depends on the syntax you use. If you add the switches before giving the filename of the pdf, it will not ignore -density and such. If you give the filename first (like in the example I posted), Imagemagick will first rasterize the pdf, and only apply the switches afterward, thus giving degraded quality. to recap:
bad:
convert file.pdf -density 200x200 file.jpg

good:
convert -density 200x200 file.pdf file.jpg

thanks guys :)

thx man, u saved my day

---

### Post by dhjdhj on 2011-02-09
I'm having a related problem --- I have a multipage PDF file which contains one image per page. I have tried using convert to convert that PDF into images (using the %d in the jpg filename) but I'm only getting the first page.

I have used convert in the past to convert multipage PDF files into a sequence of jpgs with no problem. Anyone know why this might now be failing ---

---

