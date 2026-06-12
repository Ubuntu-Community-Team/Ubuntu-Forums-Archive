---
title: "Excel in C or C++"
date: 2009-01-28
forum: Programming Talk
---

### Post by StOoZ on 2009-01-28
is there any API to read + write xls (not csv...) files ???

---

### Post by Zugzwang on 2009-01-28
Deja Vu? You already asked this question last month:

[http://ubuntuforums.org/showthread.php?t=999820&highlight=excel]("http://ubuntuforums.org/showthread.php?t=999820&highlight=excel")

Anything missing in the answers?

---

### Post by StOoZ on 2009-01-28
I couldnt figure out how to strip the code from OO.
I wonder , how come there are API's to do it in perl , but not in C / C++?

---

### Post by Zugzwang on 2009-01-29
> **StOoZ said:**
> I couldnt figure out how to strip the code from OO.
I wonder , how come there are API's to do it in perl , but not in C / C++?

Dunno. Maybe no one every saw the need to write one? Or, in this language, people are normally interfacing Excel via COM calls in Windows directly.

You could make a Perl/Python/Java command line application using one of the respective implementations to modify the XLS files (some kind of interpreter) and interface it from your C++ program.

---

### Post by cl333r on 2009-01-29
[http://www.libexcel.com/](http://www.libexcel.com/)

[http://mac.softpedia.com/get/Development/Libraries/xlsLib.shtml](http://mac.softpedia.com/get/Development/Libraries/xlsLib.shtml)

[http://members.wibs.at/herz/xlsstream/www/index.html](http://members.wibs.at/herz/xlsstream/www/index.html)

---

