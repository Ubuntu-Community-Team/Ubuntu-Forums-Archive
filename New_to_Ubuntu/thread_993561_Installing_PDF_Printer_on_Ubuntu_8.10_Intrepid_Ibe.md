---
title: "Installing PDF Printer on Ubuntu 8.10 Intrepid Ibex"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by hifly1231 on 2008-11-25
I'm not the most knowledgeable regarding computers, but I've almost completely successfully made the transition from Windows to Linux (yeah!!!).  But I cannot figure out how to install cups-pdf and get the printer to save the PDF's!  Could someone please tell me how do this step-by-step from the beginning?  I would greatly appreciate it!!!  **_I'M_** **_DESPERATE_****!!!** :confused:

---

### Post by binbash on 2008-11-25
sudo apt-get install cups-pdf

---

### Post by AndrewTheArt on 2008-11-25
I was under the impression that this functionality was built-in to Ubuntu (no need to install anything additional)

(1) Press File -> Print
(2) Select "Print to File" as the printer
(3) Name the file next to "Name:"
(4) Select the folder to output the file next to "Save to folder:". Default is your home dir.
(5) Select "PDF" next to "Output format:"
(6) Print!

---

### Post by hifly1231 on 2008-11-25
> **AndrewTheArt said:**
> I was under the impression that this functionality was built-in to Ubuntu (no need to install anything additional)

(1) Press File -> Print
(2) Select "Print to File" as the printer
(3) Name the file next to "Name:"
(4) Select the folder to output the file next to "Save to folder:". Default is your home dir.
(5) Select "PDF" next to "Output format:"
(6) Print!

AndrewTheArt,

**I CANNOT THANK YOU ENOUGH!!!**  I have **_searched_** and **_searched_** today, I've tried to install cups-pdf exactly as instructed and get it to work, and here it was already pre-installed on my Ubuntu 8.10 Intrepid Ibex, and works **_PERFECTLY_**!!!  Thank you **_SO_** **_MUCH_** for responding to my post!!!  It's people like you that keep me from giving up and going back to Windows XP!!! :KS

Very Sincerely,

Mark in Cincinnati

---

### Post by stoogiebuncho on 2008-11-25
If you are using open office, there's a button on the toolbar that will convert the document or spreadsheet or whatever to a pdf, with a lot less hassle than trying to print to a file.

I suppose if you're trying to convert pictures to pdfs, it might be handy to have that print to option, but you could always paste the picture into an Open Office document and save it as a PDF.

Do what you prefer, of course.  Just wanted to let you know of another way of doing it. ;)

---

### Post by hifly1231 on 2008-11-26
> **stoogiebuncho said:**
> If you are using open office, there's a button on the toolbar that will convert the document or spreadsheet or whatever to a pdf, with a lot less hassle than trying to print to a file.

I suppose if you're trying to convert pictures to pdfs, it might be handy to have that print to option, but you could always paste the picture into an Open Office document and save it as a PDF.

Do what you prefer, of course.  Just wanted to let you know of another way of doing it. ;)

Thanks!!!  You guys are AWESOME!!! \\:D/

---

### Post by gandaran on 2008-11-26
if you install cups-pdf you have to make a **PDF** folder on your home directory or it wont work, all pdf's are printed to this folder
you can even set the PDF printer as default system printer, it's better than choosing all the time 'print to file' option.

---

### Post by AndrewTheArt on 2008-11-26
[QUOTE=My PM to hifly]a) Glad to help! Ubuntu is awesome. Glad you're having a good experience on the forums.

b) There doesen't seem to be a good way to set a default besides what is given. You could make a script that runs in the background and moves files from the default location to your Documents folder every x minutes or seconds, I guess. If you're interested in that, PM me back and I'll see what I can do. 

Andrew[/QUOTE]

-

---

### Post by Loan_Refi on 2008-12-01
Is there a way to change the margins to PDF output?  

I mean I can do it in internet explorer but I would like to reduce the margins when using cups-pdf.

Does anyone know how to change the margin size?

Thanks!

---

### Post by Ark_74 on 2009-01-19
> if you install cups-pdf you have to make a PDF folder on your home directory or it wont work

It is weird but true :P

---

### Post by carwinz on 2009-02-17
Is there a way to change the defaults for the Postscript/PDF printer which is installed by default in 8.10 (the one described by AndrewTheArt) ?

I want to set the default directory and get it to generate a pdf by default instead of a postscript file.

Also, is there a way to set this printer as the default?

---

### Post by MarkieB on 2009-09-07
no longer participating in ubuntuforums.org

---

