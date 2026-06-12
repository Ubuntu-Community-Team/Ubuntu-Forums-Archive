---
title: "glade3 generate perl code?"
date: 2006-11-09
forum: Programming Talk
---

### Post by slavik on 2006-11-09
I just had an idea about creating wizards to generate portions of xorg.conf files (because I have a small LCD screen which needs weird configuration) and I wanted to use perl with gtk+ (I do not want to use python as I know very little about the language and do not feel confident using it).

is there anything that can generate perl code from glade3 files?

---

### Post by ansi on 2006-11-09
> **slavik said:**
> I just had an idea about creating wizards to generate portions of xorg.conf files (because I have a small LCD screen which needs weird configuration) and I wanted to use perl with gtk+ (I do not want to use python as I know very little about the language and do not feel confident using it).

is there anything that can generate perl code from glade3 files?

Try it: [http://www.glade-perl.connectfree.co.uk/](http://www.glade-perl.connectfree.co.uk/).

---

### Post by slavik on 2006-11-13
that seems to work with glade and glade2 ... I am looking for something that works with glade3

---

### Post by techrolla on 2008-04-19
Now with glade3 there is no more code generation.  Rather, libglade supports loading an XML file and generating an interface from that.  It has bindings for languages like Perl.

---

