---
title: "PDF/PDF Software alternatives?"
date: 2018-11-28
forum: New to Ubuntu
---

### Post by alejandro202 on 2018-11-28
Hello Ubuntu Community,

I recently downloaded Ubuntu and I'm trying to equip my Ubuntu Machine. I was trying to look for a good PDF Editor that allows merging and edition (eg. deleting a page), my machine already has a PDF Reader ([https://wiki.gnome.org/Apps/Evince](https://wiki.gnome.org/Apps/Evince)) . Is there any good software out there? Or is there any alternative for this?

Thanks :P

---

### Post by TheFu on 2018-11-28
If you seek a GUI tool for this, there's a commercial tool that AskNoah recommends. I don't remember the name or episode, sorry.

I use CLI tools like **gs** which are F/LOSS for splitting files on every page, then merging them back in whatever order I need.

Sometimes xournal is sufficient for quick PDF annotations. Use File --> Export to save changes. 

Beware that the F/LOSS tools don't support the most recent PDF standards.  Many are on v1.6 PDF still so any new PDF files formats aren't supported. This isn't an issue, until it is.  The 'file' command  will say which version of PDF is used. For example:
```
$ file /usr/share/doc/qpdf/qpdf-manual.pdf
/usr/share/doc/qpdf/qpdf-manual.pdf: PDF document, version 1.4

$ file /usr/share/cups/data/*pdf
/usr/share/cups/data/classified.pdf:       PDF document, version 1.2
/usr/share/cups/data/confidential.pdf:     PDF document, version 1.2
/usr/share/cups/data/default.pdf:          PDF document, version 1.5
/usr/share/cups/data/default-testpage.pdf: PDF document, version 1.4
/usr/share/cups/data/form_english.pdf:     PDF document, version 1.4
/usr/share/cups/data/form_russian.pdf:     PDF document, version 1.4
/usr/share/cups/data/secret.pdf:           PDF document, version 1.2
/usr/share/cups/data/standard.pdf:         PDF document, version 1.2
/usr/share/cups/data/topsecret.pdf:        PDF document, version 1.2
/usr/share/cups/data/unclassified.pdf:     PDF document, version 1.2

```

---

### Post by logix2 on 2018-11-29
Try the PDF Shuffler tool, available in Ubuntu Software.

---

### Post by speartip on 2018-12-01
MasterPDFEditor
[https://code-industry.net/free-pdf-editor/](https://code-industry.net/free-pdf-editor/)

---

### Post by Tadaen_Sylvermane on 2018-12-01
I also like Xournal for simply adding images to pdfs. Easy enough. Not sure about more complicated editing though.

---

### Post by pauljw on 2018-12-01
> **alejandro202 said:**
> Hello Ubuntu Community,

I recently downloaded Ubuntu and I'm trying to equip my Ubuntu Machine. I was trying to look for a good PDF Editor that allows merging and edition (eg. deleting a page), my machine already has a PDF Reader ([https://wiki.gnome.org/Apps/Evince](https://wiki.gnome.org/Apps/Evince)) . Is there any good software out there? Or is there any alternative for this?

Thanks :P

LibreOffice handles pdf files.  I'm not sure how much it can do, but I just now tested it's ability to delete a page and save the changed document. You do have to then export the file LibreOffice created to a pdf, but it worked.

---

### Post by kurt18947 on 2018-12-01
> **pauljw said:**
> LibreOffice handles pdf files.  I'm not sure how much it can do, but I just now tested it's ability to delete a page and save the changed document. You do have to then export the file LibreOffice created to a pdf, but it worked.

My pdf editing needs are modest but LibreOffice draw has done what I've needed. I think it saves in a hybrid format where added content is editable and once exported as PDF, there's no editing.

---

### Post by pauljw on 2018-12-01
> **kurt18947 said:**
> My pdf editing needs are modest but LibreOffice draw has done what I've needed. I think it saves in a hybrid format where added content is editable and once exported as PDF, there's no editing.

I was using LibreOffice Writer and I just checked and was able to open the exported pdf and edit again.  I'm also running Ubuntu 16.04/LibreOffice5 here, so maybe something changed with a newer version.

---

### Post by kurt18947 on 2018-12-02
> **pauljw said:**
> I was using LibreOffice Writer and I just checked and was able to open the exported pdf and edit again.  I'm also running Ubuntu 16.04/LibreOffice5 here, so maybe something changed with a newer version.

I think - not sure - that you can select whether exported PDF documents are editable.

---

### Post by TheFu on 2018-12-02
There are different sorts of PDF files.  PDF is based on PostScript.

100% ASCII PDF is easy to edit since there aren't any embedded images.

But to be able to handle any sort of visual document, embedded images are a key part of PDF files. 

And a mix of image and ASCII PDF files. Hopefully, the images aren't of scanned text, but are graphics.

If we create a PDF file that doesn't have any images or scans, then, depending on the creation tool, it will be 100% ASCII and editable in many tools.

When I say 100% ASCII, that ignores any compression or encryption.  Newer PDF standards include both.

If you want to truly edit a PDF file, then do everything you can to avoid image-based pages.

---

### Post by pauljw on 2018-12-02
> **kurt18947 said:**
> I think - not sure - that you can select whether exported PDF documents are editable.

:)  At any rate, seems to me the OP most likely already has a capable program for his task in LibreOffice.

---

### Post by zerubbabel on 2019-07-14
I've tried everything, I think, and lacking an adequate open-source alternative, I finally forked over the funds for two excellent pdf editors: PDF X-Change Editor Plus (a Windows application that runs very well with Wine), and PDF Studio Pro (cross platform). Between the two of them, I have been able to do anything I needed to do, including impositions (with PDF Studio). They are reasonably priced. PDF Studio Pro is more expensive than PDF X-Change, but its developer, Qoppa Software, always runs a "Buy-it-Now or Best Offer" on eBay, and they accept offers substantially less than the list price. Both of these editors are excellent. I tried Master PDF Editor also, but I did not find it as versatile as these other two options.

---

### Post by fyfe54 on 2019-07-14
[https://pdfsam.org](https://pdfsam.org)
There is a "basic" version that does split pages out of a document and merge pages in.

---

### Post by Eduardoecp on 2020-06-13
I recommend PDFedit. It's a very complete and powerful app. You can get it from [source forge]("https://sourceforge.net/projects/pdfedit/").

If you have any trouble with dependencies, you can try [this]("https://scriptips.org/2020/06/02/pdfeditor/").

---

### Post by mmoseeker on 2020-06-19
i would recommend

LibreOffice Draw 
Key Features: 
Edit the text in a file 
Add text/images in the file 
Manipulate the existing content 
Supports creating PDF files 
Cross-platform

---

