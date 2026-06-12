---
title: "New to ubuntu.. looking for recommendations for PDF print software"
date: 2021-11-23
forum: New to Ubuntu
---

### Post by mjetrying on 2021-11-23
Hi all, I'm new to ubuntu, researching the various alternative software solutions for the things I do. I've found most but I'm looking for recommendations for PDF print and merge software.

I regularly print to pdf and merge with a pdf letterhead from word and excel etc and in windows used both PDF Factory Pro and Bullzip PDF Printer. (The former has the option to select a letterhead and the latter has the option to add the letterhead as a background.)

alternativeto.net suggested CUPS-PDF but I've not been able to find much information on it. Any thoughts on that or other/better suggestions greatly appreciated...

---

### Post by TheFu on 2021-11-23
I don't do the same type of processing of PDF stuff that you do. 

CUPS has a print driver for PDF files.  That means we can throw nearly any PDF file to CUPS and let it handle printing, just like we can throw postscript files.
CUPS is the printing systems on Unix.  There is a printer driver for generic PDF.
Run 
$ system-config-printer
and add a PDF printer, if you want to output PDF.  **LibreOffice** can open most PDF files, then you can place the pages in whatever order you like and directly print to PDF.  LibreOffice is a replacement for MS-Office for most people.  Of course, if using custom features or scripting of MS-Office, those won't work in LibreOffice.  MS-Office can output the native file formats for LibreOffice, though fonts and pagination is almost always different.

I recall there was a thread here about manipulating PDF files  sometime in the last 6 months where a few GUI tools were listed. If you search for my username and PDF, there shouldn't be too many threads.

I'm a server guy, so I don't really merge PDF files using a GUI.   To merge PDFs I use a little alias:
```
alias pdf-merge='gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile='
```
To use it, 
```
$ pdf-merge myOutput.pdf someotherPDFs5.pdf  someotherPDFs1.pdf someotherPDFs7.pdf someotherPDFs42.pdf someotherPDFs99.pdf
```
If the input files are alphabetic order, I can use "file globbing" which is part of the bash shell 
```
$ pdf-merge myOutput.pdf someotherPDFs*pdf
```
beware, alphabetical order and numerical order aren't the same.  

*gs* is the ghostscript program.

Definitely look for that other thread.
Just so you have more stuff to look at - though I don't think they directly relate: pdftk, Okular,  evince, atril are some terms to search.  pdftk is an light-GUI into command line PDF tools on Linux. I think it has been replaced by something else, but don't know what that replacement is. Sorry.

---

### Post by rsteinmetz70112 on 2021-11-23
PDFSAM will merge PDFs. I use it in WIndows but it's availible for Linux. I use it append multiple PDFs into larger documents. I don't know if it will do what you want.
To create a letterhead I create a letterhead template (.ott) in Libre Office then write in the letterhead and save it as PDF or odt. The .ott file will normally save as an .odt file in a new document, the ott will remain unchanged.

There are a lot of PDF tools for Linux, many are not free. Many packages allow you to "merge" PDF files, but usually that means appending files. To do what you described above it sounds like you are overlaying one file on another.

---

### Post by ActionParsnip on 2021-11-23
Press print in any application and you should have a PDF printer available. This will make a PDF for you

---

### Post by LokiScarlet on 2021-11-24
LibreOffice is a good replacement for MSOffice. Writer is for documents, Calc is for spreadsheets, and when you're editing something that's already a PDF, you can use Draw, the vector graphics editor.
Moreover, as a software suite, if you try to open something in Writer that belongs in Draw, it'll just open it in Draw for you. To give you an idea of how Draw works, it's like Adobe Acrobat (the editor, not the reader) but free and, in my opinion, better.

---

### Post by mjetrying on 2021-12-01
PDFtk / PDFChain provided my solution. Print one document with another set as a background

---

