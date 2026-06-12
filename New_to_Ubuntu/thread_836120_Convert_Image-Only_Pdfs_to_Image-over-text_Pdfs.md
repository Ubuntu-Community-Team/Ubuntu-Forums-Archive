---
title: "Convert Image-Only Pdfs to Image-over-text Pdfs?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jlhs1971 on 2008-06-21
Hi

Does anyone know of an easy way (preferably using a gui) to convert image-only pdfs to image-over-text pdfs? Basically, I have a lot of image-only pdfs that I want to make searchable.

many thanks
julian

---

### Post by ajgreeny on 2008-06-21
I don't quite follow what you are trying to do so more info please.  You could always open the pdf and highlight the image and save it as something else (tiff, jpg?) and then add the text you want and save again as pdf using cups-pdf.  If that isn't what you are looking for ignore my ramblings. I've never tried to do that with evince, but you certainly can with kpdf or acroread.

---

### Post by jlhs1971 on 2008-06-21
HI

thanks for the reply. Basically, I scanned a lot of documents in the past to a pdf format as a pure image (i.e. one cannot copy or search the text in the PDF). This is not very useful when one wants to search one's database of documents. In order to make it more searchable (with Google Desktop for example) I need to convert the image-only PDF to one where an OCR has analyzed the document and provided a meta-text below (i.e. the original image is retained but a meta-text is added which can be indexed and searched using Google Desktop).

I hope this makes sense. I am sure that there are a lot of people out there who also have lots of PDF documents that need conversion. 

many thanks
julian

---

### Post by ajgreeny on 2008-06-21
OK now I see what you mean, but unfortunately can't help with the answer.

---

### Post by Mursalin on 2008-06-22
Hi jlhs... if you digg the forum you will find the answers. And maybe this thread is one of them, although it's quite an old thread but atleast it will give you the idea. The tool called tesseract. Here's the link:
```
[http://ubuntuforums.org/showthread.php?t=361851&highlight=ocr]("http://ubuntuforums.org/showthread.php?t=361851&highlight=ocr")
```
Just read all the posts inside that thread, as you will find much informations... including trial and errors.
Also note, that you might be needing another tool to convert the image into tiff file first, you cand find the information about that tool inside previous thread.
And here's the link for the tesseract tool (ubuntu hardy):
```
[http://packages.ubuntu.com/hardy/graphics/tesseract-ocr]("http://packages.ubuntu.com/hardy/graphics/tesseract-ocr")
``` 
Good luck.

p.s: the tool uses CLI, but it's not that difficult, i hope.

---

### Post by jlhs1971 on 2008-06-22
Thanks Mursalin

I did see that post before and tried Tesseract. It did not work on my test image-only pdf. I believe the image needed to be cleaned up a bit first. Nevertheless, I have a lot of pdfs to work on and i found Tessearct to be a bit too cumbersome. I know that Google is working on something (Ocropus) but it appears to me that there is no decent open source version of this kind of application. I am thus probably going to purchase ABBYY's PDF transformer ([http://buy.abbyy.com/content/pdftransformer/default.aspx?visitor=ea1ef5a9-5886-499c-85c8-eacd85384606](http://buy.abbyy.com/content/pdftransformer/default.aspx?visitor=ea1ef5a9-5886-499c-85c8-eacd85384606)) or else another commercial offering. Unfortunately, I am having trouble getting ABBYY's demo offering to work in WINE (sigh...) so I am looking into installing an XP emulator or dual boot.

For all of those who also have this issue it looks like the only viable route is the commercial one (unless someone hopefully proves me wrong on this thread!)


many thanks for your help

best 
julian

---

### Post by Mursalin on 2008-06-22
Hi Julian, it's me again..
Actually I have the same problem but in my case the pdf files are Arabic, which is a bit complicated as the supports are not widely available. and honestly I haven't tried tesseract my self. 
But here's a question: 
> It did not work on my test image-only pdf
on your trial using tesseract, did you convert the pdf files first into tiff format before processing with tesseract? maybe that could be the bridge-step to a success.
> For all of those who also have this issue it looks like the only viable route is the commercial one (unless someone hopefully proves me wrong on this thread!)
Somehow I agree with you, atleast untill the good people out there make a proggress to overcome this issue. Here's a windows program that probably will be my last destination incase I won't make it out.
```
[http://www.irislink.com/c2-669-225/Readiris-Pro-11-Middle-East.aspx]("http://www.irislink.com/c2-669-225/Readiris-Pro-11-Middle-East.aspx")
```

---

### Post by jlhs1971 on 2008-06-22
Hi Mursalin

Thanks for the link. That Iris software looks good especially for your needs for an Arabic OCR although at EUR498 it is not cheap! (ABBY is EUR85). I'm still looking around for a good OCR which will do the deed for me and also hopefully work on WINE. As for your question about whether I converted the PDF file to a TIFF, I did indeed. It still did not work. I basically used the method outlined in the following link: [http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704](http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704)

Take a look, but in my opinion, this method is far too cumbersome for anything other than a few pages. 

many thanks
julian

---

### Post by Mursalin on 2008-06-22
Hi Julian,
You're right about Readiris price in comparison to ABBY. I have to work hard to collect donations for this software if I have to buy it :)  And thanks for link as it gave me additional information arround this issue. Just don't forget to keep me and the community informed when you've found a good Linux-friendly OCR.
I think I have to take a break for today.

Thank you and have a nice day 
mursalin

---

### Post by LastWho on 2009-02-17
Please i m having the same issue as u guys, and wondering if readiris pro works on wine??? or if there is another alternative!!
i really don't want to reinstall windows :(

---

### Post by Benic on 2009-03-02
You can try gscan2pdf. It has an option for importing pdf and convert to it to image (jpeg, tif, png, ps, etc.).

About command-line programes, I tried imagemagick to convert pdf to tiff. It is simple and fast.

---

### Post by maizong on 2011-11-03
i read this article and its really good i found the solve its easy 
just read  it 

[http://www.freewaregenius.com/2011/11/01/how-to-extract-text-from-images-a-comparison-of-free-ocr-tools/](http://www.freewaregenius.com/2011/11/01/how-to-extract-text-from-images-a-comparison-of-free-ocr-tools/)
:guitar:

---

