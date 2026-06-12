---
title: "Algorithms for extracting  File Differences"
date: 2009-01-01
forum: Programming Talk
---

### Post by bhotla.srikanth@gmail.com on 2009-01-01
Hi,

I have been workin on a file comparison implementation which needs to high light the differences between two files.Both these files are almost alike but they have a few differences(in the sense they are revisied versions of the same file)
I have tried out some approaches like finding the Longets Common Subsequence between them
Also tried to implement the Algorithm found at 
[http://delivery.acm.org/10.1145/360000/359467/p264-heckel.pdf?key1=359467&key2=7794270321&coll=GUIDE&dl=GUIDE&CFID=16728805&CFTOKEN=10032967](http://delivery.acm.org/10.1145/360000/359467/p264-heckel.pdf?key1=359467&key2=7794270321&coll=GUIDE&dl=GUIDE&CFID=16728805&CFTOKEN=10032967)

The  Algorithm works fine for most of the cases

But in some case as mentioned in the link it fails

Can any one suggest a better algorithm 

Thanks in advance
Srikanth

---

### Post by CptPicard on 2009-01-01
I am not quite certain why the normal [diff algorithm]("http://en.wikipedia.org/wiki/Diff#Algorithm") isn't good enough for your needs?

---

### Post by bhotla.srikanth@gmail.com on 2009-01-01
I implemented the same(LCS) but it is a time consuming one and instead of optimizing i am opting for any better solution

---

### Post by CptPicard on 2009-01-01
Interesting discussion of various versions. I think I studied that Ukkonen algorithm once back at uni...

[http://www.somethinkodd.com/oddthinking/2006/01/16/comparing-strings-an-analysis-of-diff-algorithms/](http://www.somethinkodd.com/oddthinking/2006/01/16/comparing-strings-an-analysis-of-diff-algorithms/)

---

