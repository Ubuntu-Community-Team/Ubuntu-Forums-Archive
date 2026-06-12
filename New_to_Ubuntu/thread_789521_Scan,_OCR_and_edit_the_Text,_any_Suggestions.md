---
title: "Scan, OCR and edit the Text, any Suggestions?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by bobnutfield on 2008-05-10
Hello Everyone,

I was wondering if anyone knows of any software available for Ubuntu (or any linux, for that matter) that is similar to ABBY Fine Reader.  Basically, all I want to do is be able to scan a OOo created form (from either Writer or Calc) and use an OCR to save the file to text or PDF to be able to edit the text, or more simply put to fill in the blanks on the scanned form.  There are a number of apps available for Windows which do this, but I have not found anything similar in Linux.  

I have read about Tesseract, but it only reads tiff files and does not recognize formatting.  I have tried Ocrad as a plougin for Kooka and gocr as a plugin for XSANE.  None of these work as they just spit out unreadable garbage.  This is completely new territory for me and I may not be using the correct settings in my scanning programs to get a good readable scan, so if anyone has any experience with this, I would sure appreciate some advice.

Best regards

Bob

---

### Post by halitech on 2008-05-10
What scanner (make/model/connection type) are you using and can you scan an image without trying to get it into a document?

---

### Post by bobnutfield on 2008-05-11
Thanks for the reply...

Maybe my post was not clear enough.  I can scan images and documents without difficulty.  What I want to to is find a linux application which will allow editing of a document scanned and saved as a PDF (or TIFF or whatever), much the same as ABBYY Fine Reader does.  So far, I have tried XSANE using gocr as a plugin, Kooka with OCrad as a plugin, and Tesseract.  None of these has worked because they all just spit out garbage from the scanned image when trying save as text.  ABBYY Fine Reader will let you open a PDF file and edit it directly in the PDF file.

I have read some short tutuorials about editing in the gimp, but this is not practical.

Bob

---

### Post by Ludwig9 on 2008-10-11
> **bobnutfield said:**
> Thanks for the reply...

Maybe my post was not clear enough.  I can scan images and documents without difficulty.  What I want to to is find a linux application which will allow editing of a document scanned and saved as a PDF (or TIFF or whatever), much the same as ABBYY Fine Reader does.  So far, I have tried XSANE using gocr as a plugin, Kooka with OCrad as a plugin, and Tesseract.  None of these has worked because they all just spit out garbage from the scanned image when trying save as text.  ABBYY Fine Reader will let you open a PDF file and edit it directly in the PDF file.

I have read some short tutuorials about editing in the gimp, but this is not practical.Bob
I am having the same problems gocr and OCRAD while using Hardy and an old HP 6200C scanner. I have tried both Kooka and XSANE, but they can't read the text of an old photo-copied book which I downloaded on the net. I have not succeeded in getting Tesseract to work. I have downloaded it from [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/) and installed it from synaptic, but I can't find it anywhere among my accessories or programs. Where should it be? And does anyone know if OCR works any better in Intrepid Ibex? I would prefer to wait for the final version before installing it, but would do so now if OCR works better with it. 
Also, have you been able to use ABBYY FineReader with Ubuntu?

---

### Post by Jeo_fin on 2008-10-18
I don't know is this "real" answer but I use Abbyy thru VirtualBox (like Flash etc). It just makes life so much easier.
I also found [this]("http://ubuntuforums.org/showthread.php?t=361851&highlight=ocr") but haven't tried it yet.

---

### Post by Jose Catre-Vandis on 2008-10-18
> **Ludwig9 said:**
> I am having the same problems gocr and OCRAD while using Hardy and an old HP 6200C scanner. I have tried both Kooka and XSANE, but they can't read the text of an old photo-copied book which I downloaded on the net. I have not succeeded in getting Tesseract to work. I have downloaded it from [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/) and installed it from synaptic, but I can't find it anywhere among my accessories or programs. Where should it be? And does anyone know if OCR works any better in Intrepid Ibex? I would prefer to wait for the final version before installing it, but would do so now if OCR works better with it. 
Also, have you been able to use ABBYY FineReader with Ubuntu?

Tesseract is command line only

---

### Post by Jose Catre-Vandis on 2008-10-18
A few other suggesttions if working with pdfs:

pdfedit

pdftk

Or run Abbyy in wine?

---

### Post by Ludwig9 on 2008-10-18
> **Jose Catre-Vandis said:**
> A few other suggesttions if working with pdfs:

pdfedit

pdftk

Or run Abbyy in wine?
How does one get ABBYY FineReader? The trial version seems to be available only to companies with websites, not private individuals.
Cf. [http://www.abbyy.com/sdk/trial.asp?edition=el](http://www.abbyy.com/sdk/trial.asp?edition=el)

---

