---
title: "converting mht to pdf"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by newport_j on 2012-09-13
I have a file that is in mht format. It is somewhat compiicated with a table of contents. I want to convert it to a pdf file so I can send it to my kindle fire to read it. Is there any freeware that can do that?
 
Any help appreciated thans in advance.
 
Newport_j

---

### Post by newport_j on 2012-09-13
I

---

### Post by Frogs Hair on 2012-09-13
> **newport_j said:**
> I have a file that is in mht format. It is somewhat compiicated with a table of contents. I want to convert it to a pdf file so I can send it to my kindle fire to read it. Is there any freeware that can do that?
 
Any help appreciated thans in advance.
 
Newport_j

I can't find any free-ware for Linux only Windows.

---

### Post by newport_j on 2012-09-13
Well, I will try that then. i have acces to Windows machines. I just cannot easily convert my mht file to pdf file.
 
Newport_j

---

### Post by Lars Noodén on 2012-09-13
> **Frogs Hair said:**
> I can't find any free-ware for Linux only Windows.

You are unlikely to find any freeware in the Ubuntu repositories, only Free and Open Source Software under various licenses.  There is a big difference.  

If you ask specifically for freeware (closed source but free-of-charge), then [Opera should open mht](http://www.dedoimedo.com/computers/mht-linux-firefox.html).  You can get Opera from [Opera's own repository](https://help.ubuntu.com/community/OperaBrowser).

If you ask for Free and Open Source Software, you can try the Chromium web browser.  It might be able to do it.  From there, print the file but instead of sending it to a printer, send it to a file.  PDF will be one of the options.  

You might also try Firefox, but it might need an add-on to deal with MHT.

Edit: Yes, there is an add-on for Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/unmht/](https://addons.mozilla.org/en-US/firefox/addon/unmht/)

---

### Post by Frogs Hair on 2012-09-13
I Know the difference and I think the OP is looking for a free program open source or otherwise . I know Opera can make the conversion after further reading and saw mention of extensions for other browsers also.

---

### Post by Lars Noodén on 2012-09-13
I've had a chance to test both Opera (freeware) and Firefox (FOSS).  Opera can read MHTML files natively.  Firefox does it with the easy-to-get add-on.  

From there it is just to 'print' the document to a file, saving as PDF.

This was interesting.  I hadn't run into [MHTML](https://tools.ietf.org/html/rfc2557) documents before.

---

### Post by newport_j on 2012-09-13
I tried on a windows machine to just print the file to pdf. It works, but it only 1 page is cnverted. The page shown on the screen; also the table of contents is shown in the left side of the page.. 
 
I have a complex mht file with a table of contents. I would rather do a full file conversion.
 
Then send the pdf file to my Kindle Fire. The Kindle Fire will not take mht files and let you easily read them. That is why I want to chnage it ot a pdf file.
 
thanks in advance.
 
Newport_j

---

### Post by Lars Noodén on 2012-09-13
Try "printing" from your linux machine.  Windows does not have very good conversion to PDF.

---

### Post by newport_j on 2012-09-14
I saved my .mht file and loaded it into Opera perfect! When I printed it to a file and selected the format as pdf I got only one page again!
 
I have a big file with a table of contents, I must save it that way.
 
Any help appreciated.
 
Newport_j

---

### Post by Lars Noodén on 2012-09-14
I used Opera to save a long web page as MHTML.  Then I got a multi-page PDF out of opening and printing from Firefox.  This was on Lubuntu 12.10b1

Edit: It might be the table of contents that is the problem.  Do you have a document with a table of contents that you are allowed to post somewhere?  If there is a bug reading or printing TOC then it should get reported.

---

