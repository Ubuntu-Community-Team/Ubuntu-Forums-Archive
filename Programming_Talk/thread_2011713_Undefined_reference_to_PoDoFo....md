---
title: "Undefined reference to PoDoFo::..."
date: 2012-06-27
forum: Programming Talk
---

### Post by JeyPeyy on 2012-06-27
I'm trying to do a program that will read the visual pdf's we get from work with our schedule on it, and give a file in the icalendar or csv format (or some other format if my friends asks for it) so we can sync it with our calendars (eg google calendar). I've looked for libraries that parse pdf's and the best one so far seems to be [PoDoFo]("http://podofo.sourceforge.net/index.html"). So I installed the libpodofo-dev package from the default repositories.

I have podofo/base/PdfParser.h and podofo/base/PdfVecObjects.h included, but it seems like the linker can't find the object. I get these error messages:

> main.cpp:(.text+0xaf): undefined reference to PoDoFo::PdfVecObjects::PdfVecObjects()'
main.cpp:(.text+0xc7): undefined reference to `PoDoFo::PdfParser::PdfParser(PoDoFo::PdfVecObjects*)'
collect2: ld returned 1 exit status



Here's (parts of) my code:
```

#include <QFileDialog>
#include <podofo/base/PdfParser.h>
#include <podofo/base/PdfVecObjects.h>

[...]

void readPDF(QFile file)
{
    PoDoFo::PdfVecObjects *pdfVecObject = new typename PoDoFo::PdfVecObjects::PdfVecObjects;
    PoDoFo::PdfParser *parser = new typename PoDoFo::PdfParser::PdfParser(pdfVecObject);
[...]
}
```

I'm pretty sure the rest of the code has nothing to do with it.

I use Qt Creator and I haven't changed the compiler flags

---

### Post by trent.josephsen on 2012-06-27
You need to add linker flags to link in the libraries you're using. Try running `pkg-config --libs podofo`.

---

### Post by JeyPeyy on 2012-06-28
> **trent.josephsen said:**
> You need to add linker flags to link in the libraries you're using. Try running `pkg-config --libs podofo`.

> Package podofo was not found in the pkg-config search path.
Perhaps you should add the directory containing `podofo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'podofo' found


I've searched for podofo.pc but I don't have such a file.

---

### Post by trent.josephsen on 2012-06-28
Sorry, I've never heard of PoDoFo before so I can't guess what flags you might need. If you can compile their official "hello world" example, then maybe the Makefile could tell you. Else maybe you could ask on their mailing list, since there seems to be a gap in the project documentation.

---

### Post by JeyPeyy on 2012-06-28
> **trent.josephsen said:**
> Sorry, I've never heard of PoDoFo before so I can't guess what flags you might need. If you can compile their official "hello world" example, then maybe the Makefile could tell you. Else maybe you could ask on their mailing list, since there seems to be a gap in the project documentation.

I had some problems compiling the hello word example, but when I found out I needed to put -lpodofo as a flag to g++ I understood I had to put "LIBS += -lpodofo" in my .pro file (because qt creator uses qmake).

Thanks and have a great week-end

---

