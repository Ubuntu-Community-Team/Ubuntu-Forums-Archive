---
title: "Foxit PDF Editor"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by hifly1231 on 2008-11-29
When I was using Windows XP, I had Foxit PDF Editor.  I was able to type in forms using the "Typewriter" function and print out instead of printing and filling out the form by hand.  Is there anything comparable to this in the Ubuntu 8.10 repository, or anything that anyone knows of that would work this way?  Thanks!!!

---

### Post by NewJack on 2008-12-01
I believe PDFedit is in the repos.  I do not believe that FoxIt works on Linux.

---

### Post by spoonernash on 2009-01-17
Just downloaded a Linux version. Have not tried it yet.

Updated: posted too soon, further reading here indicates that Foxit for Linux is broken.

---

### Post by zerubbabel on 2009-01-17
pdf-Xchange is an excellent pdf editor that runs fine under Wine. It's not free, but it's inexpensive and being actively developed. You can find it at: [http://www.docu-track.com](http://www.docu-track.com)

---

### Post by expatCM on 2009-01-18
I think Sun are / were working on an extension to allow the basic edit of a pdf in Open Office.  You may want to take a look round ....

---

### Post by Takmadeus on 2009-01-18
Go for PDFedit, it's the most powerful pdf edityor I have found in linux

---

### Post by spoonernash on 2009-01-18
I work with fill-in form pdfs a lot. I just need to be able to enter text in the fields. Adobe is the only one I know of at this time for doing this. I wish there was something else. eVince is nice and quick for just viewing pdfs, but it does not do form entry.

---

### Post by luigi_mb on 2009-02-02
I just discovered an interesting piece of software, **Ghostview-Markup**:

[http://ocho.uwaterloo.ca/~pfieguth/Software/Ghostview/ghostview.html](http://ocho.uwaterloo.ca/~pfieguth/Software/Ghostview/ghostview.html)

a) download the **binaries** archive, and unpack it in an empty folder, say ~/gv_mod

b) convert your .pdf file to .ps using **pdftops**

c) cd ~/gv_mod && ./ghostview

d) open your .ps file in ghostview and edit the form fields

e) "save as PS" the file with your edits

f) convert the .ps file back to .pdf using **ps2pdf**

The Ghostview-Markup's interface is rather ragged, and the version of Ghostview/Ghostscript is quite old, but it worked beautifully on my system (Ubuntu 8.10). 

/luigi_mb

---

### Post by nortexoid on 2009-04-04
Foxit PDF Editor works just fine under Wine. The program runs from a single file.

---

### Post by Ben Crisford on 2009-04-04
I use Scribus as a PDF editor and it works great for me. :D

---

### Post by jamesrfla on 2009-04-04
Where you can get foxit reader [http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by spcwingo on 2009-04-04
You can also use flpsed.  It's in the repos.  It won't allow you to change what's already there, but will allow you to fill in forms, etc.

---

### Post by castawaybcn on 2009-05-12
> **hifly1231 said:**
> When I was using Windows XP, I had Foxit PDF Editor.  I was able to type in forms using the "Typewriter" function and print out instead of printing and filling out the form by hand.  Is there anything comparable to this in the Ubuntu 8.10 repository, or anything that anyone knows of that would work this way?  Thanks!!!
I recently found the only (that I know of) native gnu/linux option to **fully** (and comfortably) edit pdf files is [PDF Studio]("http://www.qoppa.com/psindex.html"), not free but at a quite low price.

---

### Post by XCan on 2009-05-12
I think ubuntu really lack a good alternative for Acrobat Pro (yes it's bloated to death, but it's easy to use). Despite the capabilities of PDFEdit, I found it very counterintuitive with very messy menus. For single page PDFs, I usually just import the PDFs into Inkscape and do the editing there.

---

### Post by Cheesemill on 2009-05-12
Unless I'm very much mistaken you can fill in PDF forms using Adobe Reader.
I know it's not open source but it is free (money) and it has the best PDF compatibility of any program I've tried (obviously :)).

Cheesemill

---

### Post by lykwydchykyn on 2009-05-12
okular has some support for forms, but it seems buggy.  Adobe Reader is the only reliable program for this that I know of.

---

### Post by andyprough on 2009-05-23
I've got Foxit PDF Editor running under Wine in Ubuntu - no problem.

---

### Post by 3L33T on 2009-12-29
FoxitPDF Editor version 2.1 DOES NOT install in WINE 1.0.1 on Ubuntu 9.10.

During wine install, i'm getting the following errors:

```

   fixme:xrender:X11DRV_AlphaBlend not a dibsection

   err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\temp\\fox9ea.tmp\\PDFSetup.exe") not found

err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\fox2275.tmp\\PDFSetup.exe" failed, status c0000135 

```

Can anyone help?

---

### Post by 3L33T on 2009-12-29
NEVER MIND...I found the simple solution here:  

[http://bit.ly/57SoPZ](http://bit.ly/57SoPZ)

---

### Post by gauravm on 2010-07-27
If all you wish to do is add to a pdf file (as in filling a form) then the best software I have found for that purpose is xournal. You can open a pdf via "File --> Annotate PDF" and then add to it whatever you choose and then "File --> Export To PDF" or "File --> Print"

This is awesome with a tablet because essentially it has negated my need to ever print anything that I need to then scan back to email! Good for trees!

---

### Post by drfox on 2010-09-27
I've tried Foxit PDF editor, but whenever I try to import an image, it crashes. PDFEdit takes up 100% of my cpu, and flpsed just doesn't work well for me. If you're just looking to type on a PDF, try Xournal (in the reps). Xournal is a much better Linux-native PDF editor for typing (just import the PDF into Xournal and press F8 to get into typewriter mode). If you want complete PDF editing in one application, Qoppa's PDF Studio--a commercial app--is the way to go. You can add your signature or other image "stamps," rearrange add or delete pages, attach other files, etc, etc. [www.qoppa.com](www.qoppa.com)
Larry

---

### Post by n.l.o on 2011-02-08
I had a similar problem, you can usually fill in forms with either evince or xournal. but I had now way of adding my signature, just fill in, print out, sign, scan to pdf.

Sooo, I signed a paper, scanned it to pdf, imported it to inkscape, traced paths and created a svg. popped the svg into fontforge, created my own font. all programs in std repos.

now I can put my signature into pdfs too, with my own font!

Cheers,
Magnus

---

### Post by Loan_Refi on 2011-03-04
I use Foxit PDF Editor (Phantom) version, I use it cause I work for a Mortgage Co. and most importantly for personal use.

I have used Adobe Acrobat Professional but its too expensive.

I now use Foxit Phantom

I use Ubuntu 10.10 95% of the time so I'm using Foxit Phantom with Wine. I also have Adobe Acrobat installed but won't run in Wine.

I use Foxit to sign any documents with my actual signature which I scanned then made the background transparent with Gimp. Whatever I sign looks as if I had signed it by hand and THEN scanned. I created a custom stamp.

Other functions I use;

Insert, Extract and Delete Pages
Typewriter, TouchUp objects tool which is better than the typewriter
Note Tool

Basically Foxit under Wine runs great with all the features and is a lot faster than Adobe Acrobat, Evince, Adobe Reader.

---

### Post by beew on 2011-03-04
> **jamesrfla said:**
> Where you can get foxit reader [http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)


Foxit reader for Linux is dead. Check out their forums. The Linux version is very primitive comparing to the Windows version. When 10.04 came out last april the only advantage of Foxit over evince was speed and smooth rendering but since 10.10 evince has caught up and has more functions. Okular is a lot more capable in terms of functionality.

BTW Foxit Linux doesn't even render its own manual correctly, if you open the Foxit manual all you see is gibberish. 

I really see no point in using Foxit, I used it for a few months because evince in 10.04 was terribly slow (little did I know that it was an outdated version because of Ubuntu repo freeze), but I dumped it as soon as I get an updated version from Maverick's repo.

I am quite pissed off with Foxit actually,  it is quite insulting for Foxit to offer Linux users a vastly substandard product comparing to Windows and then when people asked for similar features they flatly said they wouldn't be implemented (so it is not the case that the Linux version was primitive just because of early development)  Then after they killed it they don't even have the courtesy to tell you.

---

### Post by rewyllys on 2012-03-09
I can recommend PDF Studio Pro as an excellent PDF editor for Linux.  It's not free, but I found the price well worth it to me.

You can take a look at it at:

[http://www.qoppa.com/pdfstudio/index.html]("http://www.qoppa.com/pdfstudio/index.html")

---

### Post by oldos2er on 2012-03-09
Closed, necromancy.

---

