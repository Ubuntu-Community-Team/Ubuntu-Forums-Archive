---
title: "[Stress/hurry!] Text is not recognised in pdf. How to convert to text-pdf?"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by kramer65 on 2012-12-14
Hello,

I've got some PDFs in which the text is not recognised as being text. For example, if I search for words using Evince I can't find any of them even though they are obviously there in the text.

My goal is to annotate a line in the pdf using Okular, before sending it on to an official authority. Because it are some official documents and I will sent them to an official authority I don't just need the text, but I also need the text to be exactly formatted as it is now.

I tried gscan2pdf and ocrpdf, but both of these didn't seem to work well. Not only did they make quite a mess out of the text, they also couldn't keep its original formatting.

Because I need to send the documents on today there is quite some stress/hurry in this. So does anybody know how I can do this on Ubuntu? All tips are welcome!

---

### Post by maruf7 on 2012-12-14
Open the pdf file, select the text, copy-paste them in liboffice writer, edit and export as pdf again.

---

### Post by mastablasta on 2012-12-14
how did you get the PDF? if text was saved as picture in PDF then you won't be able to get text unless you maybe use some OCR programme.

---

### Post by kramer65 on 2012-12-14
> **maruf7 said:**
> Open the pdf file, select the text, copy-paste them in liboffice writer, edit and export as pdf again.
That is exactly the problem. I cannot select anything, because the text is not recognised as being text. In addition to that, I absolutely need to keep the original formatting and other images that are in the document (some official signatures by some authorities).

> **mastablasta said:**
> how did you get the PDF? if text was saved as picture in PDF then you won't be able to get text unless you maybe use some OCR programme.
So indeed, I need to use some kind of OCR, but up until now I can't find anything useful or workable. Anybody knows how I would be able to ocr my pdf without losing the formatting and images?

---

### Post by Bölvaður on 2012-12-14
> **kramer65 said:**
> So indeed, I need to use some kind of OCR, but up until now I can't find anything useful or workable. Anybody knows how I would be able to ocr my pdf without losing the formatting and images?

You wont!

The best thing to do to keep the formatting is to use what ever made it. If it is a long text you need to format, then you still have the entire day to write it again and format it. With an OCR you can extract the text if it is long enough to require it (like 2 pages or more of text), then you format it as you want it.

You could buy Adobe's program to edit pdfs, but I have no idea how to use it or anything else about it.

---

### Post by GordThompson on 2012-12-14
> **Bölvaður said:**
> You could buy Adobe's program to edit pdfs, but I have no idea how to use it or anything else about it.
I was thinking along the same lines. I used Adobe Acrobat years ago (v3.x, I think) and it could OCR an image within a PDF and place the text in an invisible layer that could be searched, but the presentation layer was still the image.

@kramer65

Perhaps you could download a trial version of Acrobat and see if it works for you:

[http://www.adobe.com/cfusion/tdrc/index.cfm?product=acrobat_pro&loc=us](http://www.adobe.com/cfusion/tdrc/index.cfm?product=acrobat_pro&loc=us)

---

### Post by Impavidus on 2012-12-14
In what sense do you have to annotate that pdf? You should be able to add comments, even overwrite or highlight with a background colour the original text, without having your computer recognise the characters as text. But okular or inkscape should be able to do so, so you probably have already tried. Modifying the original text without changing its formatting is indeed complicated. My last (but *really* last) resort would be manual editing in a text editor, but you have to be a postscript wizard to do so.

Anyway, you really should complain that people asked you to edit a file in a format that was never meant to be editable. They might learn for the next time. They might...

---

### Post by kurt18947 on 2012-12-14
Isn't there a plug-in, perhaps included by default in Libre Office Draw that enables annotating .pdf files?  It basically imports the .pdf then adds a layer on top of the .pdf containing your added text.  Then perhaps print to file?  I haven't had to do this in linux hence the question marks.

Edit:  Yes, there's an extension for Libre Office Draw called "pdf import".  It may take some learning but It looks like it'll work.  Eh, not too much learning.  Use file-open to import the .pdf file.  F2 is the shortcut to open the "add text" button.  My default font was Times New Roman 24.  It appears wise to change that before entering your first text, then your selected text will remain the default on that document.  "Export to pdf" button appears to work.  I tried it on a U.S. government .pdf form and it kept all text and formatting when exported using the "export to pdf" button.

---

### Post by kramer65 on 2012-12-14
Hi people. In the end I looked for someone who had a mac with Acrobat Pro installed. On his machine the built in OCR worked perfectly well (kkeping formatting and all) and from there I got it back to my machine.

In Okular I could highlight text perfectly well, but it was only able to save pdf's with annotation from version 0.15 while the version in the 12.04 repo's was 0.14.3. According to [this guide]("http://askubuntu.com/questions/172126/how-to-install-okular-0-15-on-12-04-lts") however, installing 0.15 messes up all sorts of things in Ubuntu 12.04. So I managed to install Okular 0.15 in a virtualbox installation of Ubuntu, annotated the file there, exported, and saved back to the host OS from where I just sent it on.

> **Impavidus said:**
> 
Anyway, you really should complain that people asked you to edit a file in a format that was never meant to be editable. They might learn for the next time. They might...

You would normally be right about this. The thing is that nobody asked me to do it. Some people actually did me a favour by sending me these documents and I am sending them onto a Technical University which I am trying to get into to do a PhD.

Hopefully these documents prove my proficiency in the relevant topics and convince them that I am the best guy to do the research.. :)

Thanks for all your help anyway!

---

### Post by Tristan Tonks on 2012-12-16
I want to introduce you to an amazing little program called pdf2svg!

It's saved my *** many times.

First of all get the program;

sudo apt-get install pdf2svg
AND
sudo apt-get install inkscape

Next identify the filepath to your original file or cd to the right directory using your terminal.

Then in your terminal;
pdf2svg "Original_File.pdf" "New_File_Name.svg"

The conversion is complete - type;

inkscape "New_File_Name.svg"

Now you can edit the pdf to your hearts content and when your done - in the Inkscape menu - just export as pdf again.

It's a solution - maybe not the best but it will work.
:)

---

