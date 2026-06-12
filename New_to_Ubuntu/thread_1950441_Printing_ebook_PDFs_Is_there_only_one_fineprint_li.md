---
title: "Printing ebook PDFs: Is there only one fineprint like utility for Ubuntu users?"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-03-31
Q: [COLOR=DarkRed]**Is there only one fineprint-like utility for Ubuntu users?**[/COLOR]

It's useful to be able to "imposition" print ebook PDFs (e.g., the 150-page [Ubuntu Pocket Guide & Reference]("http://www.ubuntupocketguide.com/index_main.html"))  to standard double-sided US "letter" (8 1/2 x 11) paper, which can then  be cut in half and then bound by the standard "perfect binding" method,  to create a home desktop published 5.5-inch wide by 8.5-inch tall handy  paperback.

On Windows, there is a great imposition utility  called "Fineprint" which will print that 150-page ubuntu PDF,  double-sided, two pages per side of 8.5x11 paper with imposition  sufficient for folding in half to make a booklet or for cutting in half  to make a book.

Note: 

[LIST]
[*]Booklet Imposition (no cutting, folded in half lengthwise & centerline stapled)
[LIST]
[*]The  first and last pages are printed on one side of a standard "letter"  sheet of paper, with the second and penultimate page on the other side  of that same sheet of paper.
[*]This first/last second/penultimate relationship follows for every sheet of paper until it meets in the middle
[*]The printed stack of paper is then folded in half (lengthwise)
[*]And lengthwise staples are placed in the crease to 'bind' the booklet
[*]The result is a 8.5" tall by 5.5" wide stapled booklet
[/LIST]
[*]Book Imposition (cut in half widthwise & bound at the inside edge)
[LIST]
[*]The  first and middle page is printed on one side of a standard "letter"  sheet of paper, with the second page and middle-of-the-book+1 page  printed on the other side of the sheet of paper.
[*]The printed stack of paper is then cut in half (widthwise)
[*]And then the two stacks are bound together in a 'perfect binding'
[*]The result is a 8.5" tall by 5.5" wide bound paperback book
[/LIST]
[/LIST]
QUESTION:
[COLOR=DarkRed]**Is there a similar utility for Ubuntu users?**[/COLOR]


Note: I searched, but all I found (so far) was the 'fp' & "fprint" shell scripts as shown below: 
[B]* [fp - a Linux FinePrint-like utility to duplex print .ps files into A5 booklets]("http://ubuntuforums.org/showthread.php?t=244715&highlight=fineprint")

[/B]But  I was hoping for a bona-fide program with a GUI that we can simply  install and run without having to edit shell scripts (as I'm a relative  beginner to Ubuntu).

---

### Post by Laobi on 2012-04-01
Try [jPdf Tweak]("http://jpdftweak.sourceforge.net/"), it can do imposition and has a GUI.  It is a Java application.

---

### Post by rocksockdoc on 2012-04-02
> **Laobi said:**
> Try [jPdf Tweak]("http://jpdftweak.sourceforge.net/"), it can do imposition and has a GUI.  It is a Java application.

Very nice find! 

It's not in the Ubuntu Software Repository unfortunately (so nobody will find it without knowing exactly what to look for on the net).

Since I never seem to be able to compile, I downloaded the precompiled Linux x86 binary ([Binary download, Linux x86 version]("http://prdownloads.sourceforge.net/jpdftweak/jpdftweak-linux-x86-1.1.zip?download")), which seems to have in the README these instructions to run it:

```

This program requires Java 5 or higher. Download it from java.sun.com. 
Start it by double clicking the jar file, or by 
java -jar jpdftweak.jar 

```

Doubleclicking the "jar" file on Ubuntu only brought up the "File Roller 2.30.1.1" Ubuntu Archive manager, so, something went wrong somewhere.

So I executed the java file directly from a terminal window after checking my java version...

[COLOR=DarkRed]QUESTION: Do I read results below correctly that I have the wrong version of Java?[/COLOR]
```

**$ which java**
REPORTED: 
/usr/bin/java
**$ java -version**
REPORTED: 
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.13) (6b20-1.9.13-0ubuntu1~10.04.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)
**$ java -jar jpdftweak.jar**

```

This brought up the JpdfTweak 1.1 GUI.

I'll see what I can do to get it to print doublesided two-pages-per-sheet-side book and booklet imposition pages!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215347&stc=1&d=1333422237[/IMG]

---

### Post by jerome1232 on 2012-04-03
> **rocksockdoc said:**
> 
[COLOR=DarkRed]QUESTION: Do I read results below correctly that I have the wrong version of Java?[/COLOR]


Yes and no, you are using (as most Ubuntu users will be using) openjdk, an open source implementation of java, it works pretty well, and should be sufficient.

However...
If you find it's not running your java progams well you can always install oracles java, it's a bit of a pain, and won't get automatic updates via your package manager... but if you need it you need it. [http://www.java.com/en/](http://www.java.com/en/)

The reason it's not provided via that repositories anymore (it once was) is because they changed their licensing and we aren't allowed to distribute it that way now.

---

### Post by rocksockdoc on 2012-04-03
> **jerome1232 said:**
> you are using (as most Ubuntu users will be using) openjdk, an open source implementation of java

Ah. I see. I had no idea. Thanks for cluing me in. 

I guess that explains why the jPDKtweak program actually came up when I executed it from the terminal (using the command "java -jar ./jpdftweak.jar").

Since the jPDKtweak GUI did come up, can I assume the Ubuntu default "java version 1.6.0_20" may be 'equivalent' to the README-implied "This program requires Java 5 or higher"?

---

### Post by Cheesemill on 2012-04-03
The Java version numbering has always been a bit strange:

Java 5 = Version 1.5
Java 6 = Version 1.6
Java 7 = Version 1.7

When jPDF Tweak says it requires version 5 or higher, that refers to 1.5 or up.

---

### Post by rocksockdoc on 2012-04-04
> **Cheesemill said:**
> When jPDF Tweak says it requires version 5 or higher, that refers to 1.5 or up.

Thank you for that helpful clarification! I see the relationship now. 

BTW, googling for all the options, I found this home-grown booklet imposition method in the NNTP USENET newsgroups:

> **peter]

I do booklet imposition with PDFs generated by LaTeX, in two stages:

1) I do some measurements on the paper thickness, so I can set an adjustment so that the text area in a 32pp signature gradually moves back towards the spine for pp1-16 and then back towards the foredge for pp17-32. This compensates for the offset caused by the folding.

2) Having typeset the PDF, I use a shell script something like the one below to create the signatures. pstops is your essential friend here: it rearranges the order and orientation of pages in a Postscript file.

```
# get the number of pages output
PP=`grep "Output written on $DOC.pdf" $DOC.log | awk '{print $5}' | tr
-d '('`
# set the size of a signature
SIG=32
# how many integral signatures
SIGS=$[PP/SIG]
# how many pages they take
PG=$[SIGS*SIG]
# what's left in the document
LAST=$[PP-PG]
# how many blank pages needed
FILL=$[SIG-LAST]
# add blank pages if required by adding dummies to the .tex file
if [ $FILL -gt 0 -a $FILL -ne $SIG ] said:**
> 
COUNT=0
while [ $COUNT -lt $SIGS ]; do
    START=$[COUNT*SIG+1]
# generate a SIG's-worth as Postscript
    dvips -p =$START -n $SIG -o $DOC.ps $DOC.dvi
# calculate the offsetting
    IMP=`echo|awk -v s=$SIG -f impose.awk v=27 hl=-3 hr=12 thk=.1`
    SEQ=`echo $COUNT | awk 'BEGIN {ORS=""} {c=$1+1;if(c<10)print
"0";print c}'`
# use pstops to rearrange things
    pstops -pa4 -b "$IMP" $DOC.ps | ps2pdf - $DOC-sig$SEQ.pdf
    COUNT=$[COUNT+1]
done
```The syntax of the awk script is left as an exercise to the reader 

I then pass the signatures to my local craft bookbinder, who sews them and cases them in.

///Peter


---

### Post by rocksockdoc on 2012-04-05
For the record, I found the following book/booklet imposition printing utilities, all of which impose on the Windows platform, only some of which impose for Linux:

[LIST]
[*][A-PDF N-up Page]("http://www.a-pdf.com/n-up-page/")
[*][ClickBook MMX]("http://www.bluesquirrel.com/products/clickbook/")
[*][Bookletizer]("http://visionsedge.com/XTensions/index.asp?id=bookletizer")
[*][InDesign Imposition Plug-In]("http://www.impositionsoftware.com/")
[*][PDF Imposition DE (Desktop Edition)]("http://www.traction-software.co.uk/pdfimpositionde/index.html")
[*][PDF Snake]("http://www.pdfsnake.com/")
[*][Quite Imposing]("http://www.quite.com/imposing/")
[/LIST]

---

