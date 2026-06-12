---
title: "Python code to determine default printer"
date: 2010-10-06
forum: Programming Talk
---

### Post by rlm1964 on 2010-10-06
All,

I have several ubuntu boxes at a client site and have a small python script to pull a pdf from a remote server based on the user checking in and print this pdf to a label printer.  Currently I do a wget to save the file then lp -d <printername> <file_name>

With the variety of printers I have to hard code the <printername>

I'd like to dynamically determine the printer name and pass that variable into the lp -d line.

on the command line I can do

lpstat -p -d 
to determine the list of printers.  I can also do
lpstat -p -d | grep "system default destination"
i can pull the line needed.

Anyone know in python a quick way to do the same thing?
Thanks in advance!!!,
Russ

---

### Post by juancarlospaco on 2010-10-07
You can parse the cups.conf file i think *(?)*

---

### Post by nvteighen on 2010-10-07
The CUPS library has a function to do that in a UNIX/Unix-like portable fashion: [http://www.cups.org/documentation.php/api-cups.html#cupsGetDefault](http://www.cups.org/documentation.php/api-cups.html#cupsGetDefault)

```

#include <cups/cups.h>

const char *cupsGetDefault (void);

```

Now, I'm pretty sure there are CUPS bindings for Python.

---

