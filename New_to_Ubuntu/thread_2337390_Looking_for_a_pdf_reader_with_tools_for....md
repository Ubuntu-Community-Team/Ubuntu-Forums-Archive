---
title: "Looking for a pdf reader with tools for..."
date: 2016-09-17
forum: New to Ubuntu
---

### Post by Citta on 2016-09-17
...highlighting, underlining, noting and crossing. In Win I was very  happy with the pdfXchange viewer, unfortunately not for Linux available.  Not exactly right, the company suggests to try a .zip, portable  version. Extracted as I would do in Win, but launching the application  resulted in an error...perhaps because I am a newbie? Wine, well, I have  already enough to do to get along with Linux, perhaps a topic for  experienced users. 
I checked the Ubuntu Software and did not find a solution, not wanting  to install every reader available there. How can I find  suitable  software, generally, what are the steps to be taken? Software outside of the Ubuntu  Software? 
Thanks a lot for you suggestions!

---

### Post by TheFu on 2016-09-17
**xournal**.  Use "export to PDF" to save changes, not "Save" ... saving just saves an application-specific data file with the modifications.  xournal is good for editing, not reading.  Use **evince** to read pdfs.

If you want to run Windows applications, then WINE needs to be loaded and the Windows program needs to be run under WINE. 

Don't install any software outside the normal repos when you are so new. There are repercussions that you are not ready to deal with. Those don't usually happen immediately, but take 3-12 months before you're system can't be maintained anymore.

BTW, "Software Center" is a very dumbed-down package manager. Install **Synaptic** if you want to see 35K packages that are available.

---

### Post by Geoffrey_Arndt on 2016-09-17
Sometimes, for a select few applications, one has to look harder:

>   Xjournal will do some editing (highlighting, underlining, adding text.   PDF editing is not it's main function, but it does a few things OK (C+)
>   Okular is the best PDF reader in Linux (by far) and does have some editing capability (plus can export pdf to text files, edit in LibreOffice and resave as PDF)
>   At least two commercial apps available for Linux.   This one has a free for home use option:   [https://code-industry.net/free-pdf-editor/](https://code-industry.net/free-pdf-editor/)

---

### Post by cmcanulty on 2016-09-17
is xjournal still available? I can't find xournal or xjournal in synaptic for 16.04.

---

### Post by Irihapeti on 2016-09-17
Xournal is still in 16.04, Universe repository.

During my brief experience with it, I discovered that it turns the document into a saved image, rather like a scan. That means I can no longer select and copy text.

Depending on what you want to do with the file, that may or may not matter, but I thought it was worth mentioning.

---

### Post by TheFu on 2016-09-17
> **Irihapeti said:**
> Xournal is still in 16.04, Universe repository.

During my brief experience with it, I discovered that it turns the document into a saved image, rather like a scan. That means I can no longer select and copy text.

I don't remember that, but all sorts of objects can end up inside a PDF file.  I used to work in publishing and wrote code to parse PDF files. With normal text-based (really postscript-like) PDFs like a word processor creates without images, that will not be the case.  OTOH, if the input is from a scanner then that will definitely be the situation, but OCR is possible to get most of the text placed "under" the image so that full-text searching is possible.

It isn't always clear when looking at a PDF what the underlying objects are.

As with all things computer related - garbage in --> garbage out.

---

### Post by zerubbabel on 2016-09-22
PDF-XChange Editor works very well on Linux via Wine. It's my favorite, and I use it all the time. There is also Master PDF Editor ([https://code-industry.net/free-pdf-editor/]("https://code-industry.net/free-pdf-editor/")) that runs natively on Linux, and is free (but not open source) for personal use.

---

