---
title: "PDF files don't display certain characters"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by baruch60610 on 2011-10-10
I've got Natty Narwhal with KDE.  When I try to display certain PDF files, some of the technical symbols don't display properly.  For instance, the character for degrees, the Greek omega (for ohms), the Greek mu (for micro-) don't show properly.

This happens in Evince, Okular, and something else (I forgot which).  The XPDF reader doesn't even start - it just bombs immediately.  Oddly enough, I do get the symbols when I use ghostview, which is an otherwise sucky program.

Can anyone suggest why I'd get this strange result, and more important, what could I do to fix it?  Do I need to download some sort of font set or something?  Any ideas??

Thanks.

---

### Post by hyper2hottie on 2011-10-10
Have you tried using Adobe pdf reader?

---

### Post by baruch60610 on 2011-10-10
Actually I thought of that, but it doesn't show up in Synaptic.  I've seen it before, but for some reason it's gone now - and not installed on my system, either...

---

### Post by NikoC on 2011-10-11
sudo apt-get install acroread

That might do the trick!

---

### Post by An Sanct on 2011-10-11
You also might need the "non-free" fonts from MicroSoft...

---

### Post by Johnb0y on 2011-10-11
> **An Sanct said:**
> You also might need the "non-free" fonts from MicroSoft...
 
+1 might do... also

```
sudo apt-get install acroread
```

also if you wish...

> sudo apt-get install acroread mozilla-acroread acroread-plugins


if that fails... try: [this ]("http://www.liberiangeek.net/2011/04/how-to-install-adobe-reader-acroread-in-ubuntu-11-04-natty-narwhal/")for Adboe install using software repo

hope that helps! :D

---

### Post by beew on 2011-10-11
I have lots of pdfs with mathematical symbols and I don't have a problem viewing them, so I think your difficulty is due to formating in one or a few such documents and it is not a wide spread phenomenon ( I have a few documents like that out of hundreds) 

Installing acroread to read just one document seems to be an overkill as it is a complete resource hog, I avoid it as much as possible. I don't even use Adobe in Windows, it is huge resource waster and is mostly unnecessary.

Though not an advocate of WINE in general, but I would rather install pdf-xchange viewer in WINE and see if it helps before going for Acroread.


BTW, if you must use Acroread it is in the Canonical's partners repo and you have to enable it before it would show up in Synaptic,--and if is not enabled sudo apt-get would not find it either.

---

### Post by An Sanct on 2011-10-11
> **beew said:**
> I have lots of pdfs with mathematical symbols and I don't have a problem viewing them, so I think your difficulty is due to formating in one or a few such documents and it is not a wide spread phenomenon ( I have a few documents like that out of hundreds)

Would it be possible (by any of you) to upload such a PDF or giving us a link to one? (As long as it does not contain any privileged and/or sensitive data, of course...)

Reading math filled PDFs is surely going to go okay on a computer of a person with math interest, as he has most of the needed fonts preinstalled.

PS2. Fonts can be embedded or linked. If they are embedded, then it is a parsing error. If they are not (they are linked) then fonts are missing and you get to see a "fallback" font like Arial or something like that with special characters missing (or replaced by something).

---

