---
title: "Converting PDF file to text file"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by mark allyn on 2014-01-10
Hello everyone,

I have a very large PDF file containing pricing information for a manufacturer.  I want to do some statistical processiong of these data.  I need to convert, I believe, the pdf to a text file so that I can do further processing.  Could someone suggest a program that would do the conversion for me.  I'll do the downstream processing in C to extract specific fields from the converted file.

Alternatively, there may be a package that I don't know about that could read the pdf into a database and I could do the extraction of what I need from there.

I'm open to either route or some other.

Thank you.

Mark Allyn

---

### Post by monkeybrain20122 on 2014-01-10
What software do you use for statistical analysis? You may be able to import it to R
[http://stackoverflow.com/questions/9185831/reading-data-from-pdf-files-into-r](http://stackoverflow.com/questions/9185831/reading-data-from-pdf-files-into-r)

**Edited: **Ok Just discovered that I have this thing called pdftotext, which is already installed with poppler-utils from the repository. But you should study the options, I tried it on the sample data from the link (with no option) it converted but the formatting is really messed up.

---

### Post by Buntu Bunny on 2014-01-10
In the Ubuntu Software Centre there is Able2Extract. It converts PDFs to Calc, Writer, Impress & more, so perhaps it would be of help. 

There's an online converter [here]("http://convertpdftotext.net/"), although I've never tried it.

---

### Post by SeijiSensei on 2014-01-10
I've sometimes had success using copy and paste from a PDF displayed by [Okular]("http://okular.kde.org/").  If you highlight a section of a document in Okular and pick copy/cut, you can choose whether the resulting object is a graphic or text. Sometimes I've found that I can choose text and copy the document into a spreadsheet. I've had varying success with this method; I guess it depends on how the PDF was created.

Okular is the default KDE viewer for PDF files; you can install it from the repositories with "sudo apt-get install okular".

---

### Post by mark allyn on 2014-01-11
Good morning Buntubunny, Seijisensei, and monkeybrainxxxx,

Thanks for the suggestions.  I haven't followed up on them yet, but will do so as soon as I am able.  To answer a couple of questions:

1.  The file is 951 PDF pages long with approximately 100 elements per page, so the cut/copy/paste approach is perhaps basically unworkable--at least in my arthritic hands.
2.  The analysis would most likely be done by using Octave or GSL  with my own custom code.  I am familiar with R and I know it has many virtues, but I have never gotten comfortable with its syntax.

I'll try the apps you have suggested.  Several look promising.  I'll let you know what happened.

Meantime, many thanks,

Mark

---

### Post by mark allyn on 2014-01-11
Hello everyone,

OK, I tried several of your suggestions and here's what I found.

1.  pdftotext works.  You have to set the right options, but it will do the job and create a text file.  I'm going to have to parse the file rather carefully in order to pull out the prices from other ordering info but that should be fun.  Good old strtok... or grep...or sed.
2.  Able2extract choked.  I'm supposing the file size was too big for it...But, I can test this easily enough.  BTW, this app charges you after a 7 day trial period.  
3.  The online converter is for Windows, not linux or unix or anything else other than msft.

So, thanks folks and I think we can wrap this thread up unless you have something you'd like to add.

Mark

---

