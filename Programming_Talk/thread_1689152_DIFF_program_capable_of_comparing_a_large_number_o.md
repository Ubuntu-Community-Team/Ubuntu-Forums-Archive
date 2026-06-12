---
title: "DIFF program capable of comparing a large number of texts"
date: 2011-02-16
forum: Programming Talk
---

### Post by mfss on 2011-02-16
[FONT=&quot]Hi[/FONT]
  [FONT=&quot]We are currently writing our master thesis, and are in great need of a specific program. We have no idea whether or not it actually exists, but what we are looking for is a program capable of comparing about 500 texts simultaneously in order to find differences/similarities between the texts – and being able to report about these cross-references. A dreamscenario would be if it’s also capable of giving a procentage of the differences in between the texts.[/FONT]
  [FONT=&quot]We are aware that some of the different diff-programs are able to compare two texts – but we **really** need it to be able to comprehend more than that.[/FONT]
  
[FONT=&quot]It´s preferable if the program can be installed on a windows computer, furthermore if it is possible for the program to load *.pdf files[/FONT]
    [FONT=&quot]
[/FONT]
[FONT=&quot]Hope that you – or someone else – are able to help us.[/FONT]

---

### Post by Arndt on 2011-02-16
> **mfss said:**
> [FONT=&quot]Hi[/FONT]
  [FONT=&quot]We are currently writing our master thesis, and are in great need of a specific program. We have no idea whether or not it actually exists, but what we are looking for is a program capable of comparing about 500 texts simultaneously in order to find differences/similarities between the texts – and being able to report about these cross-references. A dreamscenario would be if it’s also capable of giving a procentage of the differences in between the texts.[/FONT]
  [FONT=&quot]We are aware that some of the different diff-programs are able to compare two texts – but we **really** need it to be able to comprehend more than that.[/FONT]
  
[FONT=&quot]It´s preferable if the program can be installed on a windows computer, furthermore if it is possible for the program to load *.pdf files[/FONT]
    [FONT=&quot]
[/FONT]
[FONT=&quot]Hope that you – or someone else – are able to help us.[/FONT]

Interesting problem. Is it altogether clear what should be reported? What should happen if you have one original text T1, and let it deteriorate through a number of steps to produce T2, T3, up to T10, and then compare those ten files in that order? In another order?

To put it more abstractly, what does it mean to compare several files simultaneously? Is it enough to compare T1 to T2 and then T2 and T3? Is it enough to compare all pairs?

It may be guaranteed that there are large stretches of text that are common to all the files, and which can always be used as synchronization points. Is that the case? If so, how much is known about it?

Maybe the genetics people use such programs.

Converting 500 pdf files to text is a separate problem, which is probably easier to solve.

---

### Post by mfss on 2011-02-16
What we want to do is to compare annual reports to find out whether or not companies "borrow" text from each other, when writing the annual report.
Therefore, we need the program to take 1 text at a time and compare it to the others (prox. 500) to find overlapping between them. 
Quite like when universities compare exam thesis with old exam thesis, to se whether or not there has been "copy/paste"

---

### Post by MadCow108 on 2011-02-16
you might want to look at this:
[http://en.wikipedia.org/wiki/Jaccard_index](http://en.wikipedia.org/wiki/Jaccard_index)

using this term in your searches might help finding software to solve your problem

---

### Post by Some Penguin on 2011-02-16
Vector space model, TDF-IDF for simplicity.  Lucene so you're not reinventing the wheel.

[http://wiki.apache.org/lucene-java/LuceneFAQ#How_do_I_find_similar_documents.3F]("http://wiki.apache.org/lucene-java/LuceneFAQ#How_do_I_find_similar_documents.3F")

---

### Post by slavik on 2011-02-16
writing software you need is PhD worthy all on its own.

---

### Post by lavinog on 2011-02-16
How large would the texts be?

Could you divide the text by punctuation and check for the existence of the clause in other texts?

---

