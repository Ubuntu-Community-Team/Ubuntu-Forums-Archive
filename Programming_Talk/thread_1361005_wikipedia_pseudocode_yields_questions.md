---
title: "wikipedia pseudocode yields questions"
date: 2009-12-21
forum: Programming Talk
---

### Post by tdrusk on 2009-12-21
I'm looking at [this]("http://en.wikipedia.org/wiki/CYK_algorithm"). What does the partition (mid code) mean? Maybe an example would help...

---

### Post by lisati on 2009-12-21
Some of the article went over my head. If I understand the pseudo-code correctly, a rough translation of the word "partition" would be "the place where the current scan stops".

---

### Post by tdrusk on 2009-12-21
> **lisati said:**
> Some of the article went over my head. If I understand the pseudo-code correctly, a rough translation of the word "partition" would be "the place where the current scan stops".

ok. I got an answer from another site. 

```
pkhuong 1 point 18 minutes ago[-]
Each span of length i starting at j is partitioned in two sections, one of length k and the other of length i-k. Assuming that there's a way to generate the substring at [j...j+i) as an RA (from RB and RC), you still have to guess where RB will end and RC begin.
```

That kind of helps me but I am still trying to take it all in. :lolflag:

---

