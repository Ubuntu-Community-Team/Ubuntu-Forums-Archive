---
title: "In which way can I transorm pdf file in ms word doc 97 format?"
date: 2024-02-21
forum: New to Ubuntu
---

### Post by nilovsergey on 2024-02-21
under kubuntu 22.04 I have a pdf file and I need to make a ms word doc 97 file to edit 
it under both Libre Office Writer and ms word doc 97.
If I open this file from Libre Office Writer the file is opened in Libre Office Draw application, which has no option 
to save file as word doc 97 file.  In which way can I transorm my file in ms word doc 97 format ?

---

### Post by TheFu on 2024-02-21
Get a time machine.  Go back to the year 2000. Run old OSes, old programs. ;)  Ok, that probably isn't too useful, but I'm only slightly joking. I really think you are stuck, since Word-97 has been dead for over a decade.  You could try to load Linux versions from 2000 into a virtual machine and load a word processor from that time that can read-write MS-Word files.

However, going back and forth between MS-Word (any version) and LibreOffice has never been perfect. There are all sorts of things that make the files display differently.  They will have different pagination and different fonts, styles, etc.  It never really works for other side of the group - Linux or Windows.

You might try running StarOffice from 2000, but I doubt it will run.  It was a Java program, I think.  While I have some shoes that are from that time, I don't remember so many things from 2000 anymore.

StarOffice ---> OpenOffice ---> LibreOffice

The best answer is to get the person using Word-97 to move to LibreOffice. It is cross platform and F/LOSS.

---

### Post by nilovsergey on 2024-02-22
Ok, not  ms word doc 97, but how to convert to MODERN(no sure which format current now)  ms word doc format?

---

### Post by ajgreeny on 2024-02-22
It will depend very much on the PDF itself; some have fonts embedded in them which can be highlighted and copied, others are simply images without those fonts so may not have that option.  They may still be possible to get text from using OCR, eg tesseract, though I'm not sure if you can put a PDF through tesseract or if you need to convert the image to, eg, tiff or jpg first.
I'm not on a Linux box at the moment so can't easily check that or search for other options to at least allow you to extract the text.

---

### Post by nilovsergey on 2024-02-22
Could you please explain why[COLOR=#000000] the pdf file is opened in Libre Office Draw application, but not [/COLOR][COLOR=#000000]Libre Office Writer as I need? I suppose [/COLOR][COLOR=#000000]Libre Office Writer can open and convert pdf into doc(x) file. But It does not in this case. Maybe in my system some configuration options are wrong ? How to check/fix it ?[/COLOR]

---

### Post by yancek on 2024-02-22
Explained at the libreoffice site/forum at the link below.  It wasn't created to be editable originally.    You could try modifying a 'pdf' file with software created to modify a 'pdf' file specifically such as Master PDF Editor.  Some editing is possible with Draw.

[https://ask.libreoffice.org/t/trying-to-open-pdf-document-but-it-opens-in-libre-office-draw-format/41246/7](https://ask.libreoffice.org/t/trying-to-open-pdf-document-but-it-opens-in-libre-office-draw-format/41246/7)

---

### Post by TheFu on 2024-02-22
> **nilovsergey said:**
> Could you please explain why[COLOR=#000000] the pdf file is opened in Libre Office Draw application, but not [/COLOR][COLOR=#000000]Libre Office Writer as I need? I suppose [/COLOR][COLOR=#000000]Libre Office Writer can open and convert pdf into doc(x) file. But It does not in this case. Maybe in my system some configuration options are wrong ? How to check/fix it ?[/COLOR]

PDFs hold images, not just text.  If the PDF was created by scanning an image, then there isn't any text, so Draw opens it for editing.
You do realize that PDF files where never intended to be editable, right?  They are for page accurate viewing of specific images.  Think magazine layouts, not text content that wraps automatically.

**If you want a format that can be edited, don't use PDF.**  Use a format like RTF, HTML, or one of the editing program native formats at creation time.

Page layout formatting is seldom required to efficiently relay information. Something like HTML is a more portable, editable, choice.  I used to work in document management, document creation and publishing.  We used PDF files in the printing, since we were creating paper books/magazines that had very specific location requirements for every character, image, on both sides of the page.  That job taught me to avoid page layouts when they aren't necessary.

I started using HTML as my preferred "document" format and have been using it for about 25 yrs now. HTML allows text to flow/wrap based on the screen size. Very handy.  Extremely cross platform.

---

### Post by monkeybrain20122 on 2024-03-08
Yes, you can open it in LO's writer and then save it to whatever editable format. Can't guarantee the quality though.

Instead of right clicking, start LO writer, go to File > Open and then go to the folder where your pdf is, in the drop down choose PDF-portable-document-format(writer) See  first screenshot. 

Once opened, go to File > Save as and pick .odt or .docx. Second screenshot is the pdf file, third screenshot after converting to odt which can be edited with LO writer.

---

### Post by MAFoElffen on 2024-03-10
If it doesn't contain "sensitive data" that you don't mind it going online to be processed/converted... There are free online resources to do that:

Example: [https://openpdf.com/lp/pdf-to-word.html](https://openpdf.com/lp/pdf-to-word.html)

---

### Post by monkeybrain20122 on 2024-03-12
Here is another way using python

[https://morioh.com/a/be54d7d747c9/how-to-convert-pdf-files-to-doc-with-python](https://morioh.com/a/be54d7d747c9/how-to-convert-pdf-files-to-doc-with-python)

---

