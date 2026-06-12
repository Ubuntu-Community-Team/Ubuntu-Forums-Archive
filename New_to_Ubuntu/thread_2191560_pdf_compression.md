---
title: "pdf compression"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by mercuryjets on 2013-12-03
hello,
I have a couple of pdf files I need to reduce in size so that I can email them. I need to send these and some other files in an email that is no bigger than 5mb and I have 2 large pdf files which I don't have the originals for.
I would like to either reduce the pdf file size - it doesn't matter if it looses lots of detail - or compress the files. 
I have tried running some commands about ghostscript but it didn't do anything. I am a total novice about any programming issues and have no understanding of codes and that sort of thing! Having said that I have been happily using ubuntu for 4 years and making use of terminal to follow guides to force install things.
?
cheers

---

### Post by sudodus on 2013-12-03
Welcome to the Ubuntu Forums :-)

You can search the internet for ***pdf compression linux ***and find for example

[http://www.tjansson.dk/2012/04/compressing-pdfs-using-ghostscript-under-linux/](http://www.tjansson.dk/2012/04/compressing-pdfs-using-ghostscript-under-linux/)
and
[http://makingtechnologyeasier.blogspot.se/2013/06/imagemagick-fast-way-to-compress-pdf.html](http://makingtechnologyeasier.blogspot.se/2013/06/imagemagick-fast-way-to-compress-pdf.html)

I have used both methods, and the result varies depending of what kind of pdf file it is.

---

### Post by mercuryjets on 2013-12-03
Thanks,

Yes I saw those two; the 2nd one seems to be referring to re-sizing images in gimp which i do anyway :); the other referes to ghostcript - and this kept coming up in a search i did, but when i tried the gs command it it didn't work. First I got an error which said that it didn't recognise my input file or if i left no space between input and output file name or gave a path for theinput file name it just did not do anything. It is these sorts of commands that I don't really understand!

---

### Post by vanadium on 2013-12-03
- Make sure that your current directory in the terminal is the directory where the PDF resides. It should show in the directory listing (ls). Otherwise, you first need to change the directory to where your pdf is. e.g. , if your PDF is in the Downloads folder, then you need to issue the command "cd ~/Downloads" to change the current directory to "Downloads"
- To make sure you do not have trouble with spaces in the file name, either rename the file (obvious) or surround the file name with "...", e.g. as in
```

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile="output.pdf" "input.pdf"

```

I am still lookiing for a way to flatten a PDF file, which would be another way of compressing some PDF's without visual quality loss.

---

### Post by mercuryjets on 2013-12-03
Hi, Thanks for the reply 
I don't really understand this - Make sure that your current directory in the terminal is the directory where the PDF resides
I can list directories but don't know what this means:
Calibre Library  Downloads         output.pdf  Templates       Videos
Desktop          examples.desktop  Pictures    two.pdf
Documents        Music             Public      two.pdfone.pdf

If if use the command  'cd~/Documents' I get 'bash: cd~/Documents: No such file or directory'

If I copy the target document to other folders in the hope that one of these might be the 'current directory in the terminal' I get an error:
(I don't really understand what errors mean!)

Error: /undefinedfilename in (one.pdf)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1164/1684(ro)(G)--   --dict:0/20(G)--   --dict:77/200(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 9.05: Unrecoverable error, exit code 1

---

### Post by philinux on 2013-12-03
He means open a terminal and change directory to where you files are e.g. cd ~/Downloads if this is where they are. 

Or cd to other directory. Note the space between cd and the ~

---

### Post by mercuryjets on 2013-12-03
Hi and thx,
'Note the space between cd and the ~' :)
(so I have to tell the terminal which folder contains the things I am asking it to work on and it says yep got that)

So now...
GPL Ghostscript 9.05: Set UseCIEColor for UseDeviceIndependentColor to work properly.

?

---

### Post by vanadium on 2013-12-04
You can consider using a service like wetransfer.com, ubuntu one or dropbox to transfer these large files.

---

### Post by VMC on 2013-12-04
I was just today trying to compress a 2mb pdf and found this [link]("http://frankhesse.wordpress.com/2013/05/09/compress-pdf-files-on-linux-using-ghostscript/").
 It went from 2mb down to 246kb! I used both of the scripts listed.

---

