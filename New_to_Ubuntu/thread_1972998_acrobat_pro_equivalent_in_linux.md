---
title: "acrobat pro equivalent in linux?"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by al.adab on 2012-05-04
hello there,

I'm using a sony ereader (prs-650) mainly to read academic articles - they generally are in a pdf format, and the sony (and possibly other ereaders as well) is not particularly pdf-friendly. 

A colleague uses Acrobat Pro to optimize PDFs for his Sony. He says it works fine. I'm wondering if Linux offers an equivalent to Acrobat Pro or possibly an alternative program that does the job. 

I'm on Xubuntu 12.04, btw. Thank you.

---

### Post by mike555 on 2012-05-04
You might want to look here;   [http://calibre-ebook.com/](http://calibre-ebook.com/)  .... Calibre in in repositories.

---

### Post by al.adab on 2012-05-05
thanx mike555 
I'm using calibre though it doesn't look like - at least in my experience - that its pdf>epub does a very good job...

---

### Post by arochester on 2012-05-05
Have you seen this? [http://www.cogniview.com/convert-pdf-to-excel/post/pdf-editing-creation-50-open-sourcefree-alternatives-to-adobe-acrobat/](http://www.cogniview.com/convert-pdf-to-excel/post/pdf-editing-creation-50-open-sourcefree-alternatives-to-adobe-acrobat/)

The comments mention Scribus as an alternative to Adobe Acrobat Pro.

---

### Post by joetait on 2012-05-05
There is a program called K2PDFOPT which is made specifically for this: [http://www.willus.com/k2pdfopt/](http://www.willus.com/k2pdfopt/)

---

### Post by al.adab on 2012-05-06
Not terribly sure about Scribus though I don't know it very well I have to say so will give it a try. 

[http://www.willus.com/k2pdfopt/help/linux.shtml](http://www.willus.com/k2pdfopt/help/linux.shtml) sounds very interesting. I'm trying now and with my very limited understanding of computer language I got stuck at/can't work out the instruction that reads

*cd /my/pdf/folder*

whatever I try (I'd like to test it on a complex PFD I have on my desktop - file:///home/imageraw/Desktop/RX-V10.pdf - terminal tells me *No such file or directory*...

Can you plz help?

---

### Post by llamabr on 2012-05-06
open a terminal and type:

```
cd /home/imageraw/Desktop
```
and then
```
ls *pdf
```

and post the output

---

### Post by al.adab on 2012-05-06
[I]~$ cd /home/imageraw/Desktop
imageraw@T42:~/Desktop$ ls *pdf
Camarthen.pdf  RX-V10.pdf  standard-tube-map.pdf[/I]

---

### Post by llamabr on 2012-05-06
> **al.adab said:**
> [I]~$ cd /home/imageraw/Desktop
imageraw@T42:~/Desktop$ ls *pdf
Camarthen.pdf  RX-V10.pdf  standard-tube-map.pdf[/I]

That's why you can't show file:///home/imageraw/Desktop/RX-V10.pdf - terminal tells me No such file or directory...

because it's not on your Desktop dir.  So where is it?  do a 

```
locate RX-V10.pdf
```

and post the output

---

### Post by jtarin on 2012-05-06
I use Acrobat Pro 9 in Ubuntu w/WINE.

---

### Post by Rodney9 on 2012-05-06
I use Calibre for converting my pdf ebooks to epub to read on my Sony PRS-650.

The only problem I have is removing the page numbers, but Calibre still makes it very readable.

Rodney

---

### Post by rewyllys on 2012-05-06
> **al.adab said:**
> hello there,

I'm using a sony ereader (prs-650) mainly to read academic articles - they generally are in a pdf format, and the sony (and possibly other ereaders as well) is not particularly pdf-friendly. 

A colleague uses Acrobat Pro to optimize PDFs for his Sony. He says it works fine. I'm wondering if Linux offers an equivalent to Acrobat Pro or possibly an alternative program that does the job. 

I'm on Xubuntu 12.04, btw. Thank you.
Although you've already had suggestions of programs that will probably take care of your preparation-for-sony-ereader need, I can recommend *PDF Studio Pro* as a general-purpose equivalent for *Adobe Acrobat Pro*.  

*PDF Studio Pro* is available from [http://www.qoppa.com/pdfstudio/index.html]("http://www.qoppa.com/pdfstudio/index.html")

---

### Post by al.adab on 2012-05-06
hang on a sec...it is on my desktop! :) RX-V10.pdf is the second of the list (three in total): 

[I]~$ locate RX-V10.pdf
/home/imageraw/Desktop/RX-V10.pdf[/I]

---

### Post by al.adab on 2012-05-06
thanks rewyllys
a bit pricey but looks very good

---

### Post by al.adab on 2012-05-08
sorry I don't want to give the impression I'm bumping this thread + being pushy (no hurry!), just meant to ask if there's any possibility the problem lie with the software itself?

---

### Post by al.adab on 2012-05-10
is this thread getting anywhere or shall i simply start a new one re: not being able to locate a PDF file on my desktop - plz see beginning of the thread

---

### Post by jtarin on 2012-05-10
> **al.adab said:**
> is this thread getting anywhere or shall i simply start a new one re: not being able to locate a PDF file on my desktop - plz see beginning of the thread
**You located a few post back.....or so you would lead us to believe.**

> hang on a sec...it is on my desktop! RX-V10.pdf is the second of the list (three in total):

~$ locate RX-V10.pdf
/home/imageraw/Desktop/RX-V10.pdf

---

### Post by al.adab on 2012-05-11
sorry my post was misleading. it was in reply to a previous post suggesting that the reason the software cannot locate a certain pdf file is that that very file is not on the desktop...

---

### Post by kelvin spratt on 2012-05-11
Your post is very misleading
you should really look in the software center type pdf in search
a clue if you just want to read pdf acrobat, is the adobe reader 
to edit you you can use. pdfedit,
To read write pdf libreoffice writer

---

### Post by al.adab on 2012-05-12
thanks for the lecture kelvin spratt. I'll keep that in mind. Regards.

---

### Post by Jose Catre-Vandis on 2012-05-12
This has been a holy grail for me as well, but nothing seems to come close to the ease of use of Acrobat Pro. That said try pdfchain (gui of pdftk)
```
sudo apt-get install pdfchain
```
also have a look here to see what you can do with Ghostscript:
```
http://milan.kupcevic.net/ghostscript-ps-pdf/
```

A quick example:
> gs -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=output.pdf input.pdf
This reduced a 400k pdf to 300k for me. You can also replace /screen with /ebook for improved resolution

It's worth trying out Libre Office to see what it can do to pdfs

Also look at poppler-utils (they should be installed) for various pdf manipulation tools

---

