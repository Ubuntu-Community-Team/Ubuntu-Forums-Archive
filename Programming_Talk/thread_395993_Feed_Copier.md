---
title: "Feed Copier"
date: 2007-03-28
forum: Programming Talk
---

### Post by ShareBuntu on 2007-03-28
Hi there,

I'm looking for a CLI tool to input the URL of an xml feed for a blog and have it copy the URLs of links to the entries into a text file. I thought I'd post it here because there probably already exists such a program. Otherwise, what languages would be appropriate (best suited) for this?

---

### Post by lnostdal on 2007-03-29
Almost any language will do. Python, Ruby, Lisp, Perl etc.

I'd probably use Common Lisp, and something like [http://weitz.de/drakma/](http://weitz.de/drakma/) and [http://weitz.de/cl-ppcre/](http://weitz.de/cl-ppcre/) to get hold of the links. Should be quite trivial to do. :)

---

### Post by ShareBuntu on 2007-03-29
> **lnostdal said:**
> Almost any language will do. Python, Ruby, Lisp, Perl etc.

I'd probably use Common Lisp, and something like [http://weitz.de/drakma/](http://weitz.de/drakma/) and [http://weitz.de/cl-ppcre/](http://weitz.de/cl-ppcre/) to get hold of the links. Should be quite trivial to do. :)

Thanks for the reply. I think Python looks very promising. I'll have a look at the Universal Feed Parser. :)

---

### Post by Mr. C. on 2007-03-29
The CPAN archive has many XML parsers available.  Search [http://search.cpan.org/](http://search.cpan.org/) .

MrC

---

