---
title: "Java and OpenOffice files"
date: 2009-12-05
forum: Programming Talk
---

### Post by mediax on 2009-12-05
I have an idea for a little project that involves manipulating and converting files saved in OpenOffice writer format.

I'm going to be studying Java next year, so rather than look to do the coding in OpenOffice Basic (or Python, or whatever), I thought this might make a Java learning exercise.

That said, I'd prefer not to completely reinvent the wheel, so if anyone can point me in the direction of any Java applets or code samples to help with opening and reading OpenOffice writer files, I'd be grateful.

TIA

---

### Post by dhillonv10 on 2009-12-26
Hope this helps:

1. [http://wiki.services.openoffice.org/wiki/Java_and_OpenOffice.org](http://wiki.services.openoffice.org/wiki/Java_and_OpenOffice.org)

2. [http://api.openoffice.org/](http://api.openoffice.org/)

3. [http://java.dzone.com/news/integrate-openoffice-java](http://java.dzone.com/news/integrate-openoffice-java)
:guitar:

---

### Post by MaxIBoy on 2009-12-26
This could help get you started: ODT files are just renamed .zip archives, with some xml files and a few other things included. So any programming languages with XML, image manipulation, and zip opening libraries (basically any programming language) will do.

There are more specialized libraries for OpenDocument files as well. There are such libraries available for Python, PHP, and Java:
[http://opendocumentfellowship.com/projects/odfpy](http://opendocumentfellowship.com/projects/odfpy)
[http://opendocumentfellowship.com/projects/odfphp](http://opendocumentfellowship.com/projects/odfphp)
[http://www.jopendocument.org/](http://www.jopendocument.org/)

I haven't tried any of them so I can't tell you how good they are, sorry.

---

### Post by mediax on 2009-12-27
Thanks dhillonv10 and MaxIBoy, that's exactly the sort of thing I was after

---

