---
title: "Automate PNG to PDF conversion?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by arijarot on 2008-05-10
Is there a way to automate a mass conversion of PNG to PDF and then make all those PDF files into one PDF file (in an ordered fashion)?

---

### Post by noynac on 2008-05-10
> **arijarot said:**
> Is there a way to automate a mass conversion of PNG to PDF and then make all those PDF files into one PDF file (in an ordered fashion)?
You can use convert from the ImageMagick package to convert multiple PNG files to one PDF file:

```
convert *.png outputfile.pdf
```

You could also do this as a two-step process--convert each individual PNG file to a PDF file with convert and then merge the individual PDF files into a master PDF file with Ghostscript or PDFtk. This would pretty much require a shell script if the number of PNG files is large.

I'm not sure what you mean by "an ordered fashion."

---

### Post by arijarot on 2008-05-10
Thank you, noynac, I will give this a try (minus the shell scripting, as I don't know how lol). What I meant by "orderly fashion," was that I want to combine all the pdf files into one while maintaining their numbered sequence.

---

### Post by z987k on 2010-01-26
I'm looking to do the same thing.

```
convert *.png book.pdf
```
works well, but it messes up the numbering.  The png's are scans of pages named book(*).png and convert throws them together in random order in the pdf.  How do I tell convert to do book(1).png then book(2).png etc?

---

### Post by beegary on 2010-01-26
> **z987k said:**
> 
```
convert *.png book.pdf
```works well, but it messes up the numbering.  The png's are scans of pages named book(*).png and convert throws them together in random order in the pdf.  How do I tell convert to do book(1).png then book(2).png etc?

Someone here may have a more elegant solution but a quick one that will work is to convert each png separately (dependant on the number of files you have you may need to script this!!!), then use ghostscript to join them up. Ensure that the created .pdf files are named in order, i.e page1 = book(1).pdf,  page2 = book(2).pd etc. then use this:

```
gs -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=<output>.pdf <pathtoinputfiles>*.pdf
```

---

### Post by z987k on 2010-01-26
Figured it out.  

The file names need to be in numerical order.  So lets say we have book1, book2, ... book10, book11, ... through book100.png

convert *.png book.pdf would order the files in the pdf incorrectly because book1 would go right before book100.  Renaming them book001 etc solves this.

---

### Post by beegary on 2010-01-26
> **z987k said:**
> Figured it out. 
 
The file names need to be in numerical order. So lets say we have book1, book2, ... book10, book11, ... through book100.png
 
convert *.png book.pdf would order the files in the pdf incorrectly because book1 would go right before book100. Renaming them book001 etc solves this.
 
I have never used ```
convert *.png book.pdf 
``` but i think the same would apply for the ghostscript command, just I have never got up to page 100 to find out!!!
Glad you got it sorted

---

### Post by BigRedButton on 2011-08-24
This all works for me pretty well except the pdf created is in landscape format, even though the images themselves are in portrait.  Is there any way to force convert to make the pdf in portrait?

---

### Post by wojox on 2011-08-24
> **BigRedButton said:**
> This all works for me pretty well except the pdf created is in landscape format, even though the images themselves are in portrait.  Is there any way to force convert to make the pdf in portrait?

If you 

```
man convert
```

It will show you the switches. Try:

```
convert -rotate 90 
```

---

### Post by DariusS on 2011-11-09
Thank you all so much - this just saved me some real headache.
```
convert *.png output.pdf
```
Worked like a charm, exactly as I needed it to. If there's one thing I can count on in life, it's Ubuntu Forums providing the answers I need.

---

### Post by ckpcw on 2012-05-03
Just wanted to add in -

If your scans are huge and you want to make a smaller-size PDF, just add "-resample X%", where 0<X<100.. play with it.

For my 300dpi document scans, this worked nicely:
```
convert -resample 45% doc*.png doc.pdf
```

-resize changes the document dimensions, but -resample leaves the scan dimensions intact. -quality seems to have little effect here.

---

### Post by oldos2er on 2012-05-03
Old thread closed.

---

