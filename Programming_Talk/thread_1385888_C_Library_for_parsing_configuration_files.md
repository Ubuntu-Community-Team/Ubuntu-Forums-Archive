---
title: "C: Library for parsing configuration files"
date: 2010-01-20
forum: Programming Talk
---

### Post by DJ_Cyberdance on 2010-01-20
Hi there,

I'm only doing a little C and I wonder if there are any useful libraries for parsing configuration files? There is something namend libconfig, which obviously is not included in the Ubuntu repositories, at least there doesn't seem to be a C compatible library or the required header-files.

I'm happy to use any other library that can read a simple (not yet defined) configuration file syntax like token=value or sth like that. Write support is not required. It only should be easy to use and possibly be included in the Ubuntu repositories. Also, examples of use would be great but I guess as soon as I have a few clues on which way to go they can easily be googled...

Thanks in advance for any hints on that!

---

### Post by SledgeHammer_999 on 2010-01-20
Hi, I don't know if you use Gtk+ but the glib library(on which gtk depends) has the functionality you ask for. I haven't tested it myself because I discovored it yesterday. Anyway here are some links:
1.[glib docs](http://library.gnome.org/devel/glib/stable/)
2.[ glib-Simple XML subset parser(I don't think you need this solution)](http://library.gnome.org/devel/glib/stable/glib-Simple-XML-Subset-Parser.html)
3.[ Key-value file parser(I think this is exactly what you ask for)](http://library.gnome.org/devel/glib/stable/glib-Key-value-file-parser.html)

---

### Post by hessiess on 2010-01-20
For something simple like this I would be inclined to implement something from scratch. Parsing key-value or CSV data is not particularly difficult. Basically ypu parse into a 2D array, just loop over every character, pushing it into a `horizontal' array element until you find a space/comma/outher separator then start a fresh horizontal array element. When a `\n' character is reached, start a new vertical array element and repeat until the end of the file.

---

### Post by dwhitney67 on 2010-01-20
> **hessiess said:**
> For something simple like this I would be inclined to implement something from scratch. Parsing key-value or CSV data is not particularly difficult. Basically ypu parse into a 2D array, just loop over every character, pushing it into a `horizontal' array element until you find a space/comma/outher separator then start a fresh horizontal array element. When a `\n' character is reached, start a new vertical array element and repeat until the end of the file.

Starting from scratch might be a good solution, but not as you have outlined.  Repeated calls to fgets(), and perhaps strtok() or sscanf() would be easier.  Reading a file, character by character, should be avoided unless absolutely necessary (and most often it is not).

How to define the container where the data can be stored, and how it can be accessed, is the tricky part.  In C there is no easy way to translate a string token to an index for an array, unless of course, the string token contains the index itself.

For example, with "ITEM_1 = 10", the numeral 1 can serve as the index and the numeral 10 as the value.

---

