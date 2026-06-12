---
title: "JAVA SAX parsing XML file with &quot;&amp;gt;&quot;"
date: 2010-03-20
forum: Programming Talk
---

### Post by totalbeginner on 2010-03-20
If there is a "&gt;" within a line. The content before the "&gt;" got chopped off, only the characters after "&gt;" would be returned. Here is an example. If there is a line like following:

```

<Name> Ro &gt;bin</Name>

```After parsing, only "bin", instead of "Ro &gt;bin" or "Ro>bin", will be returned. Why does this happen?

---

### Post by totalbeginner on 2010-03-21
Use StringBuffer instead of String to store the characters being read in would solve such kind of problem. A nice sample would be :

[http://oreilly.com/catalog/jenut2/chapter/ch19.html](http://oreilly.com/catalog/jenut2/chapter/ch19.html)

---

