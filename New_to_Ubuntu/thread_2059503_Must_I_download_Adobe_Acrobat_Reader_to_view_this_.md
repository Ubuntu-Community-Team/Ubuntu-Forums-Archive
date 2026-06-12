---
title: "Must I download Adobe Acrobat Reader to view this PDF?"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by hanzj on 2012-09-18
Dear community,

There's a PDF that I want to view, but when I download and try to view it on my Linux computer, the PDF says: 


> Please wait...
If this message is not eventually replaced by the proper contents of the document, your PDF viewer may not be able to display this type of document.

You can upgrade to the latest version of Adobe Reader for Windows®, Mac, or Linux® by visiting [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html).

For more assistance with Adobe Reader visit [http://www.adobe.com/support/products/acrreader.html](http://www.adobe.com/support/products/acrreader.html).

Windows is either a registered trademark or a trademark of Microsoft Corporation in the United States and/or other countries. Mac is a trademark of Apple Inc., registered in the United States and other countries. Linux is the registered trademark of Linus Torvalds in the U.S. and other countries.


Do I really need to install Adobe Acrobat reader? Is there some other way, maybe a Website that I can upload the file to and spit out a PDF that can be viewed on any PDF viewer?

The file is on 
[http://www.cic.gc.ca/english/information/applications/permit.asp](http://www.cic.gc.ca/english/information/applications/permit.asp). Specifically, the PDF that's causing problems is [http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf](http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf). (It's a government website. It's a safe link/file)

---

### Post by kimberlite on 2012-09-18
I have opened with Acrobat Reader 9. It is a form, that you can fill and save. Evince unfortunately can not handle this and I do not know any other application which can.

---

### Post by shreepads on 2012-09-18
Yes.

See: [http://www.quickpdflibrary.com/faq/if-this-message-is-not-eventually-replaced-by-the-proper-contents-of-the-document.php](http://www.quickpdflibrary.com/faq/if-this-message-is-not-eventually-replaced-by-the-proper-contents-of-the-document.php)

One option, open with Adobe Reader and print to one of them PDF Printers as a std PDF... Or get from source in another format.

---

### Post by newb85 on 2012-09-18
> **hanzj said:**
> Dear community,

There's a PDF that I want to view, but when I download and try to view it on my Linux computer, the PDF says: 




Do I really need to install Adobe Acrobat reader? Is there some other way, maybe a Website that I can upload the file to and spit out a PDF that can be viewed on any PDF viewer?

The file is on 
[http://www.cic.gc.ca/english/information/applications/permit.asp](http://www.cic.gc.ca/english/information/applications/permit.asp). Specifically, the PDF that's causing problems is [http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf](http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf). (It's a government website. It's a safe link/file)

I hate to be the bearer of bad news, but this looks to me like it's been designed to force you to use Acrobat Reader.  Unfortunately, not all .pdf files are created equal (which, IMO, completely defeats the purpose of .pdf).

---

### Post by hanzj on 2012-09-18
Thank you, folks, for your reply. 
Wish there was a way for our PDF viewer to ignore this restriction and show us the PDF's contents.

---

### Post by newb85 on 2012-09-18
> **hanzj said:**
> Thank you, folks, for your reply. 
Wish there was a way for our PDF viewer to ignore this restriction and show us the PDF's contents.

The trouble is that the link doesn't actually download the correct .pdf file.  Instead, it downloads the file you saw, with embedded instructions for Adobe Reader to download and display the correct one.  An underhanded tactic to force you to use the reader they want you to use.  And the frustrating part is that once you do open the file, you will probably realize that there was no reason your .pdf reader of choice was insufficient to display the document's contents.

(Sorry for the short rant...not really...)

Edit: My two-file theory now appears to be incorrect.  Sorry

---

### Post by js9 on 2012-09-18
newb85, thanks for that tip. How do we figure out the URL for the real PDF file?

---

### Post by kimberlite on 2012-09-18
As I wrote earlier, I have downloaded the file. Evince was not able to open it, but displayed the "Please wait ..." message. Only Acrobat can open it.

---

### Post by Swagman on 2012-09-18
Strange.. I'm running Ubuntu 11:10 (32bit) and that link opened fine

[[IMG]http://img560.imageshack.us/img560/9601/pdfthingy.th.jpg[/IMG]](http://img560.imageshack.us/i/pdfthingy.jpg/)

---

### Post by Cheesemill on 2012-09-18
> **Swagman said:**
> Strange.. I'm running Ubuntu 11:10 (32bit) and that link opened fine

[[IMG]http://img560.imageshack.us/img560/9601/pdfthingy.th.jpg[/IMG]]("http://img560.imageshack.us/i/pdfthingy.jpg/")
That's because you have Adobe Acrobat Reader installed :)

---

### Post by Linux_junkie on 2012-09-18
After looking at the image of that document it appears that it has some encription technology built in to it.  This is probably the reason why no other PDF viewer can view the document.

---

### Post by dniMretsaM on 2012-09-18
> **Linux_junkie said:**
> After looking at the image of that document it appears that it has some encription technology built in to it.  This is probably the reason why no other PDF viewer can view the document.

That's what it seems like to me as well. If you look at the file in a hex editor you can even see the word "Encrypt" near the end of the file.

---

### Post by Swagman on 2012-09-19
> **Cheesemill said:**
> That's because you have Adobe Acrobat Reader installed :)

lol

So I do have.  I wonder when/how that got in there ?

/me looks at the missus.. "WOMAN ?" <---Commanding voice (I have her permission to use it !!)

---

### Post by hanzj on 2012-09-21
Can a non-AdobeAcrobat program decrypt the PDF so that we can view it?

---

### Post by tienlbhoc on 2012-09-21
I think you must use adobe reader to get the best function :p

---

