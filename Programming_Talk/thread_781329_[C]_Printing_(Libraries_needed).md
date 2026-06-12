---
title: "[C] Printing (Libraries needed?)"
date: 2008-05-04
forum: Programming Talk
---

### Post by nvteighen on 2008-05-04
Hi!

I've been wondering on how to manipulate devices on C and wanted to start with something simple: printing a text line with my printer.

I imagine I have to grab the correct library and learn how to use it. So, is libcupsys-dev (CUPS Libraries development package) what I need or is it something else?

(Probably I'll need more help afterwards with the program itself, but first what's first)

---

### Post by nebu on 2008-05-04
chk this out.... [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

### Post by nvteighen on 2008-05-04
Incredibly easy! I've printed an uppercase "A" succesfully. I'm going to play around with it a while and get it print a file.

But playing with CUPS seems interesting too, though its API documentation is a bit messy to my taste.

(And thanks for the link, how didn't I come to it before?)

---

### Post by Zugzwang on 2008-05-04
Just wanted to mention that if you're going to stick with this approach, you should definitely provide the user of your program a way to change to command used for printing (for example, for the case for which there's more than one printer for which a parameter to lpr should be provided). That's by the way precisely the way the old versions of the Acrobat Reader used to print. Try postscript if you want more complex output.

---

### Post by nvteighen on 2008-05-04
I'm finally going to try the CUPS front-end approach: an application that connects to the printing server through the library and prints a file; it's the kind of personal programming challenge I like! :)

I'll keep you informed and won't doubt to ask if I need any help (like always).

---

