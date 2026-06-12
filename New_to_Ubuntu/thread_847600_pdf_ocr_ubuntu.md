---
title: "pdf ocr ubuntu"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by LinuxRocks713 on 2008-07-02
Hi:

Does anyone know of a program that can run OCR from a PDF file? Tesserec only works for TIFF Format.

---

### Post by LinuxRocks713 on 2008-07-03
bump

---

### Post by pixnaps on 2008-09-28
I'll second that request!

---

### Post by JKyleOKC on 2008-09-28
It's definitely the long way around, but have you considered viewing the PDF file, taking a screen shot of it, converting the screen shot to TIFF format, and finally running Tesseract on the result?

I've had to do something similar to recover photos from an Adobe Photo Album format, which is PDF, in order to include them in a newsletter that I edit. There's no question that a single program to convert directly would be better, but if the need is great enough there's usually a way...

---

### Post by Tweepy on 2009-06-14
You can also install the PDF import plugin for Open Office, then save every images straight to whatever format, without loosing any quality.

---

### Post by Ian Clark on 2009-06-21
How about in terminal
```
convert filename.pdf filename.tif
```

---

### Post by treesurf on 2009-06-21
> **Tweepy said:**
> You can also install the PDF import plugin for Open Office, then save every images straight to whatever format, without loosing any quality.

The PDF import plugin for Open Office does work really well for text heavy pdfs and is super simple to use.

---

### Post by blueridgedog on 2009-06-21
The program tesseract can do it, but you need to use ghost script to convert the PDF to a tiff first.  Here is a good overview:

[http://www.groklaw.net/articlebasic.php?story=20061210115516438](http://www.groklaw.net/articlebasic.php?story=20061210115516438)

---

### Post by phillw on 2010-02-17
PDFedit is a good programme, I use it as it splits out text and images very well, so you can re-build the document however you want (It's in the repos').

Regards,

Phill.

---

### Post by syb0rz on 2011-02-08
After 3 days of working on this I have a good solution here:

1) use  pdf2djvu  to convert the PDF file to a DJVU file
2) use  ocrodjvu  to run OCR and add searchable text
3) use djvutxt to extract the text layer from the DJVU file

This is very fast. Total time for a 400-page book is about 10 minutes. Good luck!

---

### Post by syb0rz on 2011-02-08
> **syb0rz said:**
> After 3 days of working on this I have a good solution here:

1) use  pdf2djvu  to convert the PDF file to a DJVU file
2) use  ocrodjvu  to run OCR and add searchable text
3) use djvutxt to extract the text layer from the DJVU file

This is very fast. Total time for a 400-page book is about 10 minutes. Good luck!

Regarding ocrodjvu, make sure you get the latest source (0.7.1 at time of post) from the author's site: [http://jwilk.net/software/ocrodjvu](http://jwilk.net/software/ocrodjvu). Also, get the latest tesseract-ocr (3.0.0) and language packs from [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/). The Ubuntu repositories aren't up-to-date on either of these crucial pieces of code.

---

### Post by zeddock on 2011-03-09
> **syb0rz said:**
> After 3 days of working on this I have a good solution here:

1) use  pdf2djvu  to convert the PDF file to a DJVU file
2) use  ocrodjvu  to run OCR and add searchable text
3) use djvutxt to extract the text layer from the DJVU file

This is very fast. Total time for a 400-page book is about 10 minutes. Good luck!

Can you give explicit steps for noobs, please?

zeddock

---

### Post by rwigle on 2011-05-11
Here's how to grab the text from West.pdf:

1. install DjView4 using Ubuntu Software Centre.

2. install ocrodjvu using Ubuntu Software Centre.

3. ```
pdf2djvu -o West.djvu West.pdf
```

4. ```
ocrodjvu -o ocrWest.djvu  West.djvu

```

5. ```
djvutxt ocrWest.djvu West.txt
```

---

### Post by nonkreon on 2011-05-12
I was trying to convert a turkish pdf for two days. i tried tesseract embedded in ocrfeeder but it didn't work well. i tried to embed cuneiform in ocrfeeder but found myself trying to upgrade ocrfeeder to version 0.7.4 which reloading synaptic would only make it 0.6.6-3 which is another bump. i installed many other packs on the process causing me hours but then all i got is "import sane" error but sane is already installed on the process by me. ocropus, cuneiform, tesseract, none works. after not being able to revive software-center, this is the second time ubuntu got me. I'm really starting to lose it you guys...
 
PS: you know there are many online tools for ocr i realized but there should be an offline version.

---

### Post by zeddock on 2011-05-12
> **nonkreon said:**
> I was trying to convert a turkish pdf for two days. i tried tesseract embedded in ocrfeeder but it didn't work well. i tried to embed cuneiform in ocrfeeder but found myself trying to upgrade ocrfeeder to version 0.7.4 which reloading synaptic would only make it 0.6.6-3 which is another bump. i installed many other packs on the process causing me hours but then all i got is "import sane" error but sane is already installed on the process by me. ocropus, cuneiform, tesseract, none works. after not being able to revive software-center, this is the second time ubuntu got me. I'm really starting to lose it you guys...
 
PS: you know there are many online tools for ocr i realized but there should be an offline version.

I hear you brother!

This is a tremendously weak area of linux/Ubuntu IMO... It keeps business pros, who are power-USERs from joining the ranks.

I have found pDFStudio to be the best drop-in replacement for most of my Acrobat-ish needs, but OCRing into a selectable PDF is just not up to speed on Linux.

My only reliable solution has been to build a simple... hahaha... Win7 virtualbox and go to Acrobat Pro on that.  It disgusts me, because of how powerful this OS is at most other things.

I feel your pain, but I cannot help.

Sorry.

zeddock

---

### Post by nonkreon on 2011-05-12
Then I guess we just have to keep doing it on online sources... after uninstalling and reinstalling ocrfeeder couldn't start so that leaves me no way out... My hope is to become a good engineer and solve these problems so the next generations won't have to suffer being forced to use microsoft. I mean what good can come from something that is called "micro" and "soft"...

---

### Post by realmagnum on 2011-06-09
I would like to disagree from the suggestions previously mentioned.

For beginners, the best alternative is gscan2pdf.

```
sudo aptitude install gscan2pdf
```

It has graphical interface and you will be able to work directly with .pdf files.

You can also install the available language packs:

```
sudo aptitude install tesseract-ocr tesseract-ocr-data tesseract-ocr-eng tesseract-ocr-nld tesseract-ocr-deu tesseract-ocr-fra tesseract-ocr-por tesseract-ocr-deu-f tesseract-ocr-ita tesseract-ocr-spa tesseract-ocr-vie
```

---

### Post by zeddock on 2011-06-09
gscan2pdf is what I use as well, too scan into pdf on Ubuntu... Also to import images and save them as pdf. It does a great job EXCEPT it does not have OCR such that the text can be selected from within the PDF!

The text that is OCRed is held in a layer which is not attached to the position of the PDF text it recognized.

This is OK for searching through a clump of PDF's for some text, but it misses the mark for those who need to work with the text within a huge PDF document.

I mean no offense by my previous statements. This is just an area where Linux is SO CLOSE but misses in the last mile.  In fact, the OCR options on linux I think are superior in some ways to the Adobe OCR methods on Windows, speaking of OCR accuracy.  But without being able to select across a sentence in the PDF and copy the OCRed text to my buffer, most POWER USERS of PDF's are left wanting.

zeddock

PS. I doubt it would take much to finish this last-mile-need, but so far I have not found a reasonable tool. Please share if I am wrong or if there is another alternative?

---

### Post by texla on 2011-06-14
> **realmagnum said:**
> I would like to disagree from the suggestions previously mentioned.

For beginners, the best alternative is gscan2pdf.

```
sudo aptitude install gscan2pdf
```It has graphical interface and you will be able to work directly with .pdf files.

You can also install the available language packs:

```
sudo aptitude install tesseract-ocr tesseract-ocr-data tesseract-ocr-eng tesseract-ocr-nld tesseract-ocr-deu tesseract-ocr-fra tesseract-ocr-por tesseract-ocr-deu-f tesseract-ocr-ita tesseract-ocr-spa tesseract-ocr-vie
```
Thanks [realmagnum]("http://ubuntuforums.org/member.php?u=319849") - now my Gscan2pdf is scanning documents in French (near) perfectly!  

Just a note about how to get to the OCR text once you save the PDF with Gscan2pdf. It is annoying that is not connected to the text but at least it is "hidden" in the doc and that makes it much more usable than a regular scanned pdf.  
The OCR can be found in the PDF by choosing "select all" from the edit menu.  The PDF will show a little selection in the top left hand corner of your pdf. Then copy and you can paste it into any other text editor or doc and use the text.  Unfortunately, I find this method is only manageable for single page PDFs.  With a multiple page PDF it saved all the text from each page in one continuous jumble on each page - oh well - this is a good start though and I'll be waiting for that next step in Ubuntu OCR.... :popcorn:

---

### Post by zeddock on 2011-06-14
> **texla said:**
> Thanks [realmagnum]("http://ubuntuforums.org/member.php?u=319849") - now my Gscan2pdf is scanning documents in French (near) perfectly!  

Just a note about how to get to the OCR text once you save the PDF with Gscan2pdf. It is annoying that is not connected to the text but at least it is "hidden" in the doc and that makes it much more usable than a regular scanned pdf.  
The OCR can be found in the PDF by choosing "select all" from the edit menu.  The PDF will show a little selection in the top left hand corner of your pdf. Then copy and you can paste it into any other text editor or doc and use the text.  Unfortunately, I find this method is only manageable for single page PDFs.  With a multiple page PDF it saved all the text from each page in one continuous jumble on each page - oh well - this is a good start though and I'll be waiting for that next step in Ubuntu OCR.... :popcorn:

You nailed it!

As long as it is a single page PDF... or even two maybe, you will be fine.
But I deal with files with over 300 pages regularly.

For a power user, there still is not an answer on the Linux/Ubuntu side from what I see.

Hope those devs put something together soon.  It would be worth some money to me!

Thanx!

zeddock

---

### Post by mbocciab on 2011-09-13
I've used gscan2pdf for 3 months to scan documents and it's a pain in the ***. It required crop after selection for every single part of the page to be OCR.
I agree with zeddock ... it's still a very huge missing point in Linux! A colleague of mine is not passing to linux due to this point so we can consider it a very blocking point to windows to linux migrations!

---

### Post by MarjaE on 2011-10-03
> **zeddock said:**
> gscan2pdf is what I use as well, too scan into pdf on Ubuntu... Also to import images and save them as pdf. It does a great job EXCEPT it does not have OCR such that the text can be selected from within the PDF!

The text that is OCRed is held in a layer which is not attached to the position of the PDF text it recognized.

This is OK for searching through a clump of PDF's for some text, but it misses the mark for those who need to work with the text within a huge PDF document.

I mean no offense by my previous statements. This is just an area where Linux is SO CLOSE but misses in the last mile.  In fact, the OCR options on linux I think are superior in some ways to the Adobe OCR methods on Windows, speaking of OCR accuracy.  But without being able to select across a sentence in the PDF and copy the OCRed text to my buffer, most POWER USERS of PDF's are left wanting.

zeddock

PS. I doubt it would take much to finish this last-mile-need, but so far I have not found a reasonable tool. Please share if I am wrong or if there is another alternative?

You also need half-decent language support. gscan2pdf doesn't have that, since it's only compatible with Tesseract 2.0, not 3.0. And I can't get Cuneiform working either.

---

