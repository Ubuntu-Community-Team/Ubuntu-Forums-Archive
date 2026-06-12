---
title: "Read text from image in python"
date: 2012-01-27
forum: Programming Talk
---

### Post by prismctg on 2012-01-27
How can I read text from any image file using python 3.x ???Is there any module for this?

---

### Post by Zugzwang on 2012-01-27
Do you mean [Optical character recognition (OCR)]("http://en.wikipedia.org/wiki/Optical_character_recognition") or does your question refer to reading something like embedded comment texts from the image files?

---

### Post by prismctg on 2012-01-27
yes, i mean OCR

---

### Post by Zugzwang on 2012-01-27
This is what a quick google search yielded for me: [http://code.google.com/p/pytesser/](http://code.google.com/p/pytesser/) and [http://stackoverflow.com/questions/5799946/python-ocr-module-in-linux](http://stackoverflow.com/questions/5799946/python-ocr-module-in-linux) - Looks like a usable solution.

---

### Post by prismctg on 2012-01-27
But [http://code.google.com/p/pytesser/](http://code.google.com/p/pytesser/) is not for python 3.x ,it has been tested with Python 2.4 .... :(

---

### Post by Zugzwang on 2012-01-27
The first answer in [http://stackoverflow.com/questions/5799946/python-ocr-module-in-linux](http://stackoverflow.com/questions/5799946/python-ocr-module-in-linux) contains a code snippet that is so short that it should be easy to adapt to Python 3. Perhaps even no modification is necessary.

---

### Post by prismctg on 2012-02-01
thnx

---

### Post by Bodsda on 2012-02-02
This looks interesting - pulled from the previous stack overflow link

[http://code.google.com/p/ocropus/](http://code.google.com/p/ocropus/)

---

### Post by prismctg on 2012-02-02
thnx Bodsda   :)

---

### Post by BillInCampbell on 2013-01-06
As of Jan 2013 OCRopus and Tesseract do not work well with input from digital cameras or screenshots.  
The OCRopus says it's designed to use input from scanners using 300 to 600 dpi and the FAQ says:
.....
Out of the box, it will work poorly on other kinds of inputs, although you may be able to adapt it.
	Inputs it will not work on are:
		• handwriting
		• unprocessed digital camera-captured documents
		• text in photographic images
                • CAPTCHAs
......
Hi res photos of printed text might work - I haven't tried this.

I _have_ tried using Tesseract on screenshots and it fails miserably.  This is mostly due to the way Windows' CoolType and Apple's anti-aliasing render text by what's called Font Smoothing or Sub-pixel Rendering.  They essentially treat the Red Green and Blue dots that are in each pixel as white dots to give them 3x the resolution. This is why you see colors halos around some text if you look closely.

Unfortunately I have still not found an open source code library that handles images. Nor have I found a good description of good algorithms for this.  They must be out there because there are numerous apps and even MS OneNote that will OCR from photos.

---

