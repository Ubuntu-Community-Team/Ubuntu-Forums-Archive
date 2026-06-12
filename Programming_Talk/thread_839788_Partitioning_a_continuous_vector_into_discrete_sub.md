---
title: "Partitioning a continuous vector into discrete sub-units (C++)"
date: 2008-06-24
forum: Programming Talk
---

### Post by kvk on 2008-06-24
In C++, I have a time-series vector of 21 integers (years). I need to define a smaller vector (call it CHRON) such that CHRON[1][1] = Years 1-7; CHRON[1][2] = Years 8-14, and CHRON[1][3] = Years 15-21. That way in later functions I do not have to write endless "if-then" loops for each time-series division, and can simply use the CHRON vector as a reference.

What might be the best syntax for this?

Thanks so much!

---

### Post by slavik on 2008-06-24
> **kvk said:**
> In C++, I have a time-series vector of 21 integers (years). I need to define a smaller vector (call it CHRON) such that CHRON[1][1] = Years 1-7; CHRON[1][2] = Years 8-14, and CHRON[1][3] = Years 15-21. That way in later functions I do not have to write endless "if-then" loops for each time-series division, and can simply use the CHRON vector as a reference.

What might be the best syntax for this?

Thanks so much!
first find the number of partitions you want, then create vectors/lists accordingly

---

