---
title: "speed test?"
date: 2008-09-30
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-30
if i wanted to write a program for pure speed, and i wanted to test it in a few different languages what would the best way to do this be?  to simply have it calculate some large equation like the 100000 iteration of pi and then do the math to see how long it took?  or is there another way?

---

### Post by kknd on 2008-09-30
This time of benchmark usually don't give any important result if your objective is to compare the speed of programing language implementations (your result will only be valid for that test).

For a less flawed comparison, you can try the [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) (you can do your own implementation for a problem and submit).

---

### Post by techmarks on 2008-09-30
> **jimi_hendrix said:**
> if i wanted to write a program for pure speed, and i wanted to test it in a few different languages what would the best way to do this be?  to simply have it calculate some large equation like the 100000 iteration of pi and then do the math to see how long it took?  or is there another way?

I suppose you could get some hints from the computer language benchmarks web site, and the tests they run.

The top 3 languages for speed according to that page on Ubuntu are;

1. ATS

2. C++ GNU g++

3. HASKELL GHC

---

