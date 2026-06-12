---
title: "getting input in perl"
date: 2012-10-30
forum: Programming Talk
---

### Post by Tk007LwZFJW5ej on 2012-10-30
Is there a built-in way to get user input word-by-word (rather than line-by-line) from STDIN in perl, or do I have to code that myself?

---

### Post by trent.josephsen on 2012-10-30
You can fiddle with $/ to change the separator <FILEHANDLE> uses, which is a newline by default (careful changing it as it changes for the entire module -- see [here](http://www.perlmonks.org/?node_id=287647) for more details), or you can use Perl's **read** built-in if you want to do it the hard way.

---

