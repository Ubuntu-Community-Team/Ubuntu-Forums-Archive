---
title: "Printing HTML Output"
date: 2007-03-18
forum: Programming Talk
---

### Post by phossal on 2007-03-18
I've used Java to create a socket and "visit" a webpage. In return, I get a stream of HTML content. I need to print the content as if I had viewed and printed the page with a browser. Is there an easy way?

---

### Post by lnostdal on 2007-03-18
You can convert it to PDF/PS using some tool/lib. [http://www.htmldoc.org/](http://www.htmldoc.org/) or [http://user.it.uu.se/~jan/html2ps.html](http://user.it.uu.se/~jan/html2ps.html) or something.

---

### Post by Tomosaur on 2007-03-18
A BufferedReader, wrapped around a BufferedInputStream, perhaps?

Or do you mean you want the HTML code to be formatted and displayed - ie, no tags or other HTML, just the content? In that case you'll still need a stream reader, but you should use some of the HTML related classes. You can find more info [here](http://java.sun.com/j2se/1.5.0/docs/api/javax/swing/text/html/HTMLDocument.html). The HTM classes are part of the swing.text package.

---

