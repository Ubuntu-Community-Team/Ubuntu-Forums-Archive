---
title: "Merge PDFs or printing goups of PDFs"
date: 2009-06-11
forum: Programming Talk
---

### Post by tc101 on 2009-06-11
I have PDFs stored on a web server.  I need to write code to let a user select a group of PDFs and print them all at once.  

There is lots of 3rd party software to allow merging of PDFs.  If I need 3rd party software, can someone make a recommendation or tell me where I should ask about this?

Maybe I don't need to merge the docs to print them though.  The web site is ASP in VBScript.  The location of the PDFs is stored in a database.  If I get the location of several of the PDFs, is there a way to print them all at once, rather than the user opening each one in acrobat and printing them seperatly?

---

### Post by crush304 on 2009-06-11
ghostscript

[http://pages.cs.wisc.edu/~ghost/index.htm](http://pages.cs.wisc.edu/~ghost/index.htm)

---

### Post by Zugzwang on 2009-06-12
Technically, what you want can be achieved using Acrobat's built-in JavaScript capabilities. But this should be considered to be bad style as it does not work with other viewers.

So, merging the PDFs is probably the way to go. Unlike the last poster, I wouldn't recommend ghostscript but rather either use multivalent ([http://multivalent.sf.net](http://multivalent.sf.net), see the "Tools" section) or rely on pdftk (in the repositories).

---

