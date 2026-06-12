---
title: "PDF Electronic Signatures"
date: 2010-01-26
forum: Programming Talk
---

### Post by beegary on 2010-01-26
I am trying to investigate electronic signatures via Linux, specifically for use with PDF's.
Acrobat (in Windows) can use the Windows certificate store to locate a .pfx file which then can be used to place an electronic signature on a PDF.
 
Is there a way of doing something similar via Linux/Ubuntu (without using Adobe software)? I create the files using Ghostscript, but that is as far as I have got!
 
Perhaps there is a way of comparing a signed and unsigned pdf and coding the difference??

---

### Post by beegary on 2010-01-27
bumpy mcbumpworthy
 
was it a stoopid question?

---

### Post by Zugzwang on 2010-01-27
No, by no means. It's just that not there's not much software supporting this signing stuff. But google found the following for me:

[http://itextpdf.sourceforge.net/howtosign.html](http://itextpdf.sourceforge.net/howtosign.html)

There's some example Java snipplet on the page telling you how to sign using your .pfx file. You just need to wrap it into some tool to get going.

---

### Post by beegary on 2010-01-27
> **Zugzwang said:**
> No, by no means. It's just that not there's not much software supporting this signing stuff. But google found the following for me:
 
[http://itextpdf.sourceforge.net/howtosign.html](http://itextpdf.sourceforge.net/howtosign.html)
 
There's some example Java snipplet on the page telling you how to sign using your .pfx file. You just need to wrap it into some tool to get going.
 
Thank you Zugzwang
There is so much avaiable online regarding this, I often have difficulty in indentifying what I am able to do from linux (Ubuntu). Sourceforge does seem to be a valuable resource that I will be returning to (so does google sorry ;)).
That helps allot, I now just have to learn some Java! I am in the middle of leaning Python, would it be possible to call a Java module from Python or would I be better off doing everything within Java: e.g the pdf creatiion, signing etc?
 
thanks again

---

### Post by tholy on 2011-02-21
This is rather belated, but two other approaches:
1. This is very easy when it works, but sometimes the format of the PDF gets mangled. Use openoffice/libreoffice with the PDF importer extension. If you're happy with the quality of the import, you can place a graphic containing your signature in the right spot. (It's best if you save your signature with a transparent background.) 
2. This one is more work, but it is guaranteed not to change the format of the document because nothing needs to be interpreted:
    a) Use pdftk to extract individual pages from the PDF (pdftk filename.pdf burst).
    b) Sign the page: open a new file in scribus and set the page size to be an entire page. Insert an image frame and make it the size of the whole page. Using "Get image" (right click), bring in the page you want to sign. Now insert another image frame for your signature. Export the signed page as a pdf.
    c) Use pdftk to join all the individual pages back into a single file.

---

### Post by Zugzwang on 2011-02-21
> **tholy said:**
> This is rather belated, but two other approaches:
...


Tholy, it is very kind of your to share your techniques with the rest of us here. Please note that this thread is on cryptographical digital signatures and not on the paper-based ones. If you are interested, you can find more information on that matter here: [http://en.wikipedia.org/wiki/Digital_signature](http://en.wikipedia.org/wiki/Digital_signature)

---

### Post by cariboo on 2011-02-21
Thread closed seeing as the poster that reopened it was off topic.

---

